# SignalRoom docs

Mintlify source for [SignalRoom](https://67labs.mintlify.app), the public documentation surface for the Warmr app.

## What SignalRoom is

SignalRoom is private software for TikTok operators. It is the control layer for teams running their own TikTok posting setup on customer-owned iPhones: device lanes, posting runs, account state, logs, cooldowns, and operator approvals in one private cockpit on a Mac.

- **SignalRoom** is the public-facing name and landing layer.
- **Warmr** is the macOS app, repo, and control-plane implementation that actually drives the devices.
- `warmrctl` is the CLI front end agents and operators use to read state and run actions.

SignalRoom is not a hosted phone service, an agency, a broad social platform, or a TikTok API integration. It is operator software for teams that want to buy and run it themselves on their own hardware.

This docs repo is a curated Mintlify mirror. The source of truth for code, runbooks, and internal agent rules remains the private Warmr repo.

## What's in this repo

```
.
├── docs.json                  # Mintlify navigation + theme
├── index.mdx                  # Landing page
├── quickstart.mdx             # Repo-operator quickstart (conservative)
├── signalroom/                # Public SignalRoom pages
│   ├── index.mdx              # Product overview
│   ├── quickstart.mdx         # Operator quickstart
│   ├── safety.mdx             # Claims + safety framing
│   ├── agent-docs.mdx         # How agents should drive warmrctl
│   ├── setup/                 # Mac host, iPhone lanes, dev mode, runner trust
│   ├── operator-guide/        # Lane state, posting runs, cooldowns, approvals
│   ├── how-to/                # Deep practical guides (one knob at a time)
│   └── reference/warmrctl.mdx # CLI reference
├── agents/                    # Repo rules for AI agents working on Warmr
├── reference/                 # Control plane, run/device state models, log events
├── product/                   # Positioning + claims guardrails
└── mintlify/sync-plan.mdx     # How this repo mirrors the private docs tree
```

Everything else (`api-reference/`, `essentials/`, `snippets/`, `ai-tools/`, `agent-ready/`) is unmodified Mintlify starter content kept until SignalRoom pages cover the same ground.

## Local development

```bash
npm i -g mint
mint dev
```

Preview runs at <http://localhost:3000>. The CLI watches files for changes.

If `mint dev` 404s, you're not in a folder with a valid `docs.json`. `cd` into the repo root.

## Publishing

Mintlify is wired to this repo's `main` branch via the GitHub App. **Every push to `main` triggers an automatic production deploy** to <https://67labs.mintlify.app>.

For changes that need review before going live:

1. Branch off `main` (`docs/<topic>-<date>`).
2. Open a PR into `main`.
3. After merge, Mintlify rebuilds within a minute or two.

To preview a feature branch on `*.mintlify.app` before merging, change the deploy branch in the Mintlify dashboard's Git Settings, then switch it back to `main` after.

## Writing guardrails

Public copy in this repo must stay inside SignalRoom's claims guardrails (see [`product/claims-guardrails.mdx`](product/claims-guardrails.mdx)):

- Do not promise platform results or account immunity.
- Do not describe hidden, evasive, or detection-avoidance behavior.
- Use **Current**, **In progress**, **Planned** labels for everything that isn't shipped to operators yet.
- Keep the SignalRoom (public name) ↔ Warmr (repo) relationship intact in copy.

If a page would benefit from operator-only detail that doesn't belong in public docs, leave a stub here and put the full version in the private Warmr repo.

## License

See [`LICENSE`](LICENSE).
