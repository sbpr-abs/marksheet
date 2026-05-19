# Modak — Character Generation Prompts for Veo 3 / Flow
## Reference Image Prompts (Imagen) + Video Character Consistency Bible

---

## Why This Comes First

Veo 3 and Flow generate video by reading image *references*. If the person in Clip 2 has straight hair and Clip 8 has curly hair, your ad looks like a casting disaster. You must generate **character reference stills** first, lock them, and feed them back into every video prompt as image inputs.

**Workflow:**
1. Generate character reference images with Imagen (prompts below).
2. Select one approved reference per character.
3. Feed that same approved image into every Veo 3 / Flow video generation as `input_image` or `image_reference`.
4. Never generate a video of a character without their reference image attached.

---

## The Core Cast

Every 8-second clip can be shot with **one family** plus one grandmother figure. We cast four characters who appear across all 15 clips.

| Role | Name (internal) | Age | Look | Energy |
|---|---|---|---|---|
| **Mother** | Meera | 29 | Warm, tired, real. Not a model. | Quiet strength, slightly messy, unconditionally loving |
| **Father** | Arjun | 32 | Gentle, scruffy, soft eyes. | Goofy, present, not performative |
| **Daughter** | Ananya | 6 | Bright, gap-toothed, two braids. | Confident, expressive, wise beyond her years |
| **Son** | Ishaan | 4 | Round face, messy hair, always moving. | Chaotic good, asks 47 questions per hour |
| **Grandmother** | Sarla | 66 | Silver hair, deep wrinkles, rimless glasses. | Warmth incarnate. Half-smile. Storyteller eyes. |

---

## Reference Image Prompts (Imagen 3 / Imagen 4)

Generate **three views per character**: Front neutral, 3/4 smiling, profile/side. Use these prompts directly in Imagen. All prompts specify **no text, no logos, flat neutral background** to isolate the figure.

---

### MEERA — The Mother

**Front Neutral View**
```
Photo-realistic portrait of a 29-year-old Indian woman, warm olive skin,
dark brown eyes with slight natural dark circles, wavy dark brown hair
pulled loosely into a low bun with a few strands escaping at temples.
Wearing a soft mustard-yellow cotton kurti with 3/4 sleeves.
No jewelry except small simple silver studs. No makeup except faint lip tint.
Expression: neutral, tired but kind. Looking directly at camera.
Standing against a flat warm gray studio backdrop.
Soft natural window light from the left. Shallow depth of field.
No text. No logos. No patterns in background. Clean, minimal, casting-photo style.
```

**3/4 Warm Smile View**
```
Photo-realistic 3/4 view of a 29-year-old Indian woman, same woman as before,
warm olive skin, dark wavy hair in loose low bun with escaping strands,
wearing soft mustard-yellow cotton kurti. Slight warm smile, eyes crinkling,
looking slightly off-camera as if reacting to a child out of frame.
Soft golden-hour natural light on her cheek. Flat warm beige backdrop.
No jewelry except small silver studs. No heavy makeup.
Casual, real-mother warmth. Documentary casting photo.
No text. No logos. No busy background.
```

**Profile / Side View**
```
Photo-realistic profile view of a 29-year-old Indian woman,
warm olive skin, dark wavy hair in loose low bun, mustard-yellow cotton kurti.
Slight downward gaze, gentle expression. Soft natural light.
Flat warm gray backdrop. Clean silhouette. No text. No logos.
```

---

### ARJUN — The Father

**Front Neutral View**
```
Photo-realistic portrait of a 32-year-old Indian man, medium wheatish-brown skin,
short black hair slightly messy on top, warm dark brown eyes, trimmed beard
and mustache with a few grays at chin. Wearing a faded olive-green henley
shirt with rolled sleeves, soft corduroy texture. Slight tiredness around eyes.
Expression: neutral, friendly, grounded. Looking directly at camera.
Flat warm gray studio backdrop. Soft natural window light from left.
No watches, no logos on shirt, no sunglasses. Clean, authentic, casting-photo style.
No text. No logos. Minimal background.
```

