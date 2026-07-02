# AI 图像生成模型特性与提示词规则参考

本文档收录四大主流图像生成模型的特性差异、提示词结构偏好和最佳实践。
当用户选择目标模型后，根据对应章节的规则生成适配提示词。

---

## 1. Nano Banana（Gemini 2.5 Flash Image）

### 模型定位
初代 Nano Banana 模型，基于 Gemini 2.5 Flash 的原生多模态架构。1K 分辨率，价格最低。

### 核心特性
- **分辨率**: 1K（最大 1024×1024）
- **价格**: $0.039/张
- **编辑能力**: 支持图+文编辑、多图合成、风格迁移
- **参考图**: 最多 14 张
- **迭代式优化**: 支持多轮对话逐步调整

### 提示词核心原则
1. **描述场景，而非罗列关键词** — 该模型的核心优势在于深度语言理解，叙述性段落优于关键词堆砌
2. **重要细节放前面** — 模型对提示词前部内容权重更高
3. **使用语义化正向描述** — 不说"不要汽车"，而是说"一条空旷的街道，没有任何交通迹象"
4. **迭代优化** — 先短后长，一次只改一两个变量

### 提示词结构模板

**文生图（从零生成）**:
```
Subject (数量/特征) + Action/关系 + Setting (地点/时间/天气) + Style/媒介 + Composition/镜头 + Lighting/色调 + 关键细节 + Constraints (避免什么)
```

**图编辑（基于已有图片）**:
```
Keep (不变的部分) + Change (修改什么) + How (风格/力度/方向) + Constraints (避免副作用)
```

### 反推提示词适配要点
- 反推出的提示词应写成连贯的叙述性描述，而非逗号分隔的关键词列表
- 需明确包含构图/镜头描述（如 35mm、中景、特写等）
- 光线和色调描述应具体而非笼统（如"柔和黄金时刻光线"而非"好看的光"）
- Constraints 部分简短明确（如"no text, no watermark, no extra people"）

---

## 2. Nano Banana 2（Gemini 3.1 Flash Image）

### 模型定位
2026 年 2 月发布的升级版，功能与成本最佳平衡，**新项目首选**。

### 核心特性
- **分辨率**: 1K–4K（4K 价格 $0.151/张，1K 价格 $0.045/张）
- **文本渲染**: 比 Nano Banana 更强，适合信息图、海报等含文字场景
- **参考图**: 最多 14 张
- **思考模式**: 支持 `minimal`（简单场景）和 `high`（复杂场景、文字渲染、多元素交互）
- **对话编辑**: 支持多轮迭代优化

### 提示词核心原则
1. **继承 Nano Banana 所有原则** — 叙述性描述、重要细节前置、语义化正向约束
2. **善用思考模式** — 复杂场景时建议开启 `high` 思考模式
3. **4K 分辨率** — 需要高清输出时指定分辨率要求
4. **文本渲染优势** — 清楚说明文字内容、字体风格和整体设计

### 提示词结构模板
与 Nano Banana 相同的叙述性结构，但可附加：
- **分辨率指定**: 如"4K high resolution output"
- **思考模式建议**: 如"For complex scenes, recommend enabling high thinking mode"
- **文字设计**: 如"Include text 'XXX' in clean, bold sans-serif font"

### 文字渲染提示词模板
```
为 [品牌/概念] 创建一个 [图像类型]，其中包含文本「[要渲染的文本]」，字体为 [字体风格]。设计应为 [风格描述]，配色方案为 [配色方案]。
```

### 反推提示词适配要点
- 如果参考图含文字元素，应明确描述文字内容和风格
- 复杂构图时提示词需更详细，建议标注"建议开启思考模式"
- 需要高分辨率时可指定 4K
- 保持叙述性风格，但可以更精细地描述每个视觉元素

---

## 3. Nano Banana Pro（Gemini 3 Pro Image）

### 模型定位
最高画质输出，最精确的提示词遵循，适合高质量出版和品牌视觉。

