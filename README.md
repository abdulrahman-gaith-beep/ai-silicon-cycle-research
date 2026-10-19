# AI 定制硅片研究库（AI Custom-Silicon Research）

> 一站式研究仓库：AI 加速器/定制硅片（XPU）产业的深度研究报告 + 事实台账（K-register）+ 可复用研究技能（cycle-window-research）。
> 研究截止：**2026-10-19** · 方法论灵感：《Forty-Two Years of Inference Silicon》

## 仓库结构

```
├── README.md
├── reports/
│   ├── AI定制硅片产业深度研究.md      # 主报告（十一章 + 情景框架 + 触发器台账）
│   └── assets/                        # 六幅配套图表（fig1–fig6，见发布包）
├── data/
│   └── fact-register.md               # K1–K50 事实台账：报告每个关键数字的出处与口径
└── skills/
    └── cycle-window-research/         # 可复用研究技能（周期窗口研究法）
        ├── SKILL.md                   # 七步工作流 + 不可违反的纪律
        └── references/
            ├── methodology.md         # 窗口切分/K-register/类比矩阵/情景算术模式
            └── presentation.md        # 编辑级数据呈现规范（墙图/触发器卡片/图表语法）
```

## 主报告速览

《AI 定制硅片产业深度研究：从 GPU 霸权到 XPU 时代》覆盖：

- **需求侧**：四大云厂商 2026 年 ≈$725B 资本开支指引（+77%）；应用层收入交叉验证（OpenAI ≈$50B 年化口径更正事件）
- **商用 GPU**：NVIDIA Q2FY27 数据中心 $89.0B（+117%）；AMD Helios/MI450 与 OpenAI 6GW 协议
- **自研 XPU**：Google TPU v8（Sunfish/Zebrafish 双芯分治）、AWS Trainium3/4、微软 Maia 200/300、Meta MTIA、OpenAI Jalapeño
- **ASIC 设计服务链**：Broadcom（FY26 AI 收入 ≈$58B）、Marvell、MediaTek（2028 目标 26% 份额）、世芯/创意
- **供给四闸门**：HBM（2026 ≈$54.6B，售罄）、先进制程、CoWoS（月产能 →130kwpm）、互联（NVLink Fusion vs UALink vs 以太网）
- **终极约束**：电网并网队列（ERCOT 438GW+、热点区域 4–7 年）
- **中国**：出口管制双向化、华为昇腾路线图、寒武纪万亿市值
- **清算文法**：Groq $20B 授权 vs Cerebras IPO——创业硅片的退出光谱
- **情景框架**：基准 ≈2.5× vs 收缩 −15%~−35%，8 个可证伪触发器 + 1 个 kill switch

## 方法论：cycle-window-research 技能

本仓库同时交付一个可安装的 Agent 技能（`skills/cycle-window-research/`，打包件 `cycle-window-research.skill`），把标杆报告的研究与呈现方法固化为七步流程：**切窗口 → 建台账 → 当时可知性重建 → 类比矩阵 → 情景算术（含 kill switch）→ 触发器台账 → 编辑级呈现**。核心纪律：分母相容的场景乘法、口径隔离、显式撤回机制、宁可挂起也不估计掉的数据缺口。

## 相关仓库交叉引用（Related Repos）

| 仓库 | 关联点 | 互补关系 |
|---|---|---|
| [basicmi/AI-Chip](https://github.com/basicmi/AI-Chip) ★1.7k | AI/ML 芯片与 IP 名录 | 提供芯片本体目录；本库提供产业格局、份额与周期分析 |
| [aolofsson/awesome-semiconductor-startups](https://github.com/aolofsson/awesome-semiconductor-startups) ★781 | 半导体创业公司清单 | 对应本库§9“创业公司清算文法”的队列全集 |
| [OutBlade/awesome-semiconductor-industry-topics](https://github.com/OutBlade/awesome-semiconductor-industry-topics) | sub-10nm、EUV、先进封装、chiplet 资源集 | 对应§6 四道闸门的技术纵深阅读 |
| [mikeroyal/CoWoS-Guide](https://github.com/mikeroyal/CoWoS-Guide) ★56 | CoWoS 封装指南 | 对应§6.2 CoWoS 产能与工艺细节 |
| [ATOM00blue/ai-stack-silicon-to-tokens](https://github.com/ATOM00blue/ai-stack-silicon-to-tokens) | 从硅到 token 的全栈知识库（Obsidian vault） | 纵向技术栈 ↔ 本库横向产业/资本视角 |
| [harvard-edge/cs249r_book](https://github.com/harvard-edge/cs249r_book) ★29k | Harvard ML Systems 教材 | 加速器系统设计的学术基础 |
| [ai-dynamo/dynamo](https://github.com/ai-dynamo/dynamo) ★8.3k | 数据中心级分布式推理服务框架 | 推理侧软件栈现状，呼应§4.3“推理经济学” |

> 交叉引用选择标准：与 AI 硅片产业链直接相关、仍在维护、与本库视角互补（技术目录/学术/软件栈 vs 产业周期分析）。

## 使用建议

- 读报告：从 `reports/` 主报告入手，数字存疑时回查 `data/fact-register.md` 对应 K 行。
- 复用方法：把 `skills/cycle-window-research/` 安装为 Agent 技能（或直接用打包件），用于任何产业周期研究。
- 监测：按报告 §10.2 触发器台账逐季复核；触发器 1（四大云厂商资本开支增速）为 kill switch。

## 免责声明

本仓库内容基于公开信息编制，仅供研究参考，不构成投资建议。预测性陈述属于分析框架，非对任何证券的推荐。
