# 参考材料分析卡

## 项目接入

```yaml
reference_rebuild:
  enabled: true
  reference_phase: deep_read
  reference_read_scope: full_text
  reference_ids: [SRC01]
  candidate_count: 6
  selected_direction_id: ""
```

字段写入 `project.json.reference_rebuild`；来源记录保存在 `reference/`。

## source_manifest（每份来源一张）

```yaml
source_id: SRC01
title: ""
version: ""
material_type: full_script|outline|excerpt|oral_summary
rights_status: user_owned|public_domain|mechanism_study|pending
received_at: ""
scope: ""
episode_count_claimed: null
episode_count_read: 0
scene_count_claimed: null
scene_count_read: 0
missing_sections: []
confidence: low|medium|high
```

## 深读覆盖

| 来源 | 已读集场 | 缺失范围 | 每集功能表 | 阶段复盘 | 结局兑现检查 | 证据位置 |
|---|---|---|---|---|---|---|
| SRC01 |  |  | pending | pending | pending |  |

## 功能机制矩阵

| 来源集场 | 开场异常 | 30秒站队/好奇 | 90秒主动动作 | 本集目标/阻力 | 信息差 | 局势变化/回报 | 集尾问题 | 时间依据 |
|---|---|---|---|---|---|---|---|---|
| SRC01-EP001-S01 |  |  |  |  |  |  |  | actual/estimated/unknown |

## 禁带表达清单

| 类别 | 来源证据 | 识别点摘要 | 新作独立实现 | 新因果 | 复核状态 |
|---|---|---|---|---|---|
| 姓名/关系 |  |  |  |  | open |
| 事件/独特排列 |  |  |  |  | open |
| 场景/道具/规则 |  |  |  |  | open |
| 台词/心声/声纹 |  |  |  |  | open |
| 结局/反转依据 |  |  |  |  | open |

## 多来源机制交叉表（两份及以上）

| 机制编号 | 来源集合 | 抽象功能 | 禁带表达 | 新作实现 | 新因果证据 |
|---|---|---|---|---|---|
| MECH01 | SRC01/SRC02 |  |  |  |  |

单来源使用独立新机制，不虚构第二来源。交叉表只带抽象功能；方向用 [选择模板](direction-selection-template.md)，评分用 [报告模板](originality-report-template.md)。