**3/4 Laughing / Reacting View**
```
Photo-realistic 3/4 view of a 32-year-old Indian man, same as before,
medium wheatish-brown skin, messy short black hair, trimmed beard with chin grays,
faded olive henley shirt. Slight open-mouthed laugh, head tilted back slightly,
reacting to something off-camera. Caught-in-the-moment genuine expression.
Warm living room light implied. Flat warm beige backdrop.
Casual, real-father energy. Not posed. Documentary casting photo.
No text. No logos. No branded clothing.
```

**Profile / Side View**
```
Photo-realistic profile view of a 32-year-old Indian man,
wheatish-brown skin, short messy black hair, trimmed beard,
olive henley shirt. Gentle downward smile. Flat warm gray backdrop.
Soft window light. Clean line. No text. No logos.
```

---

### ANANYA — The Daughter (Age 6)

**Front Neutral View**
```
Photo-realistic portrait of a 6-year-old Indian girl, warm golden-brown skin,
large bright dark brown eyes with natural curiosity, two neat long braids
with small hair-ties at ends, no fancy bows. Front baby tooth gap visible.
Wearing a soft dusty-rose colored cotton frock with small white piping at collar.
No jewelry. No makeup. Expression: neutral, slightly curious, looking at camera.
Flat warm gray studio backdrop. Large soft natural window light. Shallow depth.
Clean casting-photo style. No text. No logos. No cartoon characters on clothing.
```

**3/4 Explaining / Confident View**
```
Photo-realistic 3/4 view of a 6-year-old Indian girl, same as before,
golden-brown skin, two long braids, dusty-rose cotton frock.
Confident expression, gesturing slightly with one small hand as if explaining
something important. Chin up. Eyes bright and serious.
Warm living room light on her face. Flat warm beige backdrop.
Documentary realism. Natural child movement, not posed.
No text. No logos. No Disney characters on clothing.
```

**Profile / Side View**
```
Photo-realistic profile view of a 6-year-old Indian girl,
golden-brown skin, two long braids with simple hair-ties, dusty-rose frock.
Looking slightly upward. Soft curiosity. Flat warm gray backdrop.
Clean silhouette. No text. No logos.
```

---

### ISHAAN — The Son (Age 4)

**Front Neutral View**
```
Photo-realistic portrait of a 4-year-old Indian boy, round golden-brown face,
chubby cheeks, dark brown eyes full of mischief, messy black hair
that refuses to lie flat, faint cowlick at crown. Wearing a soft heather-gray
cotton t-shirt with no visible logos. Slightly sticky hands implied.
Expression: neutral, half-smile, looking at camera with mischief.
Flat warm gray studio backdrop. Large soft window light. Shallow depth.
Real child, not porcelain. No text. No logos. No cartoon prints on shirt.
```

**3/4 Mid-Motion / Chaotic View**
```
Photo-realistic 3/4 view of a 4-year-old Indian boy, same as before,
golden-brown skin, messy black hair with cowlick, heather-gray t-shirt.
Caught mid-gesture, one hand raised, mouth open as if mid-question.
Eyes wide and energetic. Unposed, spontaneous, real child energy.
Warm living room light. Flat warm beige backdrop.
Documentary capture, not studio posing.
No text. No logos. Clean clothing.
```

**Profile / Side View**
```
Photo-realistic profile view of a 4-year-old Indian boy,
golden-brown skin, round cheek, messy black hair,
heather-gray t-shirt. Slight pout of concentration.
Flat warm gray backdrop. Soft light. No text. No logos.
```

---

### SARLA — The Grandmother

