# 苏格拉底磨刀石

[英文版说明](./README.md)

苏格拉底磨刀石是一个高标准的苏格拉底式认知训练 Skill，用来压力测试和强化理解。它会让 AI 助手扮演「认知边界教练」与「逻辑校准器」：澄清定义、检查证据、测试边界、暴露隐藏前提、使用反例，并进行周期性的元认知复盘。

本仓库提供两个版本：

- 中文 Skill：[`skills/socratic-whetstone-cn`](./skills/socratic-whetstone-cn/SKILL.md)
- 英文 Skill：[`skills/socratic-whetstone-en`](./skills/socratic-whetstone-en/SKILL.md)

它支持 Claude Code、Codex 和 Gemini Gems。

## 安装到 Claude Code

把下面这一行粘贴到 Claude Code：

```text
Install the Claude Code skill from https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-cn into my personal skills directory.
```

英文版：

```text
Install the Claude Code skill from https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-en into my personal skills directory.
```

手动安装：

```bash
tmp="$(mktemp -d)" \
  && git clone --depth 1 https://github.com/SevenTianyu/SocraticWhetstone.git "$tmp/SocraticWhetstone" \
  && mkdir -p "$HOME/.claude/skills" \
  && cp -R "$tmp/SocraticWhetstone/skills/socratic-whetstone-cn" "$HOME/.claude/skills/" \
  && rm -rf "$tmp"
```

如果要安装英文版，把 `socratic-whetstone-cn` 换成 `socratic-whetstone-en`。

安装后重启 Claude Code。个人 Skill 放在 `~/.claude/skills/<skill-name>/SKILL.md`；项目级 Skill 可以放在 `.claude/skills/<skill-name>/SKILL.md`。

## 安装到 Codex

把下面这一行粘贴到 Codex：

```text
$skill-installer install https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-cn
```

英文版：

```text
$skill-installer install https://github.com/SevenTianyu/SocraticWhetstone/tree/main/skills/socratic-whetstone-en
```

手动安装：

```bash
tmp="$(mktemp -d)" \
  && git clone --depth 1 https://github.com/SevenTianyu/SocraticWhetstone.git "$tmp/SocraticWhetstone" \
  && mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills" \
  && cp -R "$tmp/SocraticWhetstone/skills/socratic-whetstone-cn" "${CODEX_HOME:-$HOME/.codex}/skills/" \
  && rm -rf "$tmp"
```

如果要安装英文版，把 `socratic-whetstone-cn` 换成 `socratic-whetstone-en`。

安装后重启 Codex，让新的 Skill 元数据生效。

## 创建 Gemini Gem

Gemini Gems 不安装 `SKILL.md` 文件夹。你需要创建一个 Gem，然后把 prompt 粘贴到 Gem 的 instructions 字段里。

| 版本 | 复制 prompt 并打开 Gemini |
| --- | --- |
| 中文 | <a href="https://seventianyu.github.io/SocraticWhetstone/docs/gemini.html?lang=cn"><strong>复制中文 prompt 并打开 Gemini</strong></a> |
| 英文 | <a href="https://seventianyu.github.io/SocraticWhetstone/docs/gemini.html?lang=en"><strong>复制英文 prompt 并打开 Gemini</strong></a> |

如果上面的辅助页面暂时不可用，使用手动方式：

1. 打开 [Gemini Gems](https://gemini.google.com/gems/create)。
2. 新建一个 Gem。
3. 从下面任意一个文件复制 prompt：
   - [`gemini/socratic-whetstone-cn.md`](./gemini/socratic-whetstone-cn.md)
   - [`gemini/socratic-whetstone-en.md`](./gemini/socratic-whetstone-en.md)
4. 粘贴到 Gem 的 instructions 字段。
5. 把 Gem 命名为 `苏格拉底磨刀石` 或 `Socratic Whetstone`。

说明：GitHub README 不能直接执行剪贴板 JavaScript。上面的链接会打开一个 GitHub Pages 辅助页，在那里按钮可以复制 prompt 并跳转到 Gemini。

## 使用方式

安装后，在新对话里显式调用：

```text
Use $socratic-whetstone-cn to help me pressure-test my current understanding of [topic].
```

或者：

```text
Use $socratic-whetstone-en to help me pressure-test my current understanding of [topic].
```

这个 Skill 会先建立基线：

- 主题
- 当前理解
- 背景
- 目标
- 模式
- 强度

然后每次只推进一个诊断性问题。

## 仓库结构

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

## 参考

- [Claude Code skills 文档](https://code.claude.com/docs/en/skills)
- [OpenAI skills 目录和 Codex 安装示例](https://github.com/openai/skills)
- [Gemini Gems 帮助](https://support.google.com/gemini/answer/15146780)
