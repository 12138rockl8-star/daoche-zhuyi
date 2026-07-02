# 提示词反推模板与示例参考

本文档包含各模型的提示词生成模板和完整反推示例。
根据用户选择的目标模型，使用对应的模板生成提示词。

---

## 1. Nano Banana 系列提示词模板

### 1.1 文生图模板（Nano Banana / Nano Banana 2）

```
[主体描述，包含数量、年龄、材质、形状等特征] [动作/与其他元素的关系],
[场景设置：地点、时间、天气、环境].
[风格/媒介：照片/插画/3D等，写实程度].
[构图/镜头：特写/中景/远景，角度，镜头类型].
[光线/色调：光线类型、方向、色调倾向].
[关键细节：纹理、质感、情绪等].
[约束：避免什么].
```

**Nano Banana 2 额外参数（可选）**:
```
Resolution: [1K/2K/4K].
Text (if any): [文字内容] in [字体风格].
Thinking mode recommendation: [minimal/high].
```

### 1.2 图编辑模板（Nano Banana / Nano Banana 2）

```
保持不变：[面部特征、姿势、构图、光线方向等].
修改：[要添加/删除/替换的元素，位置，材质].
匹配：[与原图的光线、透视、色调保持一致].
约束：[避免的副作用].
```

### 1.3 Nano Banana Pro 文生图模板

```
[主体描述] [动作/关系],
[场景设置].
[风格/媒介].
相机：[镜头类型: 35mm/85mm/macro/telephoto], [角度: eye-level/low-angle/elevated], [景深: shallow bokeh/deep focus].
光照：[布光类型: three-point softbox/golden hour/neon/volumetric], [方向: from left/from window/backlit], [氛围: serene/dramatic/cinematic].
色彩分级：[色调: cool palette/warm tones/cinematic grading], [对比度: high contrast/soft contrast].
关键细节：[纹理/材质/情绪].
分辨率：[1K/2K/4K].
思考模式：建议 high（复杂场景）/ minimal（简单场景）.
约束：[避免什么].
```

### 1.4 Nano Banana Pro 图编辑模板

```
精确锁定：[面部特征、发型、服装轮廓、姿势、构图、光线方向、色彩分级].
修改：[具体元素，位置，材质，大小].
匹配原始：[光照系统、透视角度、阴影方向、色彩分级、景深].
分辨率：[1K/2K/4K].
思考模式：建议 high.
约束：[避免副作用].
```

---

## 2. GPT Image 2 提示词模板

### 2.1 文生图模板

```
Create [type of image] for [use case].

Main subject: [specific subject with visible details — age, features, materials, shapes].

Exact text, if any: "[exact copy that must appear]". Render [font style / size / placement rule]. No extra words, no duplicate text.

Composition: [framing / layout / negative space / subject placement — e.g. "centered, wide shot with clear foreground-midground-background layers"].

Style and lighting: [visual language, medium, mood, light direction — e.g. "realistic photography, 35mm, soft golden hour light from the left, warm tones"].

Constraints: [what must not change / no watermark / no extra people / no distorted hands / no fake logo].

Output format: [aspect ratio — e.g. 16:9 / 4:5 / square] / [background — e.g. transparent / clean white / natural environment] / [video-ready: yes/no].
```

### 2.2 图编辑模板

```
[What to change]: Replace/add/remove [specific element], [position in frame], [material/size/description].
[What to preserve]: Keep [list all that must stay identical — face, pose, composition, lighting direction, camera angle, visible labels, color grading] exactly.
[How to match]: Match [lighting style, perspective, shadow direction, color grading, depth of field] of original image.
Constraints: [avoid side effects — no new elements, no color shift, no composition drift].
```

---

## 3. 反推提示词完整示例

### 3.1 示例：一张赛博朋克城市夜景

**视觉分析**:
- 主体：霓虹灯街道，行人稀少
- 场景：未来城市，夜间，雨天
- 风格：赛博朋克，写实摄影
- 构图：广角，街道纵深，低视角
- 光线：霓虹灯背光，体积雾，湿地面反射
- 色彩：冷色调，蓝紫为主，霓虹点缀粉绿
- 氛围：孤独、压抑、科技感

**Nano Banana 版本**:

> 中文：一条雨夜中的赛博朋克城市街道，湿滑路面反射着霓虹灯的蓝紫色光芒，远处高楼间弥漫着体积雾。极少的行人在人行道上行走，霓虹招牌倒映在水洼中。写实摄影风格，广角镜头，低视角拍摄，街道纵深延伸至远处，冷色调以蓝紫为主点缀粉绿霓虹，体积光穿过雾气，电影般氛围。无文字水印，无多余行人。

> English: A cyberpunk city street on a rainy night, wet pavement reflecting neon blue-purple glow, volumetric fog drifting between distant skyscrapers. Few pedestrians walking on sidewalks, neon signs reflecting in puddles. Realistic photography, wide-angle lens, low-angle perspective, street depth extending into distance, cool color palette dominated by blue-purple with pink-green neon accents, volumetric light cutting through fog, cinematic atmosphere. No text, no watermark, no extra pedestrians.

**Nano Banana 2 版本**:

