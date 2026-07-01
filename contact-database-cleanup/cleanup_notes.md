# Cleanup Logic & Rules

This document outlines the specific rules applied during the cleanup process, for transparency and reproducibility.

## 1. Name Formatting
- Standardized to Title Case (e.g. "JOHN SMITH" / "john smith" → "John Smith")
- Trimmed leading/trailing/double whitespace

## 2. Email Validation
- Corrected malformed addresses (e.g. double "@@", missing domain)
- Standardized to lowercase
- Flagged any entries that couldn't be confidently corrected for manual review

## 3. Date Standardization
- Converted all date formats (M/D/YY, MM-DD-YYYY, YYYY/MM/DD, etc.) to ISO format: YYYY-MM-DD
- Blank/missing dates left blank and flagged rather than guessed

## 4. Phone Number Formatting
- Standardized to XXX-XXX-XXXX format
- Incomplete numbers (e.g. missing final digits) flagged for manual review rather than auto-completed, to avoid introducing incorrect data

## 5. Duplicate Removal
- Duplicate criteria: matching Name (case-insensitive) + Email
- Kept the most complete/recent record when duplicates were found

## 6. Missing Data
- Missing values were NOT auto-filled or guessed
- All gaps were flagged in a separate review column (removed from the public sample for clarity) so the client could make the final call

---

*Principle followed throughout: prioritize accuracy over completeness — flag uncertainty rather than silently guessing.*