**Front Neutral View**
```
Photo-realistic portrait of a 66-year-old Indian woman, deep warm brown skin
with weathered texture and natural age spots, silver-white hair in a soft
loose bun at nape with a few strands loose at temples. Wearing rimless eyeglasses
with thin gold wire. Soft pink-cream cotton saree with faded delicate floral print
in pale orange and green. Small simple gold studs. No heavy jewelry.
Expression: gentle half-smile, knowing eyes, looking directly at camera.
Flat warm gray backdrop. Soft warm golden-hour light. Shallow depth.
Dignified, not sad. Living presence. No text. No logos.
```

**3/4 Storytelling / Warm View**
```
Photo-realistic 3/4 view of a 66-year-old Indian woman, same as before,
deep weathered brown skin, silver-white hair in soft bun, rimless glasses,
pink-cream floral cotton saree. Warm storytelling expression, head slightly tilted,
eyes crinkled as if about to share something wise. Gentle hand gesture implied.
Golden warm light. Flat beige backdrop. Documentary casting style.
No text. No logos. No modern branding.
```

**Profile / Side View**
```
Photo-realistic profile view of a 66-year-old Indian woman,
deep warm brown skin, silver-white hair in soft bun with loose strands,
rimless glasses, pink-cream saree. Looking slightly downward with gentle smile.
Flat warm gray backdrop. Golden light rim. No text. No logos.
```

---

## Using References in Veo 3 / Flow

### Step 1: Generate Stills
Run each Imagen prompt above. Generate 4 variations per prompt. Pick the best one per view per character. You will have:
- 15 approved reference images total (3 views × 5 characters)

### Step 2: Approve the Set
Lay all 15 images side by side. Verify:
- [ ] Skin tones are consistent across family members (plausible genetics)
- [ ] Hair color family is the same (dark brown to black, grandmother silver)
- [ ] Clothing colors don't clash with the warm-gold ad grade (good: mustard, olive, rose, cream, pink; bad: neon, harsh red, electric blue)
- [ ] Faces look like real people, not mannequins
- [ ] Eyes have consistent warmth and direction

### Step 3: Attach to Video Prompts
For every Veo 3 or Flow video generation, include the relevant character reference(s) as input images.

**Example (Veo 3 Vertex AI / API structure):**
```
image_reference: meera_front_neutral.png
image_reference: ananya_34_confident.png
prompt: "Meera and Ananya sit shoulder-to-shoulder on a wooden bench..."
```

**If your tool only allows one image reference:**
Composite both characters into one side-by-side reference image first:
```
Two people sitting close together: Meera the mother in mustard kurti
and Ananya the daughter in dusty-rose frock. Warm olive skin, dark hair
in low bun for mother, two long braids for daughter. Both looking at a tablet
between them. Documentary casting-photo style, flat gray background,
large soft natural light from left. No text. No logos.
```
Generate this composite in Imagen. Use *that* as your single image reference for Veo 3.

---

## Character Consistency Rules Across All 15 Clips

| Rule | Specification | Why It Matters |
|---|---|---|
| **Hair** | Meera always loose low bun with escape strands. Arjun always slightly messy. Ananya always two braids, simple ties. Ishaan always cowlick. Sarla always silver bun. | Veo 3 mixes hairstyles if you don't lock them |
| **Clothing base** | Meera: mustard or cream. Arjun: olive or faded blue henley. Ananya: rose or soft yellow. Ishaan: gray or soft green. Sarla: cream/pink saree. | Color grade survives across clips |
| **No jewelry changes** | Meera: tiny silver studs only. Sarla: same gold studs. Others: nothing. | Jewelry jumps break continuity |
| **No makeup changes** | Everyone stays natural-faced. No lipstick episode-to-episode. | Glamour shifts betray realism |
| **Age lock** | Ananya stays 6. Ishaan stays 4. No "now she's 8" drift. | Veo hallucinates older faces without refs |
| **Skin tone lock** | Warm olive-golden family. No one goes paler or darker between clips. | Avoids recasting feel |
| **Setting continuity** | Living room rug is always woven, beige. Couch is always moss-green or warm brown. Kitchen counter is always light wood. | Same home, different moments |

