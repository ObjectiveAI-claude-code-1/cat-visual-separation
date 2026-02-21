# cat-visual-separation

Scores how visually distinct a cat is from its surroundings in a photograph. Evaluates tonal and color contrast against the background, pattern and texture distinction from nearby surfaces, and scene clarity free from competing elements. Scores high when the cat is immediately readable as the subject; low when camouflaged or visually overshadowed.

## Input

The function accepts a single required field:

| Field | Type | Required | Description |
|---|---|---|---|
| `photograph` | `image` | Yes | A photograph containing at least one cat as the intended subject. The image may come from any source — a professional studio session, a casual phone snapshot, an outdoor candid, a shelter listing, or a social media post. |

## Output

A scalar score in the range **[0, 1]** representing the degree of visual separation between the cat and its surroundings.

| Score Range | Interpretation |
|---|---|
| **0.8 – 1.0** | The cat is immediately and effortlessly visible as the subject. Strong contrast, distinct textures, and a clean scene give the cat its own visual plane. |
| **0.5 – 0.8** | The cat is identifiable but with some effort. Moderate contrast, partial texture overlap, or mild scene clutter softens the cat's presence as the focal point. |
| **0.2 – 0.5** | The cat struggles to stand apart. Low contrast, pattern camouflage, or competing elements undermine the cat's visibility as a distinct subject. |
| **0.0 – 0.2** | The cat is effectively absorbed into the scene. Its form dissolves into the background, its textures are indistinguishable from its surroundings, or it is visually overpowered by other elements in the frame. |

## What It Evaluates

The function measures visual separation across three independent dimensions. Each captures a different way a cat can lose its distinctness in a photograph.

### 1. Tonal and Color Contrast

The most fundamental dimension: the difference in color, brightness, and tone between the cat's fur and the surfaces directly behind and beneath it. This determines whether the cat's silhouette and edges are legible to the viewer at a glance.

**Scores high when:**
- The cat's fur clearly differs in color or brightness from its immediate background
- The cat's outline is instantly traceable — the viewer sees where the cat ends and the background begins without effort
- Example: a white cat on a charcoal bedspread, a black cat on a sunlit wooden floor

**Scores low when:**
- The cat and its background share similar colors and tones
- The cat's form dissolves into the surroundings, forcing the viewer to search for edges
- Example: a gray cat on a gray couch, a black cat in a dark room, a ginger cat on warm-toned hardwood

### 2. Pattern and Texture Distinction

Beyond raw color, this dimension examines whether the visual character of the cat's coat — its markings, texture, and pattern rhythm — is distinct from the textures in its environment. Camouflage is not only a matter of matching colors; it is also a matter of matching visual frequency.

**Scores high when:**
- The cat's fur texture contrasts with the surfaces around it (e.g., a smooth-coated cat on a heavily textured surface)
- The cat's markings have a different scale and rhythm from nearby patterns
- The cat's surface reads as belonging to a different visual category than its environment

**Scores low when:**
- The cat's coat pattern mirrors the textures of surrounding surfaces (e.g., a tabby on a mottled rug)
- The visual rhythm of the cat's fur and its environment rhyme closely enough to blur boundaries
- The cat becomes embedded in the scene's texture rather than sitting atop it as a distinct subject (e.g., a calico on a patchwork quilt, a long-haired cat on a shaggy blanket)

### 3. Scene Clarity and Competing Elements

This dimension looks beyond the background to the entire frame. Even a cat with strong contrast and distinct textures can lose its status as the subject if other elements in the scene rival it for the viewer's attention.

**Scores high when:**
- The cat is the undeniable focal point with no competing elements
- Other objects in the scene are subdued and do not rival the cat's visual weight
- The viewer's eye goes straight to the cat and stays there
- Example: a cat in a calm, uncluttered environment where it naturally commands the gaze

**Scores low when:**
- Bright objects, other animals, people, glowing screens, or bold graphic patterns compete for attention
- The scene is visually chaotic and the cat is demoted from subject to bystander
- The viewer's eye is pulled to other elements before (or instead of) finding the cat
- Example: a cat in a busy room with colorful toys, other pets, and patterned furniture all fighting for the viewer's gaze

## Use-Cases

- **Shelter and rescue adoption listings** — Ensure that photographs of adoptable cats clearly show the animal as the subject, increasing the chance of an emotional connection with potential adopters.
- **Social media curation** — Select or rank cat photos by how strongly the cat reads as the focal point, filtering out images where the cat is lost in its surroundings.
- **Stock photography filtering** — Automatically flag cat photographs where the subject lacks visual separation, streamlining catalog quality control.
- **Photography feedback and diagnostics** — Help photographers understand why certain cat images feel flat, confusing, or visually muddled, and identify which dimension (contrast, texture, or scene clutter) needs improvement.
- **Automated image pipelines** — Integrate into pet photography workflows to flag images that need re-shooting or post-processing before publication.

## Examples

| Scenario | Expected Score | Reasoning |
|---|---|---|
| White cat on a dark sofa in a clean, simple room | High | Strong tonal contrast, distinct textures, no competing elements |
| Orange tabby on a plain blue blanket, no clutter | High | Good color contrast, texture distinction, clear scene |
| Gray cat on a gray couch with a few objects nearby | Low | Minimal tonal contrast, potential texture similarity, mild clutter |
| Black cat in a dark room with a glowing TV | Very Low | No tonal contrast, textures lost in shadow, TV competes for attention |
| Tabby cat on a mottled rug in a busy living room | Very Low | Moderate color match, strong texture camouflage, high scene clutter |
