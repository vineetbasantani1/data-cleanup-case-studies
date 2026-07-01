# Cleanup Logic & Rules — Product Inventory Project

## 1. Category Standardization
- Built a mapping table converting all category label variants (spacing, punctuation, capitalization) to a single controlled taxonomy
- Example: "Home & Kitchen," "Home/Kitchen," "home-kitchen" → "Home & Kitchen"

## 2. Duplicate SKU Resolution
- Duplicate criteria: matching SKU (case-insensitive)
- Kept the most recently updated stock/price data; merged any variant details split across duplicate rows

## 3. Price Formatting
- Stripped currency symbols and stray characters
- Converted all prices to a consistent two-decimal numeric format
- Flagged (not assumed) listings where it was unclear whether tax was included

## 4. Stock Field Handling
- Distinguished confirmed out-of-stock ("0") from missing/unverified data
- Blank stock fields were flagged for client confirmation rather than defaulted to 0

## 5. Title/Description Cleanup
- Removed leftover CSV export artifacts (stray commas, escaped quotes)
- Standardized unit labeling (e.g. "12 oz" vs "12oz") to a single convention

---

*Principle followed throughout: prioritize accuracy over completeness — flag uncertainty rather than silently guessing.*
