# Prompting notes — Seedream 4.5 (stills) and Seedance 2.x (video) on Higgsfield

Two kinds of entry below: **[tested]** is from our own runs on 12 Oct 2026 (see `image-model-bakeoff.md`); **[guide]** is from online guides, not yet tested by us.

## @ references (image pointers)
- **[guide] Seedance 2.0:** each upload gets a label (@Image1, @Video1, @Audio1). Give every reference a stated *role* in the prompt, not just an attachment: "@Image1 for the shoes only", "@Image2 as the first frame", "imitate the motion of @Video1". The same guides suggest first/last-frame pairs: "@Image1 as the first frame, @Image2 as the last frame". [Magic Hour](https://magichour.ai/blog/seedance-20-reference-guide), [Picsart](https://picsart.com/blog/seedance-2-0-prompts/)
- **[guide] Higgsfield:** in Cinema Studio, Elements (@Characters / @Locations / @Props) and @ references are media chips. They count toward a ~512-character prompt cap (2.5: ~80–100 hidden characters per chip). When an image is the start frame, describe **only motion and camera**, not what's already visible. [community skill notes](https://sharedcontext.ai/skills/external/OSideMedia/higgsfield)
- **[guide] Seedream 4.5:** no documented @-syntax found. References are passed as an ordered list, so position probably matters. The guides recommend describing the change you want across all the references. [Runware](https://runware.ai/docs/models/bytedance-seedream-4-5/guides/prompting), [fal](https://fal.ai/learn/devs/seedream-v4-5-prompt-guide)
- **[tested] Seedream 4.5 on Higgsfield:** "exactly as in the reference images" plus a text description of the key details worked (shoes matched in 8/8). The web UI has an **@** button next to **+**. Next test: tag each reference by role (shoes vs bike).

## Subject and wardrobe
- [tested] Shoes: attach photos; text alone gets ignored by most models. Name the hard detail plainly ("gold heel widens smoothly where it joins the shoe"). Avoid metaphors: "trumpet cup" drew a goblet.
- [tested] Tights: sheer and fishnet both render well. Opaque comes out sheer anyway.
- [tested] Veil: every model mangles it; dropped.

## Composition
- [tested] "Single subject, no other people" removes extra figures.
- [tested] "Shoes large in frame" creates a giant foreground shoe **plus a second woman**. Use a low, close camera instead.

## Uphill on slippery ground (the hard part)
- [tested] Plain "climbing a slippery slope" drifts to standing, crossing, or descending (training data is full of sliding *down*).
- [tested] What fixed it (bike: 10/10 uphill): a **goal at the top right** (stone hut), "slope rises from lower left to top right", **"front wheel / front foot higher than the rear"**, "bike and her face point at the hut", spray thrown **"backwards and downhill toward the lower left"**.
- [tested] Avoid slide verbs for her ("slid back"); use "loses grip for an instant".

## Marks and terrain
- [tested] Footprint *trails* work; stiletto-*shaped* prints don't (they come out as oval soles or potholes). Describe the shape literally and give sizes.
- [tested] Scratches, grooves and slide marks need a **length and position** ("about 20 cm, just behind the heel"), or they span the frame.
- [tested] "Wet granite slab" reads as paving tiles. Say "natural seamless rock, no joints".

## Bike variant
- [tested] "Hips planted in the saddle, chest pushed far forward right over the handlebars, rider and bike one unit" plus "both feet off the pegs, planted, pushing" works best on snow.
- Without a photo reference the bike becomes a generic knobbly pit bike.

## Prompt order
- [guide] Subject → action → camera → style; focused beats exhaustive.
