---
name: character-designer
description: 根据完整故事、故事大纲、剧本或分场剧本完成三阶段人物设计：第一阶段读取资料、盘点角色、确认角色级别并撰写人物小传，人物小传完成后必须保存为独立Markdown文档；第二阶段基于已确认人物小传输出横版4:3演员定妆照提示词，并可按用户指定物件制作服化道辅助设计；第三阶段基于最终人物模板和已确认辅助参考图输出横版4:3人物卡提示词。触发条件：用户提到“角色设计”“人物小传”“人物设定”“角色设定”“定妆照”“服化道设计”“人物卡”“角色三视图”“角色设计表”，或提供剧本人物描述要求生成角色资料。
---

# Character Designer

角色设计引擎。目标是把剧本和故事资料中的人物，按阶段变成可确认、可生图、可复用的角色设计资产。

## 总流程

严格按三阶段推进，不跨阶段自动输出：

1. 资料读取、角色盘点、人物小传
2. 演员定妆照，可选服化道辅助设计
3. 人物卡

第一阶段没有确认，不进入第二阶段。第二阶段没有确认最终人物模板，不进入第三阶段。

## 阶段一：资料读取与人物小传

### 1.1 读取资料

开始时先询问用户是否有完整故事、故事大纲、故事梗概、剧本或分场剧本，并请用户提供文件、文件夹路径或可读取位置。

读取范围包括：

- 完整故事
- 故事大纲或梗概
- 剧本或分场剧本
- 人物资料
- 版本修订说明
- 与角色直接相关的美术、道具、动作和表演资料

多版本并存时，优先使用用户指定版本；未指定时依据定稿标记、版本号和修改时间判断。发现冲突时列出冲突，不自行合并。

未提供完整故事或剧本时，先请用户补充资料；不得只凭一句角色描述直接进入定妆照或人物卡。

### 1.2 角色盘点与级别确认

读取资料后，先输出角色盘点，列出：

- 角色或群众群体名称
- 出场场次或出现位置
- 剧情功能
- 建议级别：主角、配角、群众演员

必须让用户确认主角、配角、群众演员的最终划分。未经确认，不写人物小传。

一次最多提出3个聚焦确认问题。

### 1.3 人物小传

角色级别确认后，先写主角，再写配角。群众演员不写个人小传，只写群体风格描述。

每位主角或配角固定使用以下格式：

```markdown
## [角色名]人物小传

### 背景故事

[基于完整故事、剧本与已确认资料撰写；资料不足时标注“未提及/待确认”。]

| 项目 | 内容 |
|------|------|
| 姓名 | |
| 年龄 | |
| 性别 | |
| 身份 | |
| 外貌特征 | |
| 语言风格 | |
| 动作习惯 | |
| 特殊技能 | |
| 服装风格 | |
| 关键道具 | |
| 性格标签 | |
```

规则：

- 背景故事必须放在表格前，单独成块。
- 所有信息必须来自已读取资料或用户确认。
- 不确定内容写“未提及/待确认”，不得猜测年龄、体型、能力边界、口音或服装细节。
- 群众演员只按群体描述身份范围、年龄层、服装共同点、色彩材质、行为状态和与主配角的视觉区分；不得虚构姓名、个人背景或个人道具。

### 1.4 人物小传文档

人物小传写完后，必须保存为独立Markdown文档文件；不得只在对话框里给完整结果。

文档要求：

- 默认保存到当前工作区 `outputs/character-design/`。
- 若项目已有明确输出目录，使用项目输出目录。
- 文件名使用项目名或故事名加阶段说明，例如 `角色设计-人物小传.md`；无法确定项目名时使用 `character-biographies.md`。
- 文档内容包含资料依据、角色盘点、主配角人物小传、群众演员风格描述。
- 对话中只给摘要、待确认问题和文档路径，不重复粘贴完整文档。
- 用户要求修改人物小传时，更新文档文件后再继续。

只有用户确认人物小传无需继续修改，且文档文件已生成，才能进入第二阶段。

## 阶段二：演员定妆照

第二阶段只基于已确认人物小传和已生成的人物小传文档设计演员定妆照。

### 2.1 定妆照规格

演员定妆照固定为单张横版 `4:3` 图片，包含左右两个独立画面：

- 左侧：正面胸部以上近景，清楚看见脸部特征、发型、妆容、肤色、眼神和颈肩关系。
- 右侧：同一人物正面全身，从头顶到脚底，清楚看见体态、服装比例、鞋履和关键道具。

左右两侧必须是同一人物，保持完全相同的脸型、五官、发型、妆容、体型、服装、颜色、材质和道具。

