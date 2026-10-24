---
name: test-hooks
description: 'Test several hooks for one product as Probably video variants, such as "test 5 hooks for this product". Use when the person wants hook variants, an A/B test of openings, or the same video with different first lines.'
---

Makes one video for the product, then prepares variants of it that keep its research and remake everything from the copy on, each with its own hook. Read the `probably` skill first for the tools, the spend gate and request keys.

1. **Find the product and the Space.** `get_connection`, then `list_spaces`; ask which Space if it's unclear. `list_products` shows products the Space already knows; use one when it matches.
2. **Write the hooks.** Draft as many hooks as the person asked for (variants take 1 to 10; five when they gave no number), each a different angle, one line a creator would say in the first two seconds. Show them as a numbered list and let the person edit, drop or add before anything is prepared.
3. **Get a source video.** Use a video of this product the person names, or one from `list_videos` they pick. Otherwise prepare one: `prepare_video` with the Space, a brief naming the product, the audience and the first hook, and a new `requestKey`. Pass the spend gate (show the preview, wait for their yes, `confirm_spend`).
4. **Wait for its research.** `get_video` for the run, then `wait_for_video` with the cursor until the research stage is accepted (the steps say so) or the run delivers. Tell the person what the crew is doing while you wait.
5. **Prepare the variants.** `prepare_variants` with the `videoId`, the run's ID as `sourceRunId`, `keptThrough: "research"`, and one variant per hook: `name` a short label (`Hook 2: price shock`), `direction` the hook line and its angle, for example `Open with: "I almost returned this, then…". Angle: skeptic turned believer.` Check the fields against the tool's schema first.
6. **Pass the spend gate** for the variants: show the preview (how many variants, what each costs, whether credits cover them), wait for the person's yes, then `confirm_spend`. Without a `confirmationId`, give them the `confirmUrl`.
7. **Track them.** Each variant is a line of the video; `get_video` with `line` reads one. Report each variant's status, and when they deliver, offer `get_media` links or `share_video`.

Done when every variant the person approved is confirmed (or handed over as a `confirmUrl`) and they know how to follow it: the video's name, and that you can check on it with `check-videos`.
