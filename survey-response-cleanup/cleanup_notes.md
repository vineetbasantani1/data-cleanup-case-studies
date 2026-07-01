# Cleanup Logic & Rules — Survey Response Project

## 1. Rating Scale Standardization
- Identified which source platform used a reversed scale (1 = best) vs standard (5 = best)
- Converted all ratings to a single 1–5 scale where 5 = best

## 2. Text Encoding Fixes
- Corrected corrupted characters from export encoding mismatches (e.g. "â€™" → apostrophe)
- Fixed stray whitespace inserted mid-word by platform export bugs (e.g. "servi ce" → "service")

## 3. Timestamp Normalization
- Converted each platform's local timestamp to UTC using that platform's documented export timezone
- Standardized to ISO 8601 format for consistent sorting/analysis

## 4. Duplicate Removal
- Duplicate criteria: matching respondent email + timestamp within a 2-minute window
- Kept the first valid submission, removed subsequent duplicates

## 5. Invalid/Bot Response Filtering
- Flagged submissions with completion time under 3 seconds AND identical open-text responses across multiple entries
- Removed after manual spot-check confirmed pattern was not legitimate rapid-response behavior
- Documented exact filtering criteria and count removed for full client transparency

## 6. Null Value Standardization
- Unified "N/A," "n/a," "-," and blank into a single consistent null representation

---

*Principle followed throughout: document every judgment call (especially removals) so the client can audit or challenge any decision.*
