<div align="center">

<img src="docs/banner.svg" alt="shush" width="440" />

**A Claude Code plugin that turns down a model's verbosity by cutting which sentences exist rather than compressing the grammar they are written in.**

![version](https://img.shields.io/badge/version-0.1.0-blue?style=flat-square) ![Claude Code plugin](https://img.shields.io/badge/Claude_Code-plugin-d97757?style=flat-square) ![license](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

[Learn more →](https://seanlindsay.xyz/shush) · [Install](#quick-start) · [Roadmap](#roadmap)

</div>

## Why

I made shush because I was tired of models like Opus 4.8 writing a paragraph to explain a one line edit and narrating every tool call along the way. I tried caveman-style modes that compress grammar by dropping articles and writing in fragments, but I came to the realization that they sometimes increased my token usage through rereads and follow-up questions, and they didn't always activate when they should have. Shush takes the opposite approach and selects rather than compresses, so a sentence only gets written if removing it would change what you do or believe next, while warnings, failing output, and anything you explicitly asked for always survive.

## Features

- **Selection over compression** — cuts whole sentences that carry no decision weight while keeping full grammar, so responses shrink without the rereads that fragment-style modes cause.
- **A hard quality floor** — destructive-action warnings, failing test output, the key tradeoff at a decision point, one sentence of empathy when you're venting, and anything explicitly asked for are never cut.
- **Sentence mechanics for the survivors** — rules adapted from ASD-STE100 Simplified Technical English and Orwell's writing rules: ~20-word sentences, active voice, one instruction per sentence, short plain words, jargon only when it earns its place.
- **Always on via a SessionStart hook** — the mode is injected into every session's context automatically, with no CLAUDE.md edits needed.
- **Three intensity levels** — `/shush lite`, `full` (default), and `ultra` trade how aggressively the sentence test is enforced.
- **A plain off switch** — `stop shush` or "normal mode" reverts to normal output until re-enabled.

## Quick start

```sh
/plugin marketplace add SeanL128/shush
/plugin install shush@shush
```

Requires Claude Code with plugin support; both commands run inside a Claude Code session.

## Configuration

| Option | What it does | Default |
|--------|--------------|---------|
| `/shush lite` | Cuts preamble, narration, and postamble only; explanations stay | — |
| `/shush full` | The sentence test enforced on every line | ✓ |
| `/shush ultra` | One sentence if one suffices; detail only on request | — |
| `stop shush` | Reverts to normal output until re-enabled | — |

## Roadmap

- [x] Selection-over-compression skill with intensity levels
- [x] Always-on SessionStart hook
- [x] Plugin packaging and public marketplace install
- [x] Tuning the quality floor against stress probes (destructive actions, requested depth, frustrated users)
- [x] STE- and Orwell-derived sentence mechanics
- [ ] Tuning against real long-running sessions

## License

[MIT](LICENSE)

---

<div align="center">

Built by Sean Lindsay · [seanlindsay.xyz](https://seanlindsay.xyz)

</div>
