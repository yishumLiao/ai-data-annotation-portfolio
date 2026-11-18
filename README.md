# AI 数据标注与评测作品集

> 面向大模型训练数据生产与质量评估的实战作品集：覆盖 SFT 数据编写、RLHF 偏好标注、回复质量多维评估、Benchmark 出题、badcase 归因与标注质检全流程，与本人 5 年 AI 数据行业工作内容一一对应。

**作者**：廖壹顺（大模型评测 / AI 训练与训练数据方向）
**联系**：ysliao666@gmail.com

## 目录结构

```text
.
├── sft/                          # SFT 指令与多轮对话数据
│   ├── write_guidelines.md       # 编写规范（字段定义、质量红线、自检清单）
│   └── sft_samples.jsonl         # 20 条样例数据（含多轮、安全边界、时效边界）
├── rlhf/                         # RLHF 偏好标注
│   ├── preference_guidelines.md  # 偏好标注规范（维度定义、标尺、偏差控制）
│   └── preference_samples.jsonl  # 10 组标注样例（含逐维度归因）
├── eval/                         # 回复质量评估
│   ├── eval_rubric.md            # 评估量表（5 维 × 4 档行为锚定 + 一票否决）
│   └── evaluation_samples.jsonl  # 8 条评估样例（带原文依据引用）
├── benchmark/                    # Benchmark 出题
│   └── benchmark_questions.jsonl # 8 道专家级题目（考察点、参考答案、评分点、常见错误）
├── badcase/                      # badcase 体系
│   └── badcase_taxonomy.md       # 分类树 + 案例归因 + 预防措施
└── qa-sop/                       # 标注与质检
    ├── annotation_sop.md         # 标注 SOP（流程、一致性阈值、变更管理）
    └── qc_checklist.md           # 质检逐项核对清单
```

## 亮点

- **全链路**：写数据 → 标偏好 → 评质量 → 出题 → 质检，每个环节都有可执行规范，而不是只有数据。
- **每条数据带质检信息**：SFT 自检字段、偏好逐维度归因、评估带原文依据引用，可回溯、可仲裁。
- **规范可复现**：所有量表使用行为锚定（每档分数对应可观察行为），两名标注员按同一规范可得到一致结果。
- **偏差控制机制**：位置偏差（AB 交换复评）、双人背靠背抽检 + Kappa ≥ 0.75、冲突仲裁、规范版本管理。

## 数据统计

| 模块 | 文件 | 条数 |
|---|---|---|
| SFT 指令/多轮数据 | sft/sft_samples.jsonl | 20 |
| RLHF 偏好标注 | rlhf/preference_samples.jsonl | 10 |
| 回复质量评估 | eval/evaluation_samples.jsonl | 8 |
| Benchmark 题目 | benchmark/benchmark_questions.jsonl | 8 |

> 说明：以上数据均为本人原创样例，用于展示方法论与质量标准；生产环境中同结构数据按客户保密要求脱敏或不出域。

## 使用方式

- 标注培训：`sft/write_guidelines.md` + `qa-sop/annotation_sop.md` 可直接作为新人培训教材。
- 规范评审：`eval/eval_rubric.md` 的锚定写法可作为团队评分细则的模板。
- 数据验收：`qa-sop/qc_checklist.md` 逐项核对，可直接用于交付前自检。

## 版本

- v1.0（2026-11-18）：首版，含 SFT / RLHF / 评估 / Benchmark / badcase / SOP 六大模块。
