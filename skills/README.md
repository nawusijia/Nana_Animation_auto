# 娜娜剧作 Skills（独立开源版）

这两份 Skill 是 **写故事 / 写剧本的 Agent 规则**，不是模型权重、视频生成 API 或自动运行程序。

| Skill | 入口 | 作用 | 产物 |
| --- | --- | --- | --- |
| 娜娜剧本大纲引擎（story-outline） | [story-outline/SKILL.md](story-outline/SKILL.md) | 原创、改编、优化故事；检查钩子、核心玩法、升级、人物弧光、结局余味 | Story Blueprint / 故事大纲 |
| 娜娜完整剧本编译（screenplay-writing） | [screenplay-writing/SKILL.md](screenplay-writing/SKILL.md) | 从确认的大纲与素材写成逐字完整剧本，落实【画面】【台词】【动作】与动作因果 | 完整逐字剧本 |

## 使用方法

**不需要安装整个 H3 导演台，也不需要额外模型 API Key。** 只要使用的 AI Agent 支持读取本地 Markdown 文件，就可以独立使用：

1. 下载本仓库，在自己的 Agent 对话中指定要读取的 SKILL.md（也可以将这两个文件夹复制到你使用的 Agent 所支持的 Skills 目录）。
2. 告诉 Agent 是**原创**还是**改编**；改编时提供有权使用的原始文本，并明确哪些台词、人物、剧情必须保留。
3. 先调用 `story-outline` 得到故事大纲；确认后调用 `screenplay-writing` 得到完整剧本。
4. 检查正文里的角色台词、动作因果和场景连续性；任何已确认的台词都不能被 Agent 顺手润色。

**最简调用示例（原创）：**

```text
请读取本仓库 skills/story-outline/SKILL.md，
为我写一个 3 分钟原创悬疑短片大纲。
请先给 Story Blueprint，不要拆镜头。题材和约束：……
```

```text
我确认刚才的大纲。请读取 skills/screenplay-writing/SKILL.md，
使用 original 模式写成完整逐字剧本。
格式用【画面】【台词】【动作】，不要直接生成分镜或视频 Prompt。
```

**最简调用示例（改编）：**

```text
请读取 skills/story-outline/SKILL.md，按 adaptation 模式分析这份原文。
保留原文已锁定的台词、说话人及顺序；发现冲突先标出，不要自行修改。
先输出可供我确认的 Story Blueprint。以下是原文：……
```

## 与本仓库 H3 导演台的关系

本仓库的 H3 Agent-owned 工作流以**已有完整剧本**为输入，然后按 `/api/agent/bootstrap` 返回的阶段协议处理 Scene、资产、Shot、Sequence 和 Prompt。

这两份剧作 Skill 是**可选的前置创作工具**，当前不会自动注册为 H3 服务端的新增阶段，也不改变现有阶段的 JSON 合同。如果想用两份 Skill 写出的剧本跑 H3，先确认剧本正文，再粘贴到 H3 的「新建项目 / 保存剧本」输入区域，随后交给 Agent 按仓库 [AGENTS.md](../AGENTS.md) 继续执行。

**边界：** 大纲 ≠ 完整剧本；完整剧本 ≠ Scene 导演蓝图；这两份 Skill 不包含 Scene Directing、镜头拆分、生成提示词，也不带任何私人项目文件或 API 凭据。

## 使用与署名

这两份 Skill 随本仓库按根目录 [MIT License](../LICENSE) 开源。欢迎学习、二次修改和使用，保留相应版权与许可声明。
