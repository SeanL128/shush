# shush

A Claude Code plugin that turns down a model's verbosity by cutting which sentences exist rather than compressing the grammar they are written in.

![version](https://img.shields.io/badge/version-0.1.0-blue?style=flat-square)
![Claude Code plugin](https://img.shields.io/badge/Claude_Code-plugin-d97757?style=flat-square)
![license](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

## Why

I made shush because I was tired of models like Opus 4.8 writing a paragraph to explain a one line edit and narrating every tool call along the way. I tried caveman-style modes that compress grammar by dropping articles and writing in fragments, but I found that they sometimes increased my token usage through rereads and follow-up questions, and they didn't always activate when they should have. Shush takes the opposite approach and selects rather than compresses, so every sentence the model writes has to change what you do or believe next or it never gets written, while warnings, failing output, and anything you explicitly asked for always survive.

**Learn more →** [seanlindsay.xyz/shush](https://seanlindsay.xyz/shush)


## Quick start

```sh
/plugin marketplace add SeanL128/shush
/plugin install shush@shush
```

A session-start hook keeps shush active in every session automatically, with no CLAUDE.md edits needed. Tune it with `/shush lite|full|ultra` or turn it off with `stop shush`.

## What I learned / what broke

- Compression and selection are different levers. Mangled grammar reads as cheaper but forces clarifying turns that cost more than the articles it saved, while cutting whole sentences that carry no decision weight is what actually reduces tokens.
- A skill's description matching is too flaky to carry an always-on behavior, so the reliable pattern is a session-start hook that injects the mode directly into context.

---
Built by Sean Lindsay · [seanlindsay.xyz](https://seanlindsay.xyz)
