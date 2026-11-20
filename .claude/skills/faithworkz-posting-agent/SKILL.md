---
name: faithworkz-posting-agent
description: Publishes only APPROVED Faithworkz posts at their approved time through Composio (Instagram, Facebook, LinkedIn), logs the URL, and collects 48-hour metrics. Use on the hourly posting trigger or when asked to "publish approved posts" or "collect post metrics".
---

# Faithworkz Posting Agent

Stage 4–5: Idea → Draft → Awaiting approval → **Scheduled** → **Posted**.

## Spec

| Field | Value |
|---|---|
| Name | Faithworkz Posting Agent |
| Purpose | Publish approved posts on time and feed results back to the Idea Agent. |
| Trigger / schedule | Hourly, 07:00–22:00 IST: publish any `Scheduled` post due in the past hour. Daily 10:00 IST: collect metrics for posts that are 48 h old. |
| Inputs | Posts in `Scheduled` with an APPROVE record; platform accounts in Composio. |
| Tools | Composio: Instagram (`INSTAGRAM_POST_IG_USER_MEDIA` → `INSTAGRAM_POST_IG_USER_MEDIA_PUBLISH`), Facebook Page (`FACEBOOK_CREATE_PHOTO_POST`), LinkedIn page (`LINKEDIN_CREATE_LINKED_IN_POST`); insights tools for metrics; Private Agent Terminal store. |
| Output | Post URL and post ID logged per platform; stage → `Posted`. After 48 h: reach, impressions, likes, comments, saves, shares, engagement rate, written to the metrics log. |
| Approval gate | Refuses any post without a matching APPROVE record for that exact caption, image, platform and time. |
| Success metric | 100% of approved posts published within 15 minutes of the approved time; zero unapproved posts. |

## Account map (to be confirmed by Abel)

| Brand | Instagram | Facebook Page | LinkedIn page |
|---|---|---|---|
| Zoe Life | @zoe.life.garden (Abel's choice, 20 Nov 2026) | not connected | not connected |
| IAOMAI | @zoe.life.garden (Abel's choice, 20 Nov 2026) | not connected | not connected |
| Zoe Life Garden | @zoe.life.garden (connected, Business account) | not connected | not connected |

Post a brand's content only to the account Abel has mapped it to above.

## Steps

1. Check the APPROVE record. If missing or the content changed, stop and alert Abel.
2. Check the image URL returns image bytes (Instagram needs a direct JPEG URL).
3. Publish. On failure, wait 2 minutes and retry once. On a second failure, stop and alert Abel with the error. Never blind-retry Facebook (it can create duplicates): check the Page feed first.
4. Log the URL. Move the post to `Posted`.
5. After 48 h, collect metrics and hand them to the Idea Agent.

## Never

Delete, edit or boost a live post, run ads, or reply to comments without Abel's explicit approval.
