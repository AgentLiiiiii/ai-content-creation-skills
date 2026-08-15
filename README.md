# AI 内容创作 Skills｜使用说明

本仓库提供可重复使用的 AI 内容创作 Skill。每个 Skill 都有独立的 `SKILL.md`，由 Agent 读取后按其运行环境安装和使用。

仓库地址：<https://github.com/AgentLiiiiii/ai-content-creation-skills>

## 已包含的 Skill

| Skill | 适用任务 | 目录 |
| --- | --- | --- |
| **视频提示词工艺** | 将静态分镜与情绪目标转为图生视频动态提示词、情绪化运镜与镜头动态设计。 | `skills/video-prompt-craft` |
| **五维表演提示词** | 根据分镜图拆解人物微表情、肢体、视线、呼吸与环境互动，生成表演提示词。 | `skills/performer-prompt-engineer` |
| **角色设计** | 基于故事或剧本制作人物小传、定妆照提示词、服化道辅助设计与人物卡。 | `skills/character-designer` |

## 独立发布的动画设计 Skill

**迪士尼动画提示词设计**已单独发布，适用于参考图动画化、角色表演、环境动态、首尾帧过渡与动画镜头设计：

<https://github.com/AgentLiiiiii/design-disney-animation-prompts>

## 如何让 Agent 安装 Skill

1. 复制对应仓库地址。
2. 将地址发送给你的 Agent。
3. 告诉 Agent 你需要的能力，由它先查找合适的 `SKILL.md`，再安装对应 Skill。

### 示例：安装动画设计 Skill

将独立动画 Skill 仓库地址复制给你的 Agent，同时发送指令：

> 请安装这个动画设计 skill，并读取 SKILL.md 后按要求使用。

### 其他示例

> 请在仓库中帮我安装人物表演提示词 skill。

> 请在仓库中帮我安装角色设计 skill。

## 使用边界

- 本仓库用于存放可安装的 Skill；ima 知识库用于存放使用说明、案例和可检索的参考资料。
- 安装前由用户或 Agent 明确发起安装操作；仅提供仓库链接不会自动安装所有 Skill。
- 安装完成后，请以目标 Skill 的 `SKILL.md` 为准进行使用。