### 核心特性
- **分辨率**: 1K、2K、4K 原生支持
- **价格**: $0.134+/张（1K），4K 更高
- **专业文本渲染**: 信息图、菜单、图表、营销资产的清晰文字
- **8 图多重融合**: 混合最多 8 张参考图（API 最多 14 张）
- **AI 思考模式**: 推理复杂提示，生成中间"思考图像"
- **网络搜索接地**: 基于 Google 搜索实时数据验证事实
- **5 人一致性**: 无限次生成中保持最多 5 个不同人物的面部相似性
- **专业相机控制**: 相机角度、场景光照、景深、焦点和色彩分级
- **最高提示词遵循度**: 最精确地按照用户描述生成

### 提示词核心原则
1. **叙述性描述 + 专业控制参数** — 不仅描述场景，还要指定专业摄影参数
2. **相机语言** — 明确镜头类型、角度、景深（如 85mm portrait lens、shallow depth of field）
3. **光照系统** — 三点柔光箱、黄金时刻、霓虹背光等具体布光描述
4. **色彩分级** — 指定色调倾向（cool palette、warm tones、cinematic grading）
5. **分辨率指定** — 可明确指定 1K/2K/4K 输出
6. **思考模式** — 复杂场景务必开启 `high` 思考模式

### 提示词结构模板

**文生图**:
```
[主体描述] + [动作/关系] + [场景设置] + [风格/媒介] + [相机参数: 镜头/角度/景深] + [光照系统: 类型/方向/氛围] + [色彩分级] + [分辨率] + [Constraints]
```

**图编辑**:
```
Keep (精确锁定: 面部特征/姿势/构图/光线方向) + Change (修改什么/位置/力度) + Match (匹配原始光线/透视/色彩分级) + Resolution + Constraints
```

### 专业控制参数词汇表

**相机**:
- 镜头: 35mm wide-angle, 85mm portrait, macro, telephoto
- 角度: low-angle, eye-level, elevated 45°, bird's-eye, Dutch angle
- 景深: shallow depth of field (bokeh), deep focus, selective focus
- 拍摄类型: close-up, medium shot, wide shot, establishing shot

**光照**:
- 三点柔光箱: three-point softbox setup
- 黄金时刻: golden hour, warm directional light
- 霓虹: neon backlight, mixed fluorescent and neon
- 电影: cinematic lighting, volumetric light, ray-traced reflections
- 漫射: soft diffused light, overcast ambient

**色彩**:
- 冷色调: cool color palette, blue-tinted grading
- 暖色调: warm tones, golden grading
- 高对比: high contrast, dramatic color grading
- 胶片感: film grain, nostalgic color grading, faded tones

### 反推提示词适配要点
- 反推出的提示词必须包含专业相机和光照参数
- 如果参考图有精细材质，需详细描述（如"detailed skin texture, visible pores"而非"realistic skin"）
- 可指定分辨率（4K 推荐）
- 多人场景需标注人物数量和一致性要求
- 文字元素需详细描述内容和字体风格
- 复杂场景建议标注"建议开启思考模式（thinking: high）"

---

## 4. GPT Image 2（OpenAI）

### 模型定位
面向结构化视觉沟通的设计助手，核心优势在于精准文字渲染和指令遵循度。

### 核心特性
- **文字渲染**: 大标题、短标签、海报标题、菜单项等可读性较高
- **结构化版式**: 擅长清晰版式、产品构图、UI mockup、信息图
- **指令遵循度高**: 说明任务和成功标准时更容易保持结构
- **可编辑参考图**: 支持多参考图编辑、换装、换背景、抠图
- **图生视频首帧**: 适合生成后续转视频的第一帧
- **限制**: 极小文字、密集段落可能漂移；精确品牌标志不可靠；复杂透明背景需人工检查

### 提示词核心原则
1. **写成生产 Brief，而非关键词堆砌** — 说明这张图要完成什么任务
2. **先说明任务，再说风格** — 先写输出类型（海报、产品广告、App 界面等）
3. **把文字当作需要锁定的素材** — 文字放进引号，说明如何渲染
4. **给模型一个镜头和版式** — Close-up / Wide shot / Top-down / Left third / Clean grid
5. **编辑任务用三句话** — 改什么 + 锁定什么 + 如何保持物理真实