定妆照只用于确认真人化基础造型。不得加入侧面、背面、表情板、服装细节板、道具板、三视图或人物卡。

### 2.2 定妆照提示词规则

首次设计、用户提出修改、用户要求更新时，必须先完整输出中英文定妆照提示词。不得只给修改摘要，也不得直接询问是否生图。

提示词规则：

- 中文以“人物定妆照”开头。
- 英文以“Character look-reference photo”开头。
- 提示词只描述画面可见的脸部、发型、妆容、体态、服装、材质、道具、姿势、背景和负面约束。
- 不写角色姓名、剧情名称、人物小传、资料来源或不可见技能。
- 不在提示词文本中写 `--ar` 或平台参数；比例作为输出规格说明。
- 描述必须自足，图像模型不读剧本也能生成该角色造型。

英文模板：

```text
Character look-reference photo, two clearly separated side-by-side panels. LEFT PANEL: [front-view chest-up close portrait with visible facial features, hairstyle, makeup, skin tone, eyes, neck, and shoulders]. RIGHT PANEL: [the same person's front-view full-body portrait with visible body proportions, costume, footwear, and props].
The left and right panels must show the exact same person, with identical face, facial structure, hairstyle, makeup, body proportions, costume layers, colors, materials, textures, and props. Live-action character look-reference photography, clean neutral studio or grid-paper background. No side view, no back view, no expression sheet, no costume-and-prop support card, no extra person, no alternate design, no text, no watermark.
```

中文模板：

```text
人物定妆照，左右分成两个清晰独立的画面。左侧画面：[正面胸部以上近景的可见外貌、发型、妆容、肤色、眼神与颈肩细节]；右侧画面：[同一人物正面全身的体态、服装、鞋履与可见道具细节]。
左侧画面：正面胸部以上近景，清楚看见脸部特征、发型、妆容、肤色、眼神和颈肩关系；右侧画面：正面全身，从头顶完整显示到脚底，清楚看见整体体态、服装比例、衣摆、鞋子和关键道具。
左右两个画面必须是同一人物，脸型五官、发型、妆容、体型、服装层次、颜色、材质、纹理和道具完全一致。真人影视人物定妆照，干净摄影棚或网格背景。禁止生成侧面、背面、表情板、服装道具辅助卡、额外人物或替代造型。
```

### 2.3 生图规则

如果具备图像生成能力，在完整中英文提示词后固定询问：

`检测到有生图技能，是否使用生图生成这张定妆照？`

只有用户明确同意后，才调用图像生成工具。用户没有明确选择时，默认只输出提示词。

用户确认定妆照后，该图标记为“已确认演员定妆照”。

### 2.4 可选服化道辅助设计

用户确认演员定妆照后，进入第三阶段前必须询问：

`是否需要出人物服化道的辅助设计？如需要，请指定要单独设计的装饰物、服装局部或关键道具。`

规则：

- 用户不需要：原演员定妆照标记为“最终人物模板”，进入第三阶段。
- 用户需要：一次只处理用户指定的一项服化道资产，例如发簪、冠帽、手帕、腰封、鞋履、首饰或关键道具。
- 每项辅助设计先输出完整中英文图生图提示词，以已确认演员定妆照为基础参考。
- 每项辅助设计生成或提示词交付后，必须让用户确认。
- 未获明确通过，不得标记为参考图，不得进入下一物件定稿，不得进入第三阶段。
- 所有指定物件确认后，必须基于已确认演员定妆照和全部已确认辅助图，重装一张更新版人物定妆照。
- 更新版人物定妆照仍为横版 `4:3` 左右双画面。用户确认后标记为“最终人物模板”。
- 重装不得更换人物脸、体态、发型、妆容或基础服装关系；只替换或补全用户确认的物件结构、材质、比例和佩戴位置。

## 阶段三：人物卡

只有确认“最终人物模板”后，才能进入第三阶段。

### 3.1 人物卡规格

人物卡固定为单张横版 `4:3` 图片，只允许6个面板。

顶部3格：胸部以上头部三视图。

- 正面
- 左侧面
- 背面

底部3格：去头身体三视图。

- 正面
- 左侧面
- 背面

禁止加入：

- 表情图
- 剧情状态图
- 配色板
- 色号
- 信息条
- 道具细节板
- 服装细节板
- 额外人物
- 额外面板

### 3.2 人物卡继承规则

人物卡必须使用最终人物模板作为主参考。若存在已确认服化道辅助图，必须一并作为多图参考。

必须继承：

- 脸型
- 五官比例
- 眼型
- 肤色
- 发型和发色
- 妆容
- 体态
- 服装母版
- 色彩关系
- 标志性物件
- 已确认辅助物件的结构、材质、比例和佩戴位置

