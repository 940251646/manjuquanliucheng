# 资产提取清单

## 用途与门槛

这份清单是资产版本库的前置筛选表。必须在当前季**完整剧本**和与之对应的**完整分集大纲**完成后制作；如果只收到片段、样稿或不完整大纲，只能输出候选项和缺口，`extraction_status` 保持 `candidate_only`，不得把推断写入正式资产库。

```yaml
season_id: S01
canon_version: 1
script_scope: EP001-EP120
outline_scope: EP001-EP120
coverage_match: yes
extraction_status: ready_for_asset_library
style_profile: none # 项目未预设风格时保持 none，不在提示词中自行补风格
```

## 判定口径

### 出现方式

| 值 | 判定 | 处理 |
|---|---|---|
| `visible` | 在画面中实际可见，且需要稳定外观 | 可进入资产候选，按重复和叙事价值决定是否晋级 |
| `visible_reference` | 画面需要指向或依赖其存在，但不需要独立生成资产 | 记录正典事实和场次绑定，通常不建独立资产 |
| `mention_only` | 只在对白、心声、旁白或大纲中被提及，没有可见出镜 | 只进入索引，不生成视觉提示词，不建C/L/P |
| `scene_local_one_off` | 只在一个场次可见；是否承担线索功能另行标记 | 留在逐场道具表，资产库排除；若后续再次出现，重新评估 |

### 晋级门槛

- `occurrence_scene_count` 按**不同场次**计数，同场多次拿起、特写或提及只计一次。
- 道具默认至少出现在 2 个不同场次，并且具备复用、持续状态、持有交接、证据/伏笔或关键镜头价值，才设立 P 本体。
- 一次性道具即使被看见，也只使用逐场局部编号（如 `EP003-S02-local-prop-01`），不创建长期 P 编号。
- 人物和场景只要是正式正文中可见且有制作价值，就建立 C/L 本体；其视觉变化另建 V 变体。
- 一次性道具若后来在第二个不同场号再次出场，必须从 `scene_local_one_off` 晋级为 P 本体，并记录晋级的事实依据；仅承担线索、身份、规则或回收作用但仍只出现一场的物件，保留 `narrative_singleton_candidate` 标记，不得晋级长期P库。

### 视觉变化拆分

任何足以改变参考图、提示词或跨镜头识别的变化，都拆为独立变体：

- 人物：年龄/时期、身份呈现、服装、妆容、发型、发饰、首饰、身体或衣物状态、声音/步态阶段；
- 场景：不同空间、出入口或行动路线建立新 L；同一空间的昼夜、天气、布置、损坏和修复建立 L-V；
- 道具：完整度、开合/封缄、内容/数量、湿污/磨损、激活/熄灭、断裂/修复、真假或复制件。

常规眨眼、短暂表情和不影响识别的瞬时动作不单独建 V。内部组件可以复用，禁止为所有服装、妆容、天气组合制造笛卡尔积。

## 提取总表

| extraction_id | category(C/L/P) | candidate_name | formal_asset_id | first_episode_scene | all_episode_scenes | occurrence_scene_count | appearance_mode | visual_change_evidence | narrative_or_production_function | asset_decision | exclusion_or_promotion_reason | canon_description | visual_prompt_safe（仅本体） | source_evidence |
|---|---|---|---|---|---|---:|---|---|---|---|---|---|---|---|
| X001 | C/L/P |  |  |  |  | 0 | visible / visible_reference / mention_only / scene_local_one_off |  |  | promote / scene_only / index_only / pending |  |  |  |  |

`canon_description` 是忠实的剧情事实，包含身份、外观、路线、归属、线索特征和状态。本体 `visual_prompt_safe` 是可独立使用的完整视觉提示词，导入制作版本库后映射为本体 `safe_prompt`；变体 `visual_prompt_delta` 映射为 `prompt_delta`，不得覆盖本体提示词。提示词不能删除或改变正典事实，也不能把 `mention_only` 或 `scene_local_one_off` 伪装成长期资产。

## 本体完整提示词登记

每个晋级的 C/L/P 本体单独写完整视觉提示词，包含生成该本体必需的稳定识别特征；缺乏正文证据的属性标 `待核`，不虚构。人物需核对脸部、体态、基础服装妆发；场景需核对固定布局和出入口；道具需核对材质、形状和独有标记。风格仅引用已锁定的项目设定。

| 本体ID | C/L/P | canon_description | 完整visual_prompt_safe | style_profile（未设定填none） | 正文证据 | 缺失待核字段 |
|---|---|---|---|---|---|---|

## 人物变体登记

| character_id | variant_id | 变体名称 | 年龄/时期 | 服装 | 妆容 | 发型 | 发饰/首饰及佩戴侧 | 身体/衣物状态 | 声音/动作差异 | 触发与退出集场 | 继承来源 | 覆盖字段 | canon_description | visual_prompt_delta（仅改变处） | style_directive | 证据 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

## 场景本体与变体登记

| L本体 | scene_level | parent_L | 固定布局/出入口/路线 | canon_description | 完整visual_prompt_safe | style_profile | 使用集场/证据 |
|---|---|---|---|---|---|---|---|

| L-V变体 | L本体 | 继承来源 | 覆盖字段 | 昼夜/天气/布置/损坏/修复变化 | canon_description | visual_prompt_delta（仅改变处） | style_directive | 使用集场/证据 |
|---|---|---|---|---|---|---|---|---|

## 道具候选与排除登记

| prop_candidate | appearance_mode | occurrence_scene_count | first_scene | later_scenes | 持有人/位置变化 | 状态变化 | 是否承担线索或复用 | asset_decision | local_scene_id_or_P_id | canon_description | 完整visual_prompt_safe（仅晋级P本体） | 依据 |
|---|---|---:|---|---|---|---|---|---|---|---|---|---|

| P-V变体 | P本体 | 继承来源 | 覆盖字段 | 可见状态变化 | canon_description | visual_prompt_delta（仅改变处） | style_directive | 使用集场/证据 |
|---|---|---|---|---|---|---|---|---|

### 单场道具登记（长期资产库排除）

| 场号/局部编号 | 名称及可见部分 | 持有人/位置 | 进入→离开状态 | 线索功能（若有） | 正文/镜头证据 | 不建P理由 |
|---|---|---|---|---|---|---|

所有变体都填写明确继承来源、覆盖字段和差量；未变化的本体内容不重复。镜头或生成前才按本体完整提示词、变体继承链和已设定的可选风格临时展开 `resolved_prompt`，不将展开文本反写为变体。未设定风格时 `style_directive=none`。

## 版本库晋级清单

| 正式ID | 类型 | 从清单条目 | 晋级时间 | 首次集场 | 复用集场 | 建立的V数量 | 版本库已写 | 逐场绑定已写 | 连续性复核 |
|---|---|---|---|---|---|---:|---|---|---|

## 提取交接

- `evidence`：`extraction_id | judgment | episode_scene | observation | action | verification`
- `canon_delta`：记录晋级、排除、名称合并、L 本体与 L-V 选择；无变更写 `[]`。
- `open_issues`：缺集、缺大纲、视觉变化证据不足、持有人不明、提示词待核对等。
- `next_stage_inputs`：进入版本库和逐场绑定真正需要的完整事实、场次和资产 ID。
