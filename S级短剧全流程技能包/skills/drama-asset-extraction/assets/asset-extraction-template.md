# 生产附件：资产提取清单

项目：
正文版本/canon版本：
大纲版本：
提取日期：
覆盖集数与场次：
未读或缺失材料：
提取状态：planned / drafted / reviewed / revised / delivered

## 0. 提示词与风格约定

| 字段 | 内容 |
|---|---|
| 项目级风格是否已设定 | `yes/no` |
| style_profile | 未设定填 `none`；不得由模型自行补风格 |
| 本体提示词规则 | 人物/场景/道具本体必须写可独立生成的完整 `visual_prompt_safe` |
| 变体提示词规则 | 变体只写 `visual_prompt_delta`，只描述相对继承来源改变的字段 |
| 生成展开规则 | `resolved_prompt = base_prompt + inherited_variants + visual_prompt_delta + optional_style` |
| 风格继承 | 仅当项目级或用户明确设定时继承，否则 `style_directive=none` |

## 1. 资产统计

| 类别 | 本体数 | 视觉变体数 | on_screen | mention_only | reusable_asset | one_off_scene_prop | 不确定项 |
|---|---:|---:|---:|---:|---:|---:|---:|
| 人物 C |  |  |  |  |  |  |  |
| 场景 L |  |  |  |  |  |  |  |
| 道具 P |  |  |  |  |  |  |  |

## 2. 资产索引

| asset_id | category(C/L/P) | canonical_name | aliases | visibility | reuse_class | occurrence_scene_count | first_scene | used_scenes | status |
|---|---|---|---|---|---|---:|---|---|---|

## 3. 人物本体 C

| C编号 | 规范姓名/称谓 | 功能 | 身份锚点 | 稳定外观事实 | visibility | 首次场次 | 复用场次 | canon_description | 完整visual_prompt_safe | style_profile | 证据 |
|---|---|---|---|---|---|---|---|---|---|---|

## 4. 人物视觉变体 C-V

| 变体ID | C本体 | 变体名称 | 故事时间/叙事层 | 触发/退出依据 | 继承来源 | 覆盖字段 | 服装 | 妆容 | 发型/发饰 | 首饰/鞋包 | 身体状态 | visual_prompt_delta（仅改变处） | style_directive | resolved_prompt生成时机 | 使用场次/证据 | 状态 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

## 5. 场景本体与层级 L

| L编号 | 规范名称 | scene_level | parent L | 固定空间/布局 | style_base（未设定填none） | visibility | 首次场次 | 复用场次 | canon_description | 完整visual_prompt_safe | style_profile | 证据 |
|---|---|---|---|---|---|---|---|---|---|---|---|

主场景使用 `scene_level=parent`，子场景使用 `scene_level=child` 并填写父L；只被提及的地点也可登记，但必须标 `mention_only`。

## 6. 场景变体 L-V

| 变体ID | L本体 | 变体名称 | 故事时期 | 昼夜/天气/季节 | 活动布置 | 光线 | 损坏/清理/修复 | 通路/遮挡变化 | 继承来源 | 覆盖字段 | visual_prompt_delta（仅改变处） | style_directive | resolved_prompt生成时机 | 使用场次/证据 | 状态 |
|---|---|---|---|---|---|---|---|---|---|---|

## 7. 可复用道具本体 P

| P编号 | 规范名称 | aliases | 实物身份/材质 | 独有标记 | 功能/线索 | visibility | occurrence_scene_count | 首次场次 | 复用场次 | 所有人 | canon_description | 完整visual_prompt_safe | style_profile | 证据 |
|---|---|---|---|---|---|---|---:|---|---|---|---|---|---|

## 8. 道具视觉变体 P-V

| 变体ID | P本体 | 变体名称 | 完整度/开合/封缄 | 内容/文字/数量 | 污损/湿润/通电等 | 真假/母件关系 | 触发与恢复依据 | 继承来源 | 覆盖字段 | visual_prompt_delta（仅改变处） | style_directive | resolved_prompt生成时机 | 使用场次 | 状态 |
|---|---|---|---|---|---|---|---|---|---|---|

## 9. 逐场一次性道具表（不进入长期P资产库）

| 场次 | 道具临时名 | 可见部分 | visibility | reuse_class | 出现次数 | 持有人/位置 | 进场状态 | 离场状态 | 不入库理由 | 场次证据 |
|---|---|---|---|---|---:|---|---|---|---|---|

此表保留一次性杯、纸袋、普通餐具、临时文件等正文中实际可见但没有跨场复用的物件。即使一次性物件承担线索或身份功能，也标 `narrative_singleton_candidate`，不进入长期P库；只有后续正文在第二个不同场号实际复用，重新提取并登记影响后，才升级为P本体。

## 10. 别名与归并台账

| 原文称呼 | 归并ID | 类型 | 合并/不合并判断 | 依据位置 | 置信度 | 待核动作 |
|---|---|---|---|---|---|---|

## 11. 逐场证据与交接

| scene_id | 故事时间/叙事层 | C进入/离开状态 | L进入/离开状态 | P进入/离开状态 | 一次性道具 | 状态转换/T编号 | 正文位置 | 核对结果 |
|---|---|---|---|---|---|---|---|---|

## 12. 证据与问题

### evidence

| element_id | judgment | episode_scene | observation | action | verification |
|---|---|---|---|---|---|

### canon_delta

| fact_id | before | after | reason | source_scene | affected_artifacts |
|---|---|---|---|---|---|

### open_issues

| id | severity | issue | affected_scope | next_action | status |
|---|---|---|---|---|---|

### next_stage_inputs

- 需要资产版本库合并的C/L/P与V：
- 需要连续性复核的场次、T/N/F：
- 需要AI视觉测试的提示词和关键变体：
- 尚未读取或无法确认的正文/大纲：
