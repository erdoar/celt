# Handover: Gait Bench and AI video work (12 Oct 2026)

Paste this into a new chat. It summarises a long thread so the new chat starts with the full picture.

## Who and how
- Owner: erdoar (Nulytica). Prefers extreme directness, no fluff, an early statement of confidence, ready-to-copy prompts and small incremental changes.
- The OSINT "master prompts" from the owner's Grok chats are background only. Don't apply them.

## Gait Bench: state
- A Claude plugin that rebuilds a video of a person as a simple 3D scene. Claude looks at the frames, writes the place and the person's body as poses over time, checks its render against the clip on a comparison sheet, and corrects it. Scripts only draw what Claude wrote. Outputs, from a camera the user sets in the studio: video, clay/contact reference videos, an animated `.glb`, the scene file.
- **Version 2.0.1, ON HOLD since 9 Oct 2026** until a new major version of the AI model. The reason: on three generated clips, Claude got the key postures right, but between poses the figure moves like a keyframed mannequin, with no weight, reaction or struggle for balance. The three clips:
  - a snow-bank scramble and fall;
  - a mud-track slip and backward fall;
  - a kitchen tray slip into a split stance.
- **Repos:**
  - `erdoar/gait-bench` (private, development; `CLAUDE.md` holds the rules, `dev/HANDOFF.md` the state and next steps);
  - `erdoar/gait-bench-plugin` (public release; install with `/plugin marketplace add erdoar/gait-bench-plugin`).
- **Live:**
  - gait.nulytica.com and check.nulytica.com serve 2.0.1, Netlify deploy `6ac932ac…` on 9 Oct. Netlify credits were low after it (reset 12 Oct). Never auto-deploy; each deploy costs 15 credits.
- **Studios (Claude artifacts):**
  - the main studio: https://claude.ai/artifact/SXV5vpR9VyPay5Yhu88UJd (2.0.1 page);
  - the preview: https://claude.ai/artifact/C9ZRAQPXy3QktEU7cLGjkg (holds the kitchen capture).
- **2.0.1 highlights:**
  - "Send to Claude" in the studio posts a comment sent to Claude, which wakes the session watching the studio, so no typing is needed. This was proven end to end on the kitchen clip.
  - The studio opens on its last capture.
  - `look` accepts browser WebM clips that store no duration.
- **Known open item:** box props draw as rounded capsules (cabinets look like blobs).
- **When it resumes:** recapture the three clips with the new model and judge the movement by eye before changing any code.

## After the hold: what was discussed
- **Odyssey-3** (a world model, free research preview): not integrable. Text in, real-time video out; no API, no 3D or pose output, and no way to give it the user's video or poses. It breaks the plugin's rules (no external models, GPU or network). Lesson: convincing movement comes from models trained on video, which supports the hold. Watch for world models that accept pose or video input.
- **Seedance** (ByteDance, via Higgsfield) already produces convincing movement and has been the owner's main tool for months. Getting a *specific* walk out of it (e.g. a dignified climb up a slick slope) takes heavy prompts and tweaking, but gets there.
  - Seedance 2.0, 2.0 Mini and 2.5 accept video references alongside the prompt (2.5 in "omni_reference" mode); confirmed in Higgsfield's model list.
  - I proposed feeding Gait Bench clay references to Seedance as motion blocking. **The owner rejected it:** Gait Bench lacks emotional self-belief, situation control ("Celtic glamour") and micro stick-slip judder, so a mannequin reference would pull Seedance toward stiffness. Agreed. Don't propose it again unless the model improves.
- The useful direction now is **prompt craft for Seedance**. Claude helps with words and with diagnosing failed generations, without Gait Bench.

## Earlier work: Celtic Glamour Traction Study (built in Grok)
- The brief ("master011"):
  - photorealistic video of a fictional woman aged 25–35 in extreme heels on a slippery kitchen floor (butter by default; honey or molasses as variants);
  - visible traction struggle in the heels and legs only, against untouchable, regal, supernaturally composed poise;
  - fixed lens, static or very slow camera, sharp focus on the shoes and legs;
  - wardrobe: black veil over the lower face, short black cocktail dress, garter, opaque black stockings, suede platform stilettos with 6-inch gold heels.
- **My critique of the Grok prompts:**
  - **Cut the invisible physics.** Shore hardness, micrometre roughness, Navier-Stokes, research-model names: Seedance can't see them, and they dilute the prompt. Grok's "physics-enhanced" rounds only made the prompts longer.
  - **Translate each mechanism into what the camera sees:**
    - stick-slip: "each heel catches for an instant, then skids a few centimetres sideways; small catch-and-release judders";
    - butter: "smears into glossy streaks";
    - honey: "strings stretch from the sole and snap";
    - molasses: "the sole peels free with a slow dark strand".
  - **Show composure through behaviour:** she never looks down, her head stays level, her eyes are calm above the veil, her shoulders still, her hands loose; she never hurries, flails or falls. Abstract "witch-like power" either gets ignored or turns into literal magic effects.
  - **One framing per shot:** full length from a low camera, or a legs-and-feet close-up. Not both.
  - **Ordered beats in one shot, then what must not happen.** A fixed block for camera and character, with one line swapped for each substance.
- **Rewritten butter prompt (to test against the owner's current one):**

```
Photorealistic. Full-length shot, low static camera, fixed lens, very slow push in. Sharp focus on her shoes and legs, no motion blur.
A woman, about 30, black veil covering her lower face, short black cocktail dress, garter, opaque black stockings, suede platform stilettos with slender 6-inch gold heels.
She walks slowly and evenly across a tiled kitchen floor coated thickly in soft butter.
Each heel catches for an instant, then skids a few centimetres sideways; small catch-and-release judders; her ankles make quick tiny corrections; the butter smears into glossy streaks behind each step.
Halfway, her right heel slides out wider; she absorbs it in her knee and keeps walking.
Above the waist she is completely still: head level, eyes calm above the veil, shoulders relaxed, hands loose. She never looks down, never hurries, never flails, never falls.
```

## Suggested next steps
1. Test the rewritten butter prompt against the owner's best existing prompt in Seedance, and compare composure and stick-slip.
2. Build a short glossary: phrases that reliably produce composure, control and stick-slip in Seedance, taken from prompts that worked.
3. When a generation misses, look at its frames, say which quality broke and which words to change.
4. Gait Bench stays on hold. Its next step is in `dev/HANDOFF.md`.
