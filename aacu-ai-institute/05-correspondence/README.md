# Correspondence Log

A running, searchable archive of email and other correspondence about the Institute.

- **Newest entries go at the top** of [`correspondence.md`](correspondence.md).
- Every entry gets a heading of the form `## YYYY-MM-DD — Sender — Subject` so the file
  sorts and greps cleanly.
- Email bodies are kept close to verbatim; links, deadlines, and names are preserved exactly.
- Anything actionable is pulled up into the **Action items extracted** block at the top of
  the file and, where it has a date, into the deadlines table in the
  [main README](../README.md).

## How to add to it

Just paste an email into the chat and say it's for the Institute — it gets appended in the
same format, action items extracted, and any affected files (deadlines, logistics, schedule)
updated at the same time.

## Searching it

```bash
grep -in "zoom"        05-correspondence/correspondence.md   # find a topic
grep -n  "^## "        05-correspondence/correspondence.md   # list every message
grep -n  "TODO\|Due:"  05-correspondence/correspondence.md   # find open items
```