---

## Negative Prompts for Imagen (What to Ban)

Add these to every generation to avoid unusable characters:

```
No heavy makeup, no fashion model posing, no runway stance,
no diamond jewelry, no branded clothing, no logos visible,
no cartoon characters on fabrics, no perfect symmetrical smiles,
no porcelain skin, no excessive photoshop smoothing, no AI sheen,
no anime eyes, no cartoon proportions, no text in frame,
no cluttered backgrounds, no harsh studio flash, no cold blue light.
```

---

## Quick Lookup: Which Characters in Which Clip

| Clip | Characters Needed | Reference Images to Attach |
|---|---|---|
| 01 The Hand-Off | Meera + Ishaan | Meera hands extended, Ishaan receiving |
| 02 The Stillness | Ishaan (or Ananya) | Child 3/4 or profile |
| 03 The Exhale | Meera + Ishaan (BG) | Meera reacting, Ishaan in soft focus |
| 04 Learning Together | Arjun + Ananya | Arjun 3/4, Ananya 3/4 confident |
| 05 The Jaw Drop | Meera + Ananya (BG) | Meera 3/4 shocked, Ananya explaining |
| 06 The Memory Lap | Sarla (hands only) + empty space | Sarla front or profile |
| 07 The Story Corner | Ishaan (or Ananya) solo | Child profile or neutral |
| 08 The Morning After | Meera + two children | Composite family reference |
| 09 The Art Is Alive | None — pure animation | No character refs needed |
| 10 The Comparison Split | Ishaan (both sides) | Ishaan in various states |
| 11 The Handed Down | Sarla + Ishaan (older) | Grandmother + child composite |
| 12 The Download Moment | Ishaan (or Ananya) | Child 3/4 absorbed |
| 13 The Quiet Victory | Meera + Ananya + Ishaan | Full family composite |
| 14 The Family Circle | All 5 characters | Pan-Indian family composite |
| 15 The First Word | Ananya solo | Ananya 3/4 confident |

---

## Approved Composite Prompts for Multi-Character Scenes

When you need two or more people in the same frame and can only feed one image, generate this composite first:

**Family of Four (Meera, Arjun, Ananya, Ishaan)**
```
Documentary-style casting photo of an Indian family of four standing
close together against a flat warm beige backdrop.
Mother Meera (29, mustard kurti, loose bun, silver studs),
Father Arjun (32, olive henley, messy hair, trimmed beard),
Daughter Ananya (6, dusty-rose frock, two long braids, gap-tooth smile),
Son Ishaan (4, heather-gray t-shirt, messy hair, round cheeks).
All have warm olive to golden-brown skin tones.
Soft natural window light from the left. Slight variation in poses —
Arjun has arm around Meera, Ananya holds Ishaan's hand.
Real family energy, not forced. No text. No logos. No heavy jewelry.
Shallow depth of field. Cinematic documentary casting style.
```

**Three Generations (Sarla, Meera, Ananya)**
```
Documentary-style casting photo of three generations of Indian women
against a flat warm gray backdrop. Grandmother Sarla (66, silver bun,
rimless glasses, cream-pink saree with faded floral print, warm brown skin,
gold studs). Mother Meera (29, mustard kurti, loose dark bun, olive skin,
silver studs). Granddaughter Ananya (6, dusty-rose frock, two braids,
golden-brown skin, gap smile). Standing in a gentle diagonal line.
Sarla's hand lightly on Meera's shoulder, Meera's hand on Ananya's head.
Warm golden-hour light. Soft shadows. No text. No logos.
Dignified, loving, living family. Cinematic documentary casting style.
```

---

*Document prepared for the Modak Creative Production Team — 13 May 2026*
