# Unlimited image-model bake-off — 12 Oct 2026

Same prompt on every model, 2 tries each, Higgsfield web UI, Unlimited on (0 credits spent), 16:9 (GPT Image: 3:2, no 16:9), lowest resolution.

Prompt: steep mountain track of wet scree and mud; sheer black tulle veil over mouth and chin; short black long-sleeve dress; 100-denier opaque tights; black suede platform stiletto pumps, 1-inch platform, slender 6-inch polished gold heels; right heel mid-skid; upper body still; "exactly two legs, two feet, two shoes".

| Rank | Model | Shoe accuracy | Anatomy / morph | Veil | Notes |
|---|---|---|---|---|---|
| 1 | **Seedream 4.5** | Best: suede platform, slender gold heel, both tries | Clean | Sheer veil + face cloth (overdone) | Mud kick-up at the heel = closest to a skid. Strongest first-frame candidate. |
| 2 | **Seedream 5.0 lite** | Good: suede platform, gold heel | Clean | Mask + veil hood | Mud splash at the heel. Try B: tights read 40 den, not opaque. |
| 3 | **Seedream 4.0** | Platform drawn as a gold block wrapped round the sole (wrong) in try A; correct in try B | Try B: second woman appears + giant foreground legs | Good sheer veil | Unreliable composition. |
| 4 | **Z-Image** | Good shoe, gold heel | **Try A: three legs/feet** | Full head veil | Try B crops her face out. |
| 5 | **Kling O1** | Gold *toe cap* added; shoe right otherwise | Giant foreground legs + tiny woman behind, both tries | Head veil | Ignores the framing; stylised fashion-ad look. |
| 6 | **Higgsfield Soul** | Try A: shoe wrong; try B: giant square platform | Try B: a stray object near her hip | Try A: blindfold, not a veil | Fashion look, ignores the brief. |
| 7 | **GPT Image** | Plain pumps, **no platform, no gold heel** (bronze/copper) | Clean | Medical-style mask, no veil | Ignores the shoe spec entirely. |
| — | FLUX.2 Pro | (pending in Unlimited queue) | | | Earlier run: good shoes, veil drawn as a solid mask. |

## Takeaways
- **Use Seedream 4.5 for first frames.** It's the same company (ByteDance) as Seedance, it holds the shoe spec, and it produces the mud kick at the heel without being asked twice.
- Every model fights the veil: "veil" gets read as a mask, a head veil or a blindfold. Next test: describe it as fabric, not as "veil" ("a square of sheer black chiffon tied behind her head, hanging from the bridge of her nose to her chin").
- "Exactly two legs" doesn't stop Z-Image from adding a third.
- Kling and Seedream 4.0 add giant foreground legs when the camera is told to be low; "low camera at knee height" may need "single subject, no other people, no foreground figures".

## Round 2 — Seedream 4.5 + shoe references (8 tries, Unlimited, 16:9 2K)
Refs attached: side profile + rear triptych. Veil dropped. Added "single subject, no other people".

