# Content OS

**给 Claude Code 用的个人内容系统。** 想法出现的瞬间连同心理现场一起接住；内容有效时把背后的结构留存为可复用模版；再把两者组合成平台原生的内容（公众号、X、LinkedIn、小红书……）——用*你的*人设、*你的*声音写出来。

[English docs →](README.md)

## 为什么做它

大多数个人知识工具是"整理系统"：你给它什么，它原样还给你什么。Content OS 建立在三个判断上：

1. **想法的价值绑定在它出现时的心理现场。** 捕捉必须低摩擦且保存上下文——现场由 agent 从对话里替你填好，你只需要说一句"记录这个想法"。
2. **内容有效时，可复用的是结构，不是内容本身。** 开头的钩子模式、论证顺序、封面的视觉公式——抽成模版卡，失败模式（When Not to Use）必填，状态靠真实使用挣来。
3. **没有"人"的内容读起来像设计说明书。** 每次捕捉和每次写稿都过两层：人设（谁在说话、押什么赌注）和声音档案（怎么说、哪些词绝不用）。

## 安装

```
/plugin marketplace add Shiinama/content-os
/plugin install content-os@content-os
```

装完落地两个 skill：**content-os**（捕捉 / 模版 / 生产 / 管线）和 **profile**（人设引导）。

<details>
<summary>手动安装（不走 plugin 系统）</summary>

```bash
git clone https://github.com/Shiinama/content-os.git
ln -s "$(pwd)/content-os/skills/content-os" ~/.claude/skills/content-os
ln -s "$(pwd)/content-os/skills/profile"    ~/.claude/skills/profile
```

</details>

## 快速开始

第一次使用——先建人设（5 分钟，大部分内容 agent 会从你分享的材料里替你起草）：

> 建一下我的人设

然后正常说话就行：

| 你说 | 发生什么 |
|---|---|
| "记录这个想法：……" | 想法卡即刻写入，上下文从对话自动填充 |
| "把这个结构存成模版" | 结构（视觉风格则是图片本身）成为可复用的模版卡 |
| "想写篇文章"（不用带主题） | 从**你的想法池**里提候选选题，按成熟度和人设契合度排序 |
| "把这个想法写成公众号文章" | 按平台档案、用你的声音出稿，封面/配图 prompt 一并备好 |
| "给这篇配图" | 用你存的视觉模版生图（有花费闸门——没有你的明确同意不会花一分钱） |
| "盘点一下我的内容系统" | 一屏摘要：想法、模版、在途稿件，外加至多 3 条具体的下一步 |
| "公众号那篇 3000 阅读" | 记录数据快照，并把经验回写到产出它的模版上 |

## 组织方式

```
你的数据（plugin 更新不受影响）              plugin 本体（只读）
~/.claude/content-os/                        skills/
├── profile/profile.md   ← 谁在说话          ├── content-os/
├── ideas/               ← 想法卡            │   ├── SKILL.md          （路由）
├── templates/           ← 模版卡            │   └── references/       （捕捉/模版/生产/管线、
└── content/             ← 稿件、voice.md    │                          平台档案）
                                             └── profile/          （人设引导）
```

- **数据根**：默认 `~/.claude/content-os`，可用环境变量 `CONTENT_OS_HOME` 覆盖；首次使用自动创建。
- **多机同步**：给数据根 `git init` 并挂一个私有远程——之后每次写入自动 commit + push。
- **内置平台**：公众号、X、LinkedIn、即刻、小红书、知乎、抖音。往 `content/platforms/` 放一个文件即可新增或覆盖任何平台。
- **声音与人设归你**：`content/voice.md`（写作样本、语气规则、AI 味黑名单）与 `profile/profile.md`（身份、赌注、长期追问线）在每次写稿前必读。

## 管线

```
profile（人设）─────────── 罩在下面所有环节上的第一视角
想法池               模版池                  内容池
inbox → structured × candidate → validated → drafting → review → published
      → expandable   （文字 + 视觉）          （分平台变体 + 配图）
```

状态是挣来的，不是声明的：模版真用过且有效才升 `validated`；想法只有稿件发布了才是 `published`；每篇稿件都记录它来自哪些卡、用了哪些模版。

## 卸载

```
/plugin uninstall content-os@content-os
```

安装、更新、卸载都不会碰你的数据根。

## License

MIT