不得因三视图、裁切、模块化排版或模型随机性而换脸、换发、换装或替换道具。

### 3.3 人物卡提示词规则

第三阶段只输出人物卡的一套中英文多图图生图提示词。首次制作、用户修改人物卡或用户要求更新时，必须先完整输出中英文提示词，再询问是否生图。

英文模板：

```text
Image-to-image character card. Use the approved final character template and all approved costume/prop reference images as multi-image visual references. Preserve the exact approved face, facial structure, body proportions, hairstyle, makeup, costume identity, colors, materials, textures, props, and accessory shapes. No redesign, no face swap, no alternate hairstyle, no alternate outfit, no replacement prop.
One single horizontal 4:3 image, clean grid-paper background, exactly six equal panels and nothing else.
TOP ROW: exactly three chest-up head turnarounds in a 1x3 grid, strictly FRONT / LEFT PROFILE / BACK. The third panel must be a true rear head view showing the back of the head, back hair, nape, and rear accessory relationship.
BOTTOM ROW: exactly three headless body turnarounds in a 1x3 grid, strictly FRONT / LEFT SIDE / BACK. Show only from the neck down to the footwear, directly inheriting body proportions, costume layers, footwear, props, and approved accessory details from the final character template and approved references.
Absolutely no head, face, hair, makeup or headwear in the bottom row. No expression panel, no narrative-state panel, no color palette, no HEX codes, no info strip, no prop board, no costume-detail board, no extra panel, no readable text. Live-action film character design reference.
```

中文模板：

```text
图生图人物卡。必须将已确认的最终人物模板与全部已确认服化道辅助设计图作为多图视觉参考输入。严格继承已确认的脸型、五官比例、体态、发型、妆容、服装身份、颜色、材质、纹理、道具和饰品结构。禁止重新设计、换脸、改变发型、换装、替换饰品、改变道具形状或材质。
单张横版4:3人物卡，干净网格背景，画面必须且只能有6个等大面板。
顶部：3张胸部以上头部三视图，组成1×3网格，严格为正面／左侧面／背面。第三格必须是完整后脑、后发、颈后和背面饰品关系。
底部：3个去头身体三视图，组成1×3网格，严格为正面／左侧面／背面。每格只从颈部以下显示到鞋履，原样继承最终人物模板的身体比例、服装层次、鞋履、道具和已确认饰品细节。
底部绝对禁止头部、面部、头发、妆容和头饰。禁止表情图、剧情状态图、配色板、色号、信息条、文字、道具细节板、服装细节板、额外人物或额外面板。真人影视角色设计参考。
```

### 3.4 生图规则

如果具备图像生成能力，在完整人物卡提示词后固定询问：

`检测到有生图技能，是否使用生图生成人物卡？`

只有用户明确同意后，才调用图像生成工具。用户没有明确选择时，默认只输出提示词。

## 风格与时代适配

根据剧本风格，为提示词添加不超过5个风格关键词：

| 风格 | 关键词 |
|------|--------|
| 写实/现代 | photorealistic, cinematic, natural lighting |
| 赛博朋克 | cyberpunk, neon lights, futuristic, holographic |
| 卡通/3D | 3D Pixar style, stylized, toon shading |
| 复古/怀旧 | retro, vintage film grain, analog, 1980s |
| 黑色幽默 | gritty, muted tones, noir lighting, exaggerated features |
| 科幻 | sci-fi, high-tech, sleek, metallic textures |

## 输出规则

- 阶段结果分别交付，不跨阶段自动推进。
- 第一阶段人物小传完成后，必须保存为独立Markdown文档，并在对话中提供文档路径。
- 第二阶段只交付演员定妆照提示词或经用户同意生成定妆照，不输出人物卡。
- 第二阶段可选服化道辅助设计只处理用户指定物件，不批量扩展。
- 第三阶段只交付横版 `4:3` 六格人物卡提示词或经用户同意生成人物卡。
- 图生图提示词必须依赖已确认演员定妆照、最终人物模板和已确认辅助参考图实现一致性锁定。
- 角色姓名或资产名称只能作为交付标题，不得替代参考图约束。
- 所有量化信息和行为信息必须可追溯到剧本、故事大纲、人物小传或用户确认；无依据时标注“未提及/待确认”或“不适用”。

## 注意事项

- 如果剧本中有多个角色，逐一处理，不合并。
- 每个角色的人物小传和资产提示词独立输出。
- 不得把未确认的服装、化妆、特殊技能、道具功能或身材数据写成定稿。
- 避免抽象情绪词，改用具体视觉描述，例如“低垂的眼角”“紧抿的嘴唇”。
- 风格关键词不要堆砌，每套提示词不超过5个风格词。

