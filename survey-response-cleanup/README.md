# Data Cleanup Project: Customer Survey Response Cleanup

## Overview
Cleaned and consolidated 3,800 customer satisfaction survey responses collected across three different platforms (web form, email survey tool, and in-store tablet). Standardized inconsistent answer formats, resolved encoding errors, removed invalid/bot-like responses, and merged the exports into a single analysis-ready dataset.

---

## The Problem
Because the surveys were collected across three different tools over 18 months, the exports didn't match up cleanly:

- Multiple-choice answers stored inconsistently across platforms (e.g. "5 - Very Satisfied," "Very Satisfied," and "5" all representing the same response)
- Open-text comments containing encoding errors from a platform export (e.g. "great servi ce" / "donâ€™t" instead of "don't")
- Timestamp fields in three different timezones with no timezone label, making it impossible to accurately sequence responses
- ~120 duplicate submissions from users who accidentally submitted the survey twice
- A cluster of ~60 suspicious responses submitted in under 3 seconds each, with identical open-text answers — likely bot or test submissions
- Rating scales inconsistently reversed between platforms (one tool used 1 = best, others used 5 = best)
- Blank "N/A" values entered inconsistently as "N/A," "n/a," "-," or left truly blank

---

## What I Did
1. **Audited each source export separately** — before merging, catalogued the specific format/scale differences per platform so nothing was lost in translation
2. **Standardized the rating scale** — normalized all responses to a single 1–5 scale (5 = best), correcting the reversed-scale platform
3. **Fixed text encoding errors** — cleaned corrupted characters in open-text responses caused by export encoding mismatches
4. **Normalized timestamps** — converted all timestamps to a single timezone (UTC) using each platform's documented export timezone, enabling accurate chronological analysis
5. **Removed duplicates** — flagged and removed 120 duplicate submissions based on matching respondent email + timestamp within a 2-minute window
6. **Filtered invalid responses** — identified and removed the 60 bot-like submissions based on completion time and repeated identical text, documenting the filtering criteria for client transparency
7. **Standardized null values** — unified all "no answer" variants into a single consistent blank/null convention
8. **Final QA pass** — cross-checked response counts per platform against the original raw export counts to confirm no legitimate data was lost during cleanup

**Tools used:** Excel (Power Query for merging/deduplication), Google Sheets for manual review of flagged text responses

---

## Before & After

| Metric | Before | After |
|---|---|---|
| Total responses (raw, 3 sources) | 3,800 | 3,620 |
| Duplicate submissions | ~120 | 0 |
| Suspected bot/invalid responses | ~60 | 0 (removed, documented) |
| Rating scale formats | 3 inconsistent formats | 1 standardized (1–5) |
| Encoding errors in text fields | ~280 | 0 |
| Inconsistent "N/A" representations | 4 variants | 1 standardized null |

**Sample — Before:**
```
Platform | Rating           | Comment                  | Timestamp
Web      | 5 - Very Satisfied | great servi ce           | 2023-11-02 14:03 (local)
Email    | 1                  | donâ€™t recommend        | 11/2/23 9:03am
Tablet   | 5                  | -                        | 02/11/2023 18:03
```

**Sample — After:**
```
Platform | Rating | Comment              | Timestamp (UTC)
Web      | 5      | great service        | 2023-11-02T18:03:00Z
Email    | 5      | don't recommend      | 2023-11-02T14:03:00Z
Tablet   | 5      |                      | 2023-11-02T18:03:00Z
```
*(Note: "Email" platform rating shown corrected from reversed 1–5 scale to standardized scale — original raw value was "1" on a scale where 1 = best.)*

---

## Result / Impact
The client was able to run accurate cross-platform satisfaction trend analysis for the first time, since responses could finally be compared on a consistent scale and timeline. Removing bot/duplicate responses corrected their satisfaction score, which had been artificially skewed by the invalid submissions.

---

## Files in This Project
- `before_sample.csv` — anonymized sample of raw, multi-platform survey data
- `after_sample.csv` — anonymized sample of cleaned, standardized data
- `cleanup_notes.md` — detailed logic/rules used for cleaning, including bot-filtering criteria

---

*Note: This is an illustrative sample project created to demonstrate process and methodology — not an actual client engagement.*
