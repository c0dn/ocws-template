---
description: Write a conventional commit for the staged changes
---

Commit the staged changes.

1. Run `git diff --staged`. If nothing is staged, say so and stop.
2. Check `git log --oneline -10` and match the repository's commit style.
3. Write a conventional commit subject (`feat:`, `fix:`, `docs:`, ...) under 72
   characters that says what the change does. Add a body only if the subject
   cannot carry the reason.
4. Run `git commit` and show the result. Do not push.
