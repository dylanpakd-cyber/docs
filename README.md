# SignalRoom docs

Mintlify source for [SignalRoom](https://docs.signalrooms.xyz). Public documentation surface for the Warmr app.

## What SignalRoom is

SignalRoom drives 10+ real iPhones from a single Mac, with computer-vision control, four-level auto-recovery, 37-timezone scheduling, and pre-publish activity workflows on every account. Designed for long-term TikTok account stability.

- **SignalRoom** is the public-facing product name.
- **Warmr** is the macOS app and control-plane implementation under the hood.
- `warmrctl` is the CLI front end agents and operators use to read state and run actions.

SignalRoom is software the customer runs. Not a hosted phone service, not a managed-ops agency, not an API integration.

## What's in this repo

```
.
├── docs.json                       Mintlify navigation + theme
├── index.mdx                       Docs site router landing
├── signalroom/                     SignalRoom pages
│   ├── index.mdx                   Product overview, capabilities, FAQ
│   ├── quickstart.mdx              Your first 30 minutes walkthrough
│   ├── safety.mdx                  Why SignalRoom is safe to run
│   ├── agent-docs.mdx              How agents drive warmrctl
│   ├── setup/                      Mac host, iPhone lanes, settings, runner
│   ├── operator-guide/             Lane state, runs, cooldowns, approvals
│   ├── how-to/                     Deep practical guides
│   └── reference/warmrctl.mdx      CLI reference
├── agents/                         Repo rules for AI agents editing Warmr
├── reference/                      Control plane, state models, log events
└── product/                        Positioning, claims
```

## Local development

```bash
npm i -g mint
mint dev
```

Preview runs at http://localhost:3000. The CLI watches files for changes.

If `mint dev` 404s, you're not in a folder with a valid `docs.json`. `cd` into the repo root.

Validate before pushing:

```bash
mint validate
mint broken-links
```

Mintlify's strict MDX parser rejects `<https://...>` autolinks and `<lowercase placeholder>` patterns in body text. Use `[text](url)` markdown links and non-bracket placeholders.

## Publishing

Mintlify is wired to this repo's `main` branch via the GitHub App. Every push to `main` triggers an automatic production deploy to https://docs.signalrooms.xyz (and the canonical Mintlify alias at https://67labs.mintlify.app).

For changes that need review before going live:

1. Branch off `main` (`docs/<topic>-<date>`).
2. Open a PR into `main`.
3. After merge, Mintlify rebuilds within a minute or two.

To preview a feature branch on `*.mintlify.app` before merging, change the deploy branch in the Mintlify dashboard's Git Settings, then switch it back to `main` after.

## Writing voice

Public copy in this repo follows the aggressive Clout-style positioning defined in [`product/claims-guardrails.mdx`](product/claims-guardrails.mdx):

- Confident, comparison-led, benefit-first.
- Concrete numbers from real customer pilots (120 hours/month saved, 4-level recovery in 5-25 sec, 37 timezones, 10+ iPhones from one Mac).
- Claim long-term account stability, real iPhones, computer-vision control, minimal ban-risk vs unofficial APIs.
- The only operational truth that still applies: SignalRoom is software the customer runs, not a hosted service.

No em-dashes between clauses in any docs page. Use commas, periods, or colons.

If a page would benefit from operator-only detail that doesn't belong in public docs, leave a stub here and put the full version in the private Warmr repo.

## License

See [`LICENSE`](LICENSE).