> 中文：一条雨夜中的赛博朋克城市街道，湿滑路面反射着霓虹灯的蓝紫色光芒，远处高楼间弥漫着体积雾。极少的行人在人行道上行走，霓虹招牌倒映在水洼中。写实摄影风格，广角镜头，低视角拍摄，街道纵深延伸至远处，冷色调以蓝紫为主点缀粉绿霓虹，体积光穿过雾气，电影般氛围。4K超高清分辨率。建议开启思考模式（high）。无文字水印，无多余行人。

> English: A cyberpunk city street on a rainy night, wet pavement reflecting neon blue-purple glow, volumetric fog drifting between distant skyscrapers. Few pedestrians walking on sidewalks, neon signs reflecting in puddles. Realistic photography, wide-angle lens, low-angle perspective, street depth extending into distance, cool color palette dominated by blue-purple with pink-green neon accents, volumetric light cutting through fog, cinematic atmosphere. 4K ultra high resolution. Recommend high thinking mode. No text, no watermark, no extra pedestrians.

**Nano Banana Pro 版本**:

> 中文：一条雨夜中的赛博朋克城市街道，湿滑路面反射着霓虹灯的蓝紫色光芒，远处高楼间弥漫着体积雾。极少的行人在人行道上行走，霓虹招牌倒映在水洼中。写实摄影风格。相机：广角镜头 35mm，低视角拍摄，深景深。光照：霓虹背光与体积雾混合，从招牌和店面散射，电影级体积光效。色彩分级：冷色调以蓝紫为主，霓虹点缀粉绿与橙色，高对比度电影级色彩分级。4K超高清输出。思考模式：high。无文字水印，无多余行人，无变形肢体。

> English: A cyberpunk city street on a rainy night, wet pavement reflecting neon blue-purple glow, volumetric fog drifting between distant skyscrapers. Few pedestrians walking on sidewalks, neon signs reflecting in puddles. Realistic photography. Camera: wide-angle 35mm lens, low-angle perspective, deep focus. Lighting: mixed neon backlight and volumetric fog, scattering from signs and storefronts, cinematic volumetric lighting effects. Color grading: cool palette dominated by blue-purple, neon accents in pink-green and orange, high contrast cinematic color grading. 4K ultra high resolution output. Thinking mode: high. No text, no watermark, no extra pedestrians, no deformed limbs.

**GPT Image 2 版本**:

> 中文：为赛博朋克概念艺术创建一张写实城市夜景图。
主体：一条雨夜中的赛博朋克街道，湿滑路面反射霓虹蓝紫光芒，远处高楼间弥漫体积雾，极少行人在人行道上行走。
构图：广角纵深构图，低视角，街道延伸至远处，前景为水洼倒影，中景为霓虹店面，背景为雾中高楼。
风格与光线：写实摄影风格，霓虹背光与体积雾混合照明，冷色调蓝紫为主点缀粉绿霓虹，电影级氛围。
约束：无文字水印，无多余行人，无变形肢体，无低质量模糊。
输出格式：16:9 横版，自然夜景背景。

> English: Create a realistic cyberpunk city night scene for concept art.
Main subject: a cyberpunk street on a rainy night, wet pavement reflecting neon blue-purple glow, volumetric fog between distant skyscrapers, few pedestrians on sidewalks.
Composition: wide-angle depth composition, low-angle perspective, street extending into distance, foreground puddle reflections, midground neon storefronts, background fog-shrouded towers.
Style and lighting: realistic photography, mixed neon backlight and volumetric fog illumination, cool palette dominated by blue-purple with pink-green neon accents, cinematic atmosphere.
Constraints: no text, no watermark, no extra pedestrians, no deformed limbs, no low-quality blur.
Output format: 16:9 landscape, natural night environment.

---

## 4. 增加元素时的提示词扩写规则

当用户要求在原图基础上增加元素时，按以下规则扩写提示词：

### Nano Banana 系列（叙述性扩写）
将新元素自然融入叙述中，保持场景连贯性：

```
原叙述 + [新元素的描述：位置、材质、大小、与现有元素的互动关系]
```

示例（在赛博朋克街道增加一架飞行器）：
> "远处高楼间一架银色飞行器掠过，尾部蓝色推进光芒划破雾气"

### GPT Image 2（结构化扩写）
在 Main subject 或 Composition 中明确增加新元素：

```
Main subject: [原描述] + [新元素: 位置, 特征, 与主体的关系]
Composition: [原构图] + [新元素占据的画面位置]
```

示例（在赛博朋克街道增加一架飞行器）：
> "Main subject: ... A silver aircraft flying between distant towers, blue thrust glow cutting through fog."
> "Composition: ... aircraft positioned in upper third of frame."

---

## 5. 双语输出格式标准

最终提示词输出统一使用以下格式：

```
## 🎯 目标模型: [模型名称]

### 🇨🇳 中文提示词

[完整的中文提示词]

### 🇬🇧 English Prompt

[完整的英文提示词]

---

💡 **模型使用建议**:
- [模型特有的使用提示，如思考模式建议、分辨率建议等]
- [该提示词的核心优势说明]
- [迭代优化建议]
```
