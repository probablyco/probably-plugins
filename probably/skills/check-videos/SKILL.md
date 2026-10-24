---
name: check-videos
description: 'Check on the person''s Probably videos: what is in production, what waits on them, what is delivered. Use when they ask how their videos are doing, whether something is done, or to be told when a video changes.'
---

Reads the person's videos and reports what each needs from them. Read the `probably` skill first for the tools and the spend gate. Reading spends nothing.

1. **List what's open.** `list_videos`, filtered by the Space when the person named one, and by status when they asked about one (`needs-you`, `needs-approval`, `in-production`, `delivered`, `stopped`, `not-started`). Follow `cursor` for more pages only when they asked for everything.
2. **Lead with what waits on them.** For each video in `needs-you` or `needs-approval`, `get_video` and say what it waits for: a question from the crew, a change to confirm, a delivery to approve. Offer the action, never take it unasked: `approve_delivery` approves a delivery; a change that remakes paid work goes through the spend gate.
3. **Then what's moving and what's done.** One line per video in production (its stage, from `get_video`'s steps and activity) and per delivery (offer `get_media` links or `share_video`).
4. **Wait when asked.** To be told when a video changes, call `wait_for_video` with its `cursor` (up to 50 seconds each), again with each new cursor, and report each change in a sentence. Stop when it delivers, fails, waits on the person, or they tell you to stop.

Done when every video the person asked about has its status and its next step, theirs or the crew's, in one short list.
