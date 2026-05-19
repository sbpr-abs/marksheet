# Instagram Automation Setup Guide

Step-by-step guide to connect your Instagram account to this workspace and automate posting via the Instagram Graph API.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Step 1: Convert to a Business or Creator Account](#step-1-convert-to-a-business-or-creator-account)
- [Step 2: Create and Link a Facebook Page](#step-2-create-and-link-a-facebook-page)
- [Step 3: Create a Meta App](#step-3-create-a-meta-app)
- [Step 4: Add Instagram Test User](#step-4-add-instagram-test-user)
- [Step 5: Generate a Long-Lived Access Token](#step-5-generate-a-long-lived-access-token)
- [Step 6: Configure Environment Variables](#step-6-configure-environment-variables)
- [Step 7: Install Python Dependencies](#step-7-install-python-dependencies)
- [Step 8: Test Your First Post](#step-8-test-your-first-post)
- [Step 9: Automate from the Content Pipeline](#step-9-automate-from-the-content-pipeline)
- [Important Limitations](#important-limitations)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Before starting, confirm you have:

- An **Instagram Business** or **Creator** account. Personal accounts cannot use the Graph API for publishing.
- A **Facebook Page** linked to that Instagram account.
- A **Meta for Developers** account (use the same Facebook login).
- Admin or Content Creator role on the Facebook Page.
- A publicly accessible URL for any image you want to post (the Graph API does not accept local file paths directly).

> **Note:** If your account is currently a personal account, you must convert it. This is free and can be reversed later.

## Step 1: Convert to a Business or Creator Account

1. Open the Instagram app on your phone.
2. Go to your **Profile** > **Menu** (three lines) > **Settings and privacy**.
3. Tap **Account type and tools** > **Switch to professional account**.
4. Choose **Business** or **Creator**.
5. Complete the prompts (category, contact info, etc.).

## Step 2: Create and Link a Facebook Page

The Instagram Graph API requires a linked Facebook Page.

1. Go to [facebook.com/pages/create](https://facebook.com/pages/create).
2. Choose a page category and fill in the name.
3. Click **Create Page**.
4. Go to your Instagram app > **Profile** > **Edit profile** > **Page**.
5. Select the Facebook Page you just created and connect it.

## Step 3: Create a Meta App

1. Visit [developers.facebook.com/apps](https://developers.facebook.com/apps).
2. Click **Create App** > Select **Other** use case > **Business** app type.
3. Fill in the app name (e.g., `ABS Content Poster`) and contact email.
4. Click **Create App**.
5. On the app dashboard, click **Add product** and find **Instagram**.
6. Click **Set up** on the Instagram product tile.
7. Navigate to **Instagram Graph API** > **Basic Display** is not needed; stay in the Graph API section.

## Step 4: Add Instagram Test User

Before generating tokens, add your Instagram account as a test user.

1. In your Meta App dashboard, go to **Roles** > **Test Users**.
2. Under Instagram Testers, click **Add Instagram Testers**.
3. Enter your **Instagram Business/Creator username** and send the invitation.
4. On your phone, open the Instagram app.
5. Go to **Profile** > **Menu** > **Settings and privacy** > **Website permissions** > **Apps and websites** > **Tester invites**.
6. Accept the invitation.

## Step 5: Generate a Long-Lived Access Token

1. In your Meta App dashboard, go to **Instagram Graph API** > **User Token Generator**.
2. Select your connected Instagram account from the dropdown.
3. Click **Generate Token**.
4. Copy the token immediately. It expires in 60 days by default.
5. Convert it to a **long-lived token** (valid for 60 days and refreshable). Run the following from this workspace once you have copied the token:

```bash
# Replace SHORT_TOKEN with the token you copied
SHORT_TOKEN="your_short_token_here"
APP_ID="your_app_id_here"
APP_SECRET="your_app_secret_here"

curl -s -X GET "https://graph.facebook.com/v19.0/oauth/access_token?grant_type=fb_exchange_token&client_id=${APP_ID}&client_secret=${APP_SECRET}&fb_exchange_token=${SHORT_TOKEN}"
```

6. Save the `access_token` from the response. This is your long-lived token.

> **Security tip:** Treat this token like a password. Do not commit it to git. It lives in `.env`, which is already ignored.

## Step 6: Configure Environment Variables

1. Open [`.env`](../../.env) in the project root.
2. Add the following lines at the bottom:

```
# Instagram / Meta Graph API Configuration
META_APP_ID=your_app_id_here
META_APP_SECRET=your_app_secret_here
META_ACCESS_TOKEN=your_long_lived_access_token_here
INSTAGRAM_BUSINESS_ACCOUNT_ID=your_ig_account_id_here
META_GRAPH_API_VERSION=v19.0
```

3. To find your **Instagram Business Account ID**, make this request in your terminal:

```bash
curl -s -X GET "https://graph.facebook.com/v19.0/me/accounts?access_token=YOUR_ACCESS_TOKEN" | python3 -m json.tool
```

Look for the `instagram_business_account` object inside your linked page. The `id` there is your `INSTAGRAM_BUSINESS_ACCOUNT_ID`.

## Step 7: Install Python Dependencies

Run the following from the workspace root:

```bash
uv pip install requests python-dotenv
```

These are already declared in the project's dependency flow. `requests` handles HTTP calls to the Graph API, and `python-dotenv` loads your `.env` file.

## Step 8: Test Your First Post

You need a **publicly accessible image URL**. The Graph API cannot read files directly from `content/images/` inside this container.

**Options for a public URL:**
- Upload the image to an S3 bucket or CDN.
- Use a temporary tunnel (ngrok) to expose a local file.
- Host the image on any public web server.

Once you have a URL, run:

```bash
python3 content/tools/instagram-poster.py \
  --image-url "https://example.com/your-image.png" \
  --caption "Your caption here #hashtag"
```

If the script succeeds, you will see:

```
Creating media container...
Created container: 1234567890
Publishing...
Published! ID: 9876543210
```

Check your Instagram feed to confirm the post appeared.

## Step 9: Automate from the Content Pipeline

After confirming the manual test works, automate it. Here are two common approaches within this project:

### Option A: Post Directly After Generation

Modify any existing generation script (e.g., [`generate-ganesha-fruit-images.py`](../tools/generate-ganesha-fruit-images.py)) to call the poster after uploading the output to a public store.

Example snippet at the end of a generation script:

```python
import subprocess

image_url = upload_to_s3(output_path)  # Your upload helper
subprocess.run([
    "python3", "content/tools/instagram-poster.py",
    "--image-url", image_url,
    "--caption", "New drop from the GDM collection! 🎨"
])
```

### Option B: Batch Post from a Schedule File

Create a CSV or YAML schedule of posts in [`content/marketing/`](../marketing/), then loop over it:

```bash
# Example: post from a simple list
while IFS=',' read -r url caption; do
  python3 content/tools/instagram-poster.py \
    --image-url "$url" \
    --caption "$caption"
done < content/marketing/schedule.csv
```

## Important Limitations

- **Personal accounts:** The Instagram Graph API does not support personal accounts. You must be a Business or Creator account.
- **Public URL required:** Every image or video must exist at a publicly accessible URL before posting. The API cannot read local disk paths.
- **Reels:** Direct Reels publishing requires additional permissions (`instagram_content_publish`) and a video URL. Single-image posting is the simplest to start with.
- **Rate limits:** The API has standard rate limits. Do not exceed roughly 25 posts per hour per account.
- **Token expiry:** Long-lived tokens expire after 60 days. You must refresh them before expiry.

## Troubleshooting

### "The user must be an admin" error
Ensure you are an admin or have the Content Creator role on the linked Facebook Page.

### "Invalid token" error
Generate a new long-lived token. Short-lived tokens expire quickly.

### "URL not accessible" error
The `image_url` must be publicly reachable from Facebook's servers. Test it by opening the URL in an incognito browser window.

### "Media not found" when publishing
Wait a few seconds between container creation and publishing. Very large images may take longer to process.

### Package not found errors
Confirm `python-dotenv` and `requests` are installed:

```bash
uv pip install requests python-dotenv
```

---

## Related Documents

- [`.env.example`](../../.env.example) - Environment variable template
- [`content/tools/instagram-poster.py`](../tools/instagram-poster.py) - Ready-to-use posting script
- [`content/docs/marketing-automation-guide.md`](marketing-automation-guide.md) - Broader marketing automation architecture
- [`content/marketing/`](../marketing/) - Marketing data and schedule files

## External References

- [Instagram Graph API - Content Publishing](https://developers.facebook.com/docs/instagram-api/guides/content-publishing) - Official Meta documentation
- [Meta Access Tokens](https://developers.facebook.com/docs/facebook-login/guides/access-tokens) - Token lifecycle and refresh
- [Instagram Account Types](https://help.instagram.com/502653020765552) - Business vs Creator vs Personal

## See Also

- `scripts/run-mcp-server.sh` - MCP server launcher for this workspace
- `read-me.md` - Project setup and development guide
