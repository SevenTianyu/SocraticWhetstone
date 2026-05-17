# Socratic Whetstone

[Chinese version](./README.zh-CN.md)

Socratic Whetstone is a high-standard Socratic coaching skill for pressure-testing understanding. It helps an AI assistant act as a cognitive boundary coach and logic calibrator: define terms, inspect evidence, test boundaries, surface hidden assumptions, use counterexamples, and run periodic metacognitive reviews.

This repository provides two versions:

- Chinese skill: [`skills/socratic-whetstone-cn`](./skills/socratic-whetstone-cn/SKILL.md)
- English skill: [`skills/socratic-whetstone-en`](./skills/socratic-whetstone-en/SKILL.md)

It supports Claude Code, Codex, and Gemini Gems.

## Install in Claude Code

Paste one line into Claude Code:

```text
Install the Claude Code skill from https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-en into my personal skills directory.
```

Chinese version:

```text
Install the Claude Code skill from https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-cn into my personal skills directory.
```

Manual fallback:

```bash
tmp="$(mktemp -d)" \
  && git clone --depth 1 https://github.com/SevenTianyu/SocraticWhetstone.git "$tmp/SocraticWhetstone" \
  && mkdir -p "$HOME/.claude/skills" \
  && cp -R "$tmp/SocraticWhetstone/skills/socratic-whetstone-en" "$HOME/.claude/skills/" \
  && rm -rf "$tmp"
```

For the Chinese version, replace `socratic-whetstone-en` with `socratic-whetstone-cn`.

Restart Claude Code after installation. Personal Claude Code skills live under `~/.claude/skills/<skill-name>/SKILL.md`; project skills can live under `.claude/skills/<skill-name>/SKILL.md`.

## Install in Codex

Paste one line into Codex:

```text
$skill-installer install https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-en
```

Chinese version:

```text
$skill-installer install https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-cn
```

Manual fallback:

```bash
tmp="$(mktemp -d)" \
  && git clone --depth 1 https://github.com/SevenTianyu/SocraticWhetstone.git "$tmp/SocraticWhetstone" \
  && mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills" \
  && cp -R "$tmp/SocraticWhetstone/skills/socratic-whetstone-en" "${CODEX_HOME:-$HOME/.codex}/skills/" \
  && rm -rf "$tmp"
```

For the Chinese version, replace `socratic-whetstone-en` with `socratic-whetstone-cn`.

Restart Codex after installation so the new skill metadata is picked up.

## Create a Gemini Gem

Gemini Gems do not install `SKILL.md` folders. Create a Gem and paste the prompt into the Gem instructions field.

| Version | Copy prompt and open Gemini |
| --- | --- |
| English | <a href="https://seventianyu.github.io/SocraticWhetstone/docs/gemini.html?lang=en"><img src="https://img.shields.io/badge/Copy%20prompt%20%2B%20open-Gemini-4285F4?style=for-the-badge&logo=googlegemini&logoColor=white" alt="Copy English prompt and open Gemini"></a> |
| Chinese | <a href="https://seventianyu.github.io/SocraticWhetstone/docs/gemini.html?lang=cn"><img src="https://img.shields.io/badge/Copy%20prompt%20%2B%20open-Gemini-4285F4?style=for-the-badge&logo=googlegemini&logoColor=white" alt="Copy Chinese prompt and open Gemini"></a> |

If the helper page is not available yet, use the manual path:

1. Open [Gemini Gems](https://gemini.google.com/gems/create).
2. Create a new Gem.
3. Copy the prompt from one of these files:
   - [`gemini/socratic-whetstone-en.md`](./gemini/socratic-whetstone-en.md)
   - [`gemini/socratic-whetstone-cn.md`](./gemini/socratic-whetstone-cn.md)
4. Paste it into the Gem instructions field.
5. Name the Gem `Socratic Whetstone`.

Note: GitHub README pages cannot run clipboard JavaScript directly. The badge opens a small GitHub Pages helper where the button can copy the prompt and jump to Gemini in one click.

## Use

After installing, start a new conversation and ask for the skill explicitly:

```text
Use $socratic-whetstone-en to help me pressure-test my current understanding of [topic].
```

or:

```text
Use $socratic-whetstone-cn to help me pressure-test my current understanding of [topic].
```

The skill first establishes a baseline:

- topic
- current understanding
- background
- goal
- mode
- intensity

Then it proceeds with one diagnostic question at a time.

## Repository Layout

```text
.
├── README.md
├── README.zh-CN.md
├── skills/
│   ├── socratic-whetstone-cn/
│   │   ├── SKILL.md
│   │   └── agents/openai.yaml
│   └── socratic-whetstone-en/
│       ├── SKILL.md
│       └── agents/openai.yaml
├── gemini/
│   ├── socratic-whetstone-cn.md
│   └── socratic-whetstone-en.md
└── docs/
    └── gemini.html
```

## References

- [Claude Code skills documentation](https://code.claude.com/docs/en/skills)
- [OpenAI skills catalog and Codex installer examples](https://github.com/openai/skills)
- [Gemini Gems help](https://support.google.com/gemini/answer/15146780)