- **Shoe: big step up in all 8.** Black suede, tall platform, high almond toe, slender gold heel. Matches the real pair far better than text-only.
- **Single subject held in 8/8.** No extra people or foreground legs. 8/8 had correct anatomy.
- **Skid: mud spray at the moving heel in 5/8** (#2, 4, 5, 7, 8). #7 is the best first frame: clear side-on skid with good shoes.
- **Faults:**
  - #3 drew "trumpet-shaped gold cup" literally, as a goblet detached from the shoe. Reword: "the gold heel widens smoothly at the top where it joins the shoe".
  - Tights came out sheer (~30 den) in all 8 despite "100-denier opaque". Try "fully opaque matte black tights, no skin visible through them".
  - #8 platform exaggerated (~3 in).

## Round 3 — harder terrain (Seedream 4.5 + shoe refs, 15 submitted / 14 returned, Unlimited)
Sheer or fishnet tights (user: both perfect). Picks: `round3_picks.jpg`.

| Terrain | Result |
|---|---|
| A wet granite slab | Steep and glossy with good reflections, but it reads as paved tiles (grid lines), not natural rock. Try 1 gave the platforms a woven-gold texture (wrong). Fix: "natural seamless granite, no joints or tiles". |
| B polished cobbles (fishnet) | **Best scene.** Steep alley, glassy wet stones, fishnet and shoes right. But no visible slip: the "heel in the gap" skid didn't show. |
| C glacier snow | **Footprint trail works** (dotted line up the slope). But the prints are generic flat shoe prints, not stiletto holes, and the shoes are small in frame. No scrape groove. |
| D blue ice (fishnet) | Striking. The scratch came out as one giant laser line across the whole slope; ice chips appear in try 2. Fix: "a short scratch about 20 cm long, just behind the heel". |
| E slush/mud | **Trail + slide splash both appear** (try 2 best). Prints are again oval sneaker-like shapes, not stiletto holes. Try 1 is flat ground; try 3 is a tilted camera, not a steep track. |

Lessons:
- Diffusion models do footprint *trails* but not stiletto-*shaped* prints. Try describing the print shape literally: "each print is a small deep round hole the size of a coin, with a separate wide oval dent 15 cm in front of it".
- Damage marks (scratches, grooves, slide marks) need a stated length and position, or they become huge.
- Upper-body composure held in all 14.

## Round 4 — cobbles / blue ice / slush, 5 each (15/15 returned, Unlimited)
- **"Shoes large in frame" backfires:** in 3/5 cobble shots it produced a giant foreground shoe plus a second, small, full-length woman behind (two figures, 3–4 legs). Drop it; get shoe size from a lower, closer camera without saying "large".
- Cobbles #4 and #5 are the keepers: steep stepped alley, heel tip on a wet cobble with a short bright streak; in #5 the shoe is visibly twisted on the stone (the ankle roll came through).
- Blue ice: scratch now shorter and ice chips appear. But **she stands or walks across the slope in 5/5, never clearly up it**.
- Slush: **footprint trail now reads as round holes** (big round dents, not coin + oval pairs) and the heel splash appears in 5/5. Direction is ambiguous: the trail often runs *ahead* of her up the track, which reads as descending.
- Confirms the user's point: "uphill on a slippery slope" gets pulled toward sliding/descending imagery. Next: pin direction in-frame (slope rises left→right, she faces upper right, front foot higher, goal above her, trail *below and behind* her), and avoid slide verbs.

## Bike round 1 — text-only bike, shoe refs, slush (5/5 returned, Unlimited)
Sheet: `bike_round1.jpg` (tile 6 repeats tile 5).
- **The hut works as an uphill anchor**: the slope, track and hut read clearly in 5/5.
- **Direction: only 2/5 point up toward the hut** (#1, #2). In #3–5 the bike faces left, i.e. downhill, even with "points up-slope toward the hut".
- **Legs: feet sit on the footpegs, not down pushing**, in most tries. Needs "both feet off the pegs, planted in the slush on either side of the bike".
- Rear-wheel spray appears in 5/5, but the bike isn't sunk to the hubs.
- The bike is a generic knobbly-tyred pit bike, not the user's supermoto (road tyres, black seven-spoke wheels). Needs the photo reference.
- She sits in the saddle, leans forward and stays calm. The composure holds.

## Bike round 2 — fixes applied (10/10 returned, Unlimited)
Rows 1–2.5 slush (#1–5), rest glacier (#6–10). Sheet: `bike_round2.jpg`.
- **Direction fixed: 10/10 ride up toward the hut.** "Front wheel higher than rear; bike and face point at the hut" plus the hut works.
- **Chest over the bars** clearly in glacier #6–10; in slush she still sits more upright.
- **Legs down pushing** in 6/10 (glacier ones best: legs back, heels digging into the snow).
- Spray plume in 10/10; a trench in the snow in some.
- **Glacier set is the strongest** of the whole session.
- Still a knobbly pit bike, not the user's supermoto → bike photo reference needed.

## Bike round 3 — glacier, 4 refs (shoe ×2 + user's bike ×2), roles stated in words (10/10, Unlimited)
Sheet: `bike_round3.jpg`.
- **Bike identity much closer:** black multi-spoke wheels, white plastics, black number board, Renthal-style bar pad in most. Tyres still partly knobbly. No artefacts from the scribbled plate.
- **Direction regressed: ~5/10 climb toward the hut** (#1, 2, 7, 8, 9); the rest face left or toward the camera. Round 2 got 10/10 with a shorter prompt and no bike refs. The bike photos are side-on, facing right, on flat ground, and the longer prompt seems to dilute the direction cue.
- Chest over the bars: strongest in #3, 6, 9. Feet down pushing: #1, 2, 4, 7.
- Next: put the direction sentence first, cut the description of the bike's looks (the refs carry it), and drop the rear bike photo.
