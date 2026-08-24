# xAI Marketplace — grokbotwallet entry & PR

## Catalog entry (append to `plugins` in `.grok-plugin/marketplace.json`)

```json
{
  "name": "grokbotwallet",
  "description": "Governed wallet for Grok agents: budgets, allowlists, operator modes, and human approval before money or consequential actions move.",
  "category": "development",
  "source": {
    "source": "url",
    "url": "https://github.com/richard7463/grokbotwallet.git",
    "sha": "6459abb105301efee81cb0ed794c862e4dcf04b1"
  },
  "homepage": "https://github.com/richard7463/grokbotwallet",
  "keywords": [
    "grokbotwallet",
    "governed wallet",
    "agent approval",
    "human in the loop",
    "budget policy"
  ],
  "domains": [
    "grokbotwallet.io"
  ]
}
```

## PR body

```markdown
## What this PR does

Adds `grokbotwallet` as a third-party plugin so Grok Build agents get a
governed wallet: budgets, allowlists, operator modes, and human approval
before money or consequential actions move.

- Plugin name: `grokbotwallet`
- Type: remote source
- Source URL + pinned SHA:
  `https://github.com/richard7463/grokbotwallet.git` @ `6459abb105301efee81cb0ed794c862e4dcf04b1`
- Homepage: https://github.com/richard7463/grokbotwallet

## Ownership

- [x] I own this plugin and have the right to distribute it.

## Security

- [x] No `curl | bash`, remote-code download/exec, or eval patterns.
- [x] No secrets, API keys, or credentials in the plugin.
- [x] The plugin never asks users or agents for private keys or passwords.
- [x] Remote source is pinned to a full commit SHA.

## Checklist

- [x] `name` is kebab-case and unique.
- [x] `sha` is a full 40-character lowercase commit SHA (public + reachable).
- [x] `.grok-plugin/plugin-index.json` regenerated via
      `python3 scripts/generate-plugin-index.py`.
- [x] `python3 scripts/validate-catalog.py` passes.
- [x] Homepage, clear description, brand-scoped keywords and domains.
```

## Steps to submit

```bash
# 1. Push the plugin repo (already a git repo at integrations/grokbotwallet)
git push origin main

# 2. Pin the real SHA
git ls-remote https://github.com/richard7463/grokbotwallet.git HEAD

# 3. Replace REPLACE_WITH_FULL_COMMIT_SHA in the entry + PR body

# 4. Fork xai-org/plugin-marketplace, branch from main, append the entry,
#    regenerate the index, validate:
python3 scripts/generate-plugin-index.py
python3 scripts/validate-catalog.py
python3 scripts/generate-plugin-index.py --check

# 5. Open the PR with the body above, wait for CI + code-owner review.
```
