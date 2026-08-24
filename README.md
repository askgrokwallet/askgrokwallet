# grokbotwallet — governed wallet for Grok agents

Agents can think, trade, and pay. grokbotwallet decides what they are allowed
to do — inside human-defined rules, with a verifiable receipt for every
outcome.

```text
agent request -> policy (allow / ask / deny) -> execute or approve -> proof
```

This repository is the **Grok Build plugin package** for grokbotwallet. The app
itself (policy engine, approval inbox, vault contracts) lives in the
`grokbotwallet` project; this package is what Grok installs.

## Install

```bash
# From GitHub (recommended — pinned SHA)
grok plugin install richard7463/grokbotwallet --trust

# Or from a local path during development
grok plugin install ./integrations/grokbotwallet --trust
```

After install, the `grokbotwallet` skill appears in `/skills`. Enable it for a
Bot via Settings → Plugins where needed.

## What the skill does

1. Compiles plain-English policy ("payments under $50 run automatically; over
   $50 ask me; never pay blacklisted merchants; daily budget $200").
2. Evaluates every request: `allow` / `ask` / `deny`.
3. `ask` requests land in the grokbotwallet approval inbox; the operator
   approves or denies from any device.
4. Approved and blocked outcomes both produce a receipt.

## Files

| Path | Purpose |
| --- | --- |
| `SKILL.md` | The skill (canonical, mirrors the app's skill). |
| `.grok-plugin/plugin.json` | Plugin manifest. |
| `examples/approval-request.json` | Sample approval request payload. |
| `examples/policy-example.txt` | Sample plain-English policy. |
| `scripts/smoke.mjs` | Local structure validation. |
| `docs/MARKETPLACE_ENTRY.md` | Exact catalog entry + PR body for the xAI marketplace. |

## Security

- The plugin never asks for private keys, passwords, or credentials.
- Policy, budgets, and allowlists are operator-defined; the skill never
  invents them.
- Blocked actions return a reason and are never executed.
- Receipts record who, what, how much, verdict, decision, and timestamps.

## Publish checklist

See `docs/MARKETPLACE_ENTRY.md` — entry JSON, PR body, SHA pinning steps, and
the local validation commands.

## License

MIT.
