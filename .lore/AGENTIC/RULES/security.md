---
description: Security rules for all code
---

## 1. Credential Protection
Every file you write could be committed, leaked, or read by another agent. Act accordingly.

## 2. Reference, Don't Embed
Reference vaults and env var names — repos get leaked, and secrets in version history are permanent.
- Store the location (vault path, env var name, secret manager key), not the value itself.
- `.env` files, credential JSONs, and key files belong in `.gitignore`. Before creating one, verify it's listed.
- If you encounter an exposed secret, flag it to the operator immediately.

## 3. Sanitize What You Generate
Use obviously fake placeholders in examples and configs — generated values that look real become real problems.
- Use `example.com`, `TOKEN_HERE`, `<your-api-key>`, `sk-test-xxx` — patterns that are clearly not real.
- Reference the source instead of echoing secret values into files.
- Don't embed URLs containing auth tokens or session IDs.

## 4. Validate at Boundaries
Trust internal code. Verify external input.
- Parameterize database queries. Escape output for the rendering context (HTML, shell, SQL).

## 5. Escalate Uncertainty
When uncertain whether data is sensitive, ask the operator before writing.
