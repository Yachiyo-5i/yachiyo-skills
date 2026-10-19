# yachiyo-skills

我自己的 Claude skill 合集。每个 skill 是一个独立目录，里面有 `SKILL.md`（必需）和按需加载的 `references/`、`assets/`。

## Skills

| Skill | 说明 | 技术栈 |
|---|---|---|
| [`apple-dark-ui`](./apple-dark-ui) | 按 Apple HIG（含 Liquid Glass）设计和实现**深色** Web 界面：分层模型、近黑配色与组件顶光、字号体系、同心圆角、玻璃与标准材质、Chromium 上的 SVG 折射、组件与页面模板、移动端胶囊 Tab Bar、实现中的坑和验收清单 | React + Tailwind CSS v4 |

## 快速开始

```bash
npx skills add Yachiyo-5i/yachiyo-skills
```

按提示选择 skill 和要安装到的 agent（Claude Code、Cursor 等）即可。装好后直接对话试试：

> 用 apple-dark-ui 做一个深色的订单后台首页，桌面带侧边栏，移动端用胶囊 Tab Bar。

只装其中一个：`npx skills add Yachiyo-5i/yachiyo-skills --skill apple-dark-ui`。

## 其他安装方式

<details>
<summary>手动安装（Claude Code）</summary>

把需要的 skill 目录拷贝或软链到 skills 目录，Claude 会按 `SKILL.md` 里的 `description` 自动判断是否使用：

```bash
# 个人级：所有项目可用
ln -s "$(pwd)/apple-dark-ui" ~/.claude/skills/apple-dark-ui

# 项目级：只在某个项目里可用
cp -R apple-dark-ui /path/to/project/.claude/skills/
```

</details>

<details>
<summary>Claude 桌面端 / claude.ai</summary>

到 [Releases](https://github.com/Yachiyo-5i/yachiyo-skills/releases) 下载 `<name>.skill`，在设置里上传即可。每次打 `v*` tag 会由 GitHub Actions 自动打包。

</details>

## 目录约定

```
<skill-name>/
├── SKILL.md          # 必需：frontmatter（name、description）+ 主要指令，尽量控制在 500 行内
├── references/       # 按需读取的详细文档；SKILL.md 里写明什么时候读哪个
└── assets/           # 可以直接拷进项目的代码、模板、字体等
```

- `description` 要同时写清楚「做什么」和「什么时候用」，这是触发 skill 的主要依据。
- 每个 skill 保持自包含，不引用其他 skill 或具体项目里的路径、名称。
- 新增 skill 后，在上面的表格里补一行。

## 许可

[MIT](./LICENSE) © Yachiyo-5i

skill 中提到的字体（Literata、思源宋体、JetBrains Mono）不包含在本仓库内，它们各自使用 SIL OFL 1.1 授权，请按其协议使用。
