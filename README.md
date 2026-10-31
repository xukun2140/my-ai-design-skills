# my-ai-design-skills
个人AI设计技能库，收集、整理和复用AI设计工作流

## Skills

- [`interior-design-board`](.agents/skills/interior-design-board/SKILL.md)：规划室内设计概念展板、材料与色彩方案、家具陈设建议，并整理可直接用于图像生成模型的完整提示词。
- [`design-skill-creator`](design-skill-creator/SKILL.md)：分析设计参考并提炼可迁移方法，生成、验证、安装和维护标准化设计 Skill。
- [`commercial-poster-design`](.agents/skills/commercial-poster-design/SKILL.md)：将产品卖点转化为商业海报的主体构图、材质光影、动态效果、视觉层级与文字排版方案。

## 目录结构

```text
my-ai-design-skills/
├── README.md
├── .agents/
│   └── skills/
│       ├── interior-design-board/
│       │   └── SKILL.md
│       └── commercial-poster-design/
│           └── SKILL.md
└── design-skill-creator/
    └── SKILL.md
```

三个 Skill 当前均为单文件指令，不依赖仓库内的脚本、模板或素材。`references/`、`scripts/`、`assets/` 是可按需添加的资源目录，并非当前缺失的文件。

## 获取与安装（Codex）

```sh
git clone https://github.com/xukun2140/my-ai-design-skills.git
cd my-ai-design-skills
```

在本仓库中工作时，Codex 可发现 `.agents/skills/` 中的两个 Skill。根目录下的 `design-skill-creator/` 需要按下面的方式安装后使用。

要在其他项目或所有项目中使用某个 Skill：

1. 按上面的目录结构找到对应 Skill 文件夹，复制整个文件夹，保留其名称和内部的 `SKILL.md`。
2. 仅在某个项目使用：复制到该项目的 `.agents/skills/<skill-name>/`。
3. 用户级使用：复制到 `~/.agents/skills/<skill-name>/`；Windows 中 `~` 指用户主目录，即 `%USERPROFILE%`，PowerShell 中可用 `$env:USERPROFILE`。
4. 若目标已存在，先比较内容，再决定是否更新，避免覆盖本地修改。安装后若未显示，重启 Codex。

例如，用户级安装创建器的目标文件应为 `~/.agents/skills/design-skill-creator/SKILL.md`。这是复制安装，无需安装项目依赖。

目录发现规则见 [OpenAI 官方 Skills 文档](https://learn.chatgpt.com/docs/build-skills)。图片生成及 PDF、演示文稿等文件输出需要运行环境提供相应能力；这些工具不随本仓库提供。`design-skill-creator` 会在通用 `skill-creator` 可用时复用其规范和校验工具，否则报告验证能力限制。

## 调用示例

安装后，在支持 `$` 提及技能的 Codex 界面中显式调用：

```text
$interior-design-board 为一个现代自然风格的客厅规划概念展板，输出文字方案和完整提示词，不生成图片。

$design-skill-creator 将我提供的设计案例提炼成可复用的 Skill，先查重并验证，本次只创建仓库文件，不安装。

$commercial-poster-design 为一款气泡水规划商业海报，说明主体构图、光影和文案层级，只输出文字方案。
```

也可以直接描述任务，由 Codex 根据各 Skill 的 `description` 匹配。调用前应提供空间需求、产品资料或设计案例等输入；要求实际图片或文件时说明交付格式。