### 提示词结构模板

**文生图**:
```
Create [type of image] for [use case].
Main subject: [specific subject and visible details].
Exact text, if any: "[copy that must appear]".
Composition: [framing, layout, negative space, subject placement].
Style and lighting: [visual language, medium, mood, light direction].
Constraints: [what must not change, no extra words, no watermark].
Output format: [aspect ratio, transparent background, video-ready frame].
```

**图编辑**:
```
[What to change]: Replace/add/remove [element], [position], [material], [size].
[What to preserve]: Keep [identity, pose, composition, lighting direction, camera angle, visible labels] exactly.
[How to match]: Match [lighting, perspective, shadow direction, color grading] of original.
Constraints: [avoid side effects].
```

### 常见镜头/版式词汇表

| 镜头/版式 | 适用场景 |
|-----------|---------|
| Close-up | 产品纹理、手、脸部、材质、标签 |
| Wide shot | 环境、故事场景、城市海报、视频起始帧 |
| Top-down | 食物、桌面场景、flat-lays、包装 |
| Left third / Right third | 广告布局中文字与产品平衡 |
| Clean grid | UI mockup、角色设定图、图表、信息图 |

### 反推提示词适配要点
- 反推出的提示词必须以"Create [type] for [use case]"开头，明确任务类型
- 主体描述需具体锚定（不能只说"一个女人"，要说"一位25岁亚洲女性，短发，穿白色衬衫"）
- 如有文字元素，必须用引号包裹并说明渲染方式
- 必须包含 Constraints 和 Output format
- 不要使用空泛美学词（如"ultra detailed, masterpiece"），用具体物理描述替代
- 中文文字场景需指定"Simplified Chinese"并限制文字数量和层级

---

## 5. 模型选择速查对比

| 维度 | Nano Banana | Nano Banana 2 | Nano Banana Pro | GPT Image 2 |
|------|------------|---------------|----------------|-------------|
| 提示词风格 | 叙述性描述 | 叙述性描述 | 叙述性+专业参数 | 结构化 Brief |
| 分辨率 | 1K | 1K-4K | 1K-4K | 标准尺寸 |
| 文字渲染 | 基础 | 较强 | 专业级 | 强（短文字） |
| 思考模式 | ❌ | minimal/high | high | ❌ |
| 参考图 | 14张 | 14张 | 8-14张 | 多参考图 |
| 价格 | $0.039 | $0.045-0.151 | $0.134+ | API $30/M tokens |
| 最适合 | 预算编辑 | 通用首选 | 高质量出版 | 结构化视觉 |
| 提示词结构 | Subject→Style→Constraints | 同上+分辨率+文字 | 同上+专业控制 | 任务→主体→约束→输出 |

---

## 6. 反推提示词通用视觉分析维度

无论选择哪个模型，反推提示词时都需从参考图中提取以下维度：

1. **主体**: 谁/什么（人物/物体/场景），数量、特征、材质、形状
2. **动作/姿态**: 正在做什么，如何与其他元素互动
3. **场景/环境**: 地点、时间、天气、室内/室外、城市/自然
4. **风格/媒介**: 照片/插画/3D/水彩/像素，写实程度，艺术方向
5. **构图/镜头**: 特写/中景/远景，角度，画面布局
6. **光线/色调**: 柔光/硬光/背光/霓虹，暖冷对比，胶片感
7. **色彩系统**: 主色调、配色方案、对比度
8. **材质/纹理**: 皮肤纹理、布料质感、金属光泽、木材纹路
9. **文字元素**: 如有文字，描述内容、位置、风格
10. **情绪/氛围**: 宁静/戏剧化/温暖/冷峻/梦幻/幽默
11. **质量/细节**: 细节程度、清晰度、背景复杂度

分析时按优先级排列：主体 > 动作 > 场景 > 风格 > 构图 > 光线 > 色彩 > 材质 > 文字 > 情绪 > 约束
