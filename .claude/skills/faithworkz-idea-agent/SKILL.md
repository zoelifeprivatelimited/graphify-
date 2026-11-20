---
name: faithworkz-idea-agent
description: Weekly content research for Zoe Life brands (Faithworkz operations). Use when asked to "run the idea agent", "get content ideas", or on the weekly Sunday trigger. Produces 10 ranked post ideas per brand.
---

# Faithworkz Idea Agent

Stage 1 of the Faithworkz pipeline: **Idea** → Draft → Awaiting approval → Scheduled → Posted.

## Spec

| Field | Value |
|---|---|
| Name | Faithworkz Idea Agent |
| Purpose | Find what the audience of each brand cares about this week and turn it into 10 ranked post ideas per brand. |
| Trigger / schedule | Weekly, Sunday 18:00 IST. Also on demand: "run idea agent". |
| Inputs | Active brands (default: Zoe Life, IAOMAI); last 4 weeks of post metrics from the Posting Agent log; Indian health calendar (below); competitor handles list (Abel to supply); brand docs in Drive (`Zoe Life/IAOMAI/IAOMAI – Brand & Product Overview`). |
| Tools | Web search; Google Drive (read brand docs); Instagram via Composio (read own recent media + insights); Private Agent Terminal store (write ideas). |
| Output | Per brand, a ranked table of 10 ideas: rank, hook, angle, format (reel / carousel / static / text), platform, why it could perform, health claim involved (yes/no), source needed. Written to the Terminal's content queue with stage `Idea`. |
| Approval gate | None to produce ideas. Ideas never go public. Any idea that needs a health claim is marked `needs source`. |
| Success metric | At least 3 of each week's top-5 ideas beat the brand's median engagement rate once posted. |

## Steps

1. Read the brand overview docs and the claims guidance. Never propose an idea that needs a cure, treatment, reversal or guarantee claim.
2. Pull the last 4 weeks of metrics from the Posting Agent log. Note the top 3 formats and hooks.
3. Check the health calendar for the next 14 days and current Indian news on the brand's topics.
4. Look at competitor posts (only handles Abel has listed). Note angles, never copy text or visuals.
5. Score each idea 1–5 on: relevance to the audience this week, fit with past winners, ease of production, compliance risk (inverse). Rank by total.
6. Write the table to the queue. Hand the top 3 per brand to the Writer Agent.

## Indian health calendar (seed, verify each year)

- Jan: winter wellness; Makar Sankranti / Pongal (sweets season)
- Feb 4: World Cancer Day
- Mar: Holi (sweets); Mar 24: World TB Day
- Apr 7: World Health Day
- May 31: World No Tobacco Day
- Jun 21: International Yoga Day
- Jul: monsoon health (water-borne illness)
- Sep 1–30: Poshan Maah (National Nutrition Month)
- Oct–Nov: Diwali and wedding season (sweets, late meals)
- Nov 14: World Diabetes Day
- Dec: winter immunity season

## Brand rules

- Spell brands exactly: Zoe Life, IAOMAI, Zoe Life Garden, Faithworkz.
- IAOMAI products: say "helps support healthy blood sugar levels as part of a balanced diet and active lifestyle". Never say cures, reverses, treats, or replaces medicine. Avoid "Miracle", "100% natural" and "pure" until the regulatory review is done.
