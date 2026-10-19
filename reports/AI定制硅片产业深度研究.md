# AI 定制硅片产业深度研究：从 GPU 霸权到 XPU 时代

**研究截止：2026 年 10 月 19 日** · 报告类型：产业全景深度研究 · 配套资产：`assets/` 图表六幅 · 方法论附录：见仓库 `skills/` 与 `data/` 目录

---

## 摘要（Executive Summary）

AI 加速器产业正在经历其历史上最快的收入建设与最深度的资本开支周期。NVIDIA 数据中心收入从 2023 年 4 月季度（Q1 FY2024）的 **42.8 亿美元** 增长到 2026 年 7 月季度（Q2 FY2027）的 **890 亿美元**，三年间增长约 **20.8 倍**，单季同比仍高达 **+117%**（[NVIDIA](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027)）。为这轮建设买单的是人类历史上最大规模的企业资本开支计划：亚马逊、微软、Alphabet、Meta 四家 2025 年合计资本开支约 **4100–4130 亿美元**，2026 年指引合计约 **7250 亿美元**，同比增幅约 **77%**，Evercore 与美国银行已预计 2027 年合计突破 **1 万亿美元**（[AI Weekly](https://aiweekly.co/alerts/amazon-microsoft-alphabet-meta-plan-725b-ai-capex-in-2026)）。

本报告的核心论点是：**产业的结构性矛盾已从"是否买 GPU"迁移到"GPU 还是自研 XPU"，再从芯片本身迁移到芯片背后的四道物理闸门——HBM 高带宽内存、先进制程、CoWoS 先进封装与电网**。定制 ASIC 出货量预计 2024–2027 年增长三倍，2028 年出货突破 1500 万颗并超过数据中心 GPU 出货量（[Counterpoint](https://counterpointresearch.com/en/insights/AI-Server-Compute-ASIC-Shipments-to-Triple-by-2027)）；但按美元口径，定制硅片在加速器支出中的占比仍远落后于出货量口径——这是阅读一切"ASIC 超越 GPU"标题时必须牢记的度量纪律。HBM 市场 2026 年规模预计 **546 亿美元**（同比 +58%），且三大原厂 2026 年产能已全部售罄、2027 年大部分产能已被预订（[Silicon Analysts](https://siliconanalysts.com/analysis/hbm4-market-share-race-2026)）；台积电 CoWoS 月产能从 2022 年约 1.2 万片爬坡至 2026 年底约 12–13 万片，供需缺口预计从约 20% 收窄至约 10%（[TrendForce](https://www.trendforce.com/news/2026/06/15/news-tsmc-cowos-supply-demand-gap-reportedly-seen-narrowing-from-20-to-10-by-end-2026-as-capacity-expands/)）；而电网并网排队已成为唯一无法用资本开支在两年内买开的闸门——美国 ERCOT 大负荷并网申请超过 438GW，其中近九成来自数据中心（[Forbes](https://www.forbes.com/sites/guneyyildiz/2026/06/30/the-energy-transition-just-hit-the-wall-ai-compute-cannot-ignore/)）。

本报告不给出单点结论，而是给出两条情景路径与一组可证伪触发器：**基准情景**下，定制硅片美元份额从 2025 年的约 12% 向 2027–2028 年的 20% 以上迁移，产业利润池向闸门所有者（HBM 三强、台积电、ASIC 设计伙伴、互联厂商）再分配；**收缩情景**下，若四大云厂商 2027 年资本开支增速跌破约 +15%，全行业将进入类似 2001 年光通信泡沫出清的"并购而非破产"式清算。判定权交给数据，而非叙事。

---

## 一、产业全景与市场总量

### 1.1 市场规模的三种数法

AI 加速器市场的规模估计因口径不同而差异巨大，这本身就是理解该产业的第一课。Mordor Intelligence 的宽口径（含 GPU/ASIC/FPGA、云与边缘）给出 2025 年 **1405.5 亿美元**、2026 年 **1746.9 亿美元**、2031 年 **5181.2 亿美元** 的规模路径，对应 2026–2031 年 CAGR 约 **24.3%**；其中 GPU 占 2025 年收入份额 59.2%，ASIC 以 27.25% 的 CAGR 成为增长最快的处理器类型（[Mordor Intelligence](https://www.mordorintelligence.com/industry-reports/ai-accelerators-market)）。窄口径的"数据中心加速器"市场则小得多：Grand View Research 估计 2025 年为 241 亿美元、2033 年 1422 亿美元（[Grand View Research](https://www.grandviewresearch.com/industry-analysis/data-center-accelerator-market-report)）。口径差异主要来自是否计入整机系统、边缘设备与定制芯片的内部转移定价——投资者引用任何 TAM 数字前，必须先问分母是什么。

比绝对规模更重要的是结构变化的方向。ResearchAndMarkets 的长周期报告将"数据中心计算与 AI"市场 2025 年定为约 2150 亿美元，并把 GPU、定制 ASIC、Arm 对 x86 之争并列为未来十五年的三条主线（[ResearchAndMarkets via Yahoo](https://finance.yahoo.com/technology/ai/articles/global-market-computing-ai-data-111600912.html)）。三家机构对增速的估计惊人地一致——24%–27% 的复合增速区间——但对 ASIC 渗透斜率的估计分歧明显，这恰是本报告第五节要展开的核心争议。

### 1.2 产业链分层与利润池地图

AI 硅片产业链可分为五层：**设计**（NVIDIA、AMD、云厂商自研团队、ASIC 设计服务商）、**制造**（台积电一家独占 3nm 级先进制程的事实供给）、**封装**（台积电 CoWoS 为主，日月光/Amkor 承接外溢订单）、**内存**（SK 海力士、三星、美光三家垄断 HBM）、**互联与系统**（Broadcom/Marvell 的交换芯片与 SerDes、光模块、整机 ODM）。2026 年的产业现实是：每一层都呈现寡头格局，且每一层的寡头都在本季度创下了历史最高利润——台积电 Q3 2026 净利润 7631 亿新台币（同比 +68.7%），连续第六个季度创纪录，营业利润率达 58.7%（[Yahoo Finance](https://finance.yahoo.com/technology/articles/tsmcs-record-q3-earnings-upbeat-140000557.html)）。

利润池的分布验证了一个关键假设：**"征税权"属于产能不可快速复制的环节**。NVIDIA 单季毛利率 75.0%、台积电营业利润率 58.7%、SK 海力士 HBM4 报价比 HBM3E 溢价约 70%——而处于充分竞争环节的整机 ODM 与云厂商自身，则分别承受个位数毛利与破表的资本开支强度。下表汇总了产业链各层 2026 年的代表性格局：

| 环节 | 主导者 | 2026 年关键事实 | 竞争格局 |
|---|---|---|---|
| 商用 GPU | NVIDIA | Q2FY27 数据中心收入 890 亿美元，同比 +117%（[NVIDIA](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027)） | 一家独大，AMD 加速追赶 |
| 自研 XPU | Google/AWS/微软/Meta/OpenAI | TPU v8 分拆训练/推理双芯片；Trainium3 上量；Maia 200 已部署 | 云厂商内部市场，不外卖 |
| ASIC 设计服务 | Broadcom、Marvell、MediaTek、世芯、创意 | Broadcom AI 收入 Q3FY26 达 167 亿美元，同比 +221%（[Broadcom](https://www.prnewswire.com/news-releases/broadcom-inc-announces-third-quarter-fiscal-year-2026-financial-results-and-quarterly-dividend-302868129.html)） | 五家分食，Broadcom 领跑 |
| 晶圆代工 | 台积电 | Q3 2026 收入 467.2 亿美元，同比 +41.2%（[TSPA](https://tspasemiconductor.substack.com/p/tsmcs-2026-q3-earnings-call-ai-demand)） | 先进制程事实垄断 |
| 先进封装 | 台积电 CoWoS + OSAT | 2026 年底月产能约 12–13 万片（[TrendForce](https://www.trendforce.com/news/2026/06/15/news-tsmc-cowos-supply-demand-gap-reportedly-seen-narrowing-from-20-to-10-by-end-2026-as-capacity-expands/)） | 台积电主导，外溢至日月光/Amkor |
| HBM | SK 海力士、三星、美光 | 2026 市场约 546 亿美元，2026 产能售罄（[Silicon Analysts](https://siliconanalysts.com/analysis/hbm4-market-share-race-2026)） | 三寡头，份额再平衡中 |
| 网络互联 | Broadcom、Marvell、NVIDIA | Tomahawk 6（100Tbps）发布逾半年无对手（[Enertuition](https://enertuition.substack.com/p/broadcom-is-not-likely-to-fly-on)） | 商用双雄 + NVIDIA 私有生态 |

---

## 二、需求侧：史上最深的资本开支周期

### 2.1 四大云厂商的开支解剖

需求侧的总量数字需要分解才能读懂。2026 年指引层面：亚马逊约 **2000 亿美元**、微软约 **1900 亿美元**、Alphabet **1750–1850 亿美元**、Meta **1150–1350 亿美元**，合计约 7250 亿美元，较 2025 年的约 4100 亿美元增长 77%（[AI Weekly](https://aiweekly.co/alerts/amazon-microsoft-alphabet-meta-plan-725b-ai-capex-in-2026)；[Statista](https://www.statista.com/chart/35046/capital-expenditure-of-meta-alphabet-amazon-and-microsoft/)）。CreditSights 估计其中约 75%（约 4500 亿美元）直接流向 AI 基础设施——GPU、服务器、网络设备与数据中心（[Investing.com](https://www.investing.com/analysis/big-tech-will-spend-600b-on-ai-in-2026-5-stocks-cashing-the-checks-200674615)）。一个可比的量级参照是：这一数字超过美国整个上市能源行业年度钻井、炼化与配送资本开支的四倍。

![四大云厂商资本开支](assets/fig1_hyperscaler_capex.png)

资金的流向同样值得解剖。Presenc AI 的追踪显示，NVIDIA 截获总流量的约 55–60%，AMD 约 7–9%，台积电约 8–10%，HBM 三强合计约 6–8%（[Presenc AI](https://presenc.ai/research/hyperscaler-ai-capex-map-2026)）。值得注意的是 2026 年 7 月季度的边际变化：微软单季因芯片涨价增加的支出估计高达 250 亿美元——需求曲线没变，是供给的价格在涨（[Statista](https://www.statista.com/chart/35046/capital-expenditure-of-meta-alphabet-amazon-and-microsoft/)）。这是"闸门征税"最直接的财务证据。

### 2.2 需求是否真实：应用层收入的交叉验证

支撑这轮开支的应用层收入正在以史无前例的速度兑现，但也开始出现需要仔细审计的裂缝。OpenAI 年化收入 2025 年底约 200 亿美元，2026 年 10 月约 **500 亿美元**——但 FT 的更正报道揭示，此前市场盛传的 700 亿美元口径源于投资者用 Anthropic 的会计方法（将云伙伴渠道全额计入收入）对 OpenAI 做的"毛额化"调整，OpenAI 自身口径只计入分成净额（[Axios](https://www.axios.com/2026/10/08/openai-50-billion-arr-anthropic-revenue-accounting)；[Exploding Topics](https://explodingtopics.com/blog/openai-revenue)）。Anthropic 年化收入 2026 年 7 月底达 **650 亿美元**，4 月时刚突破 300 亿美元（[Yahoo Finance](https://finance.yahoo.com/technology/article/openais-annualized-revenue-20-billion-lower-than-prior-investor-estimates-174058048.html)；[Anthropic](https://www.anthropic.com/news/google-broadcom-partnership-compute)）。

硬币的另一面是亏损与承诺之间的巨大缺口。OpenAI 2025 年经营亏损 209.2 亿美元，2026 年 Q2 单季经营亏损 123 亿美元；公司预计 2026–2030 年累计负自由现金流约 **2780 亿美元**，同期算力与基础设施支出约 **8560 亿美元**（[Exploding Topics](https://explodingtopics.com/blog/openai-revenue)）。换言之，应用层收入的确在指数增长，但当前 AI 基础设施建设的相当一部分是由**资本市场的信仰溢价**而非经营现金流资助的——这正是 2001 年光通信周期与本轮周期最本质的财务相似点，尽管 2026 年的出资方主体（云厂商）远比 2000 年的电信运营商盈利。

---

## 三、商用 GPU 阵营：NVIDIA 霸权与 AMD 的破局

### 3.1 NVIDIA：把加速器公司变成经济体系的中央节点

NVIDIA 的 Q2 FY2027（截至 2026 年 7 月 26 日）财报是一组需要停下来消化量级的数字：总营收 962.2 亿美元（同比 +106%），数据中心 890 亿美元（同比 +117%，占比 92.5%），GAAP 毛利率 75.0%，单季 GAAP 净利润 596.9 亿美元；Q3 指引 1080 亿美元，且该指引**不包含任何来自中国的数据中心计算收入**（[NVIDIA](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027)）。年化收入运行率约 4320 亿美元——超过 2025 年全球半导体全行业销售额的一半。2025 年 10 月 29 日，NVIDIA 成为历史上首家市值突破 **5 万亿美元** 的公司；从 1 万亿到 5 万亿，用了不到两年半（[Fortune](https://fortune.com/2025/10/29/nvidia-first-5-trillion-company-ceo-jensen-huang-500-billion-revenue-blackwell-rubin-gpus-china/)）。

![NVIDIA 数据中心收入](assets/fig2_nvidia_dc_revenue.png)

结构上最值得关注的变化是收入构成的多元化与平台化。Q2 FY2027 的 890 亿美元中，超大规模云厂商子分部约 490 亿美元，而"ACIE"子分部（NeoCloud、主权 AI、工业与企业）达 400 亿美元，环比 +25%、同比 +138%，管理层预计长期将占数据中心收入约一半（[BetaFinch](https://betafinch.com/blog/nvidia-fy2027-revenue-breakdown-by-segment)）。同时，NVIDIA 正在把护城河从芯片扩展到机架与互联：Vera Rubin 平台已全面量产，每吉瓦装机对应的 NVIDIA 收入从 Hopper 代的约 180 亿美元升至 Rubin 代的约 400 亿美元（[BetaFinch](https://betafinch.com/blog/nvidia-fy2027-revenue-breakdown-by-segment)）；而对 Groq 推理技术约 **200 亿美元** 的非独家授权交易（2025 年 12 月）已转化为 GTC 2026 上发布的 Groq 3 LPU——由三星 4nm 代工、在 Vera Rubin 平台内负责 decode 阶段的 SRAM 协处理器（[InferenceChips](https://www.inferencechips.com/companies/groq/)；[Lexology](https://www.lexology.com/library/detail.aspx?g=ab4f2eb1-065e-4b12-8d18-a4c180522d0b)）。

### 3.2 AMD：Helios 机架与 OpenAI 的 6GW 期权

AMD 在 2025 年 10 月完成了 AI 时代最重要的单点突破：与 OpenAI 签订多年期、跨代际的 **6GW** GPU 部署协议，首个 1GW 的 MI450 系列于 2026 下半年开始部署；作为交易结构的一部分，AMD 向 OpenAI 授予最多 1.6 亿股认股权证（完全行权约占股本 10%），行权与部署里程碑及 AMD 股价目标双重挂钩（[AMD](https://ir.amd.com/news-events/press-releases/detail/1260/amd-and-openai-announce-strategic-partnership-to-deploy-6-gigawatts-of-amd-gpus)；[More Than Moore](https://morethanmoore.substack.com/p/amd-and-openai-the-6-gigawatt-bet)）。这笔交易的潜在销售价值约 900 亿美元，消息当日 AMD 股价盘中上涨 35%——它把 AMD 从"第二供应商"升格为前沿实验室的战略级算力伙伴。

执行层面，Helios 机架级系统的爬坡节奏是 2026 下半年至 2027 年最重要的观察点：Q3 2026 是"爬坡起点"，Q4 显著上量，2027 年 Q1 进一步放量，量产高峰要到 2027 年 Q2（[BloFin](https://blofin.com/en/academy/education/amd/amd-ai-chip-roadmap-mi450-and-helios-explained)）。客户名单已从 OpenAI 扩展到 Oracle（5 万颗 MI450 超级集群，2026 Q3 起）、Anthropic（最多 2GW，首个 1GW 于 2027 上半年上线）、微软、Meta 等（[Shattered](https://shattered.io/amd-helios-mi450-oracle-50000-gpus-2026/)）。满配 Helios 机柜单价约 500–550 万美元；ROCm 软件生态在推理负载上已实质性缩小与 CUDA 的差距，但训练侧的库广度仍落后约二十年积累（[Shattered](https://shattered.io/amd-helios-mi450-oracle-50000-gpus-2026/)）。

---

## 四、定制硅片浪潮：云厂商的自研芯片军备赛

### 4.1 Google TPU：从内部成本优势到外部商品

TPU 是定制硅片浪潮的源头与体量基准。2026 年 4 月 22 日 Cloud Next 上发布的第八代 TPU 首次把训练与推理拆成两颗芯片：**TPU 8t（Sunfish）** 与 Broadcom 共同设计，面向大规模训练，单芯片 FP4 峰值 12.6 PFLOPS，9600 芯片超级 Pod 提供 121 ExaFLOPS（FP4），较 Ironwood 训练成本性能比提升约 2.7 倍；**TPU 8i（Zebrafish）** 与 MediaTek 共同设计，面向推理与智能体负载，HBM 增至 288GB、带宽 8.6TB/s，片上 SRAM 达 384MB，推理成本性能比较 Ironwood 提升约 80%，两者均计划 2026 下半年 GA（[AI-Revolution](https://ai-revolution.co.jp/media/what-is-tpu-v8/)；[Wccftech](https://wccftech.com/google-splits-tpuv8-strategy-two-chips-broadcom-training-mediatek-inference-duties/)）。

TPU 的经济属性已在 2025–2026 年发生质变：从"Google 自己的省钱工具"变成"对外出售的云商品"。Anthropic 2025 年 10 月承诺使用最多 **100 万颗 TPU**，对应 2026 年超过 1GW、2027 年 3.5GW 的算力；2026 年 4 月，Anthropic 再与 Google 和 Broadcom 签订多吉瓦级下一代 TPU 扩容协议，2027 年起上线（[Tech-Insider](https://tech-insider.org/google-tpu-8t-8i-broadcom-mediatek-nvidia-2026/)；[Anthropic](https://www.anthropic.com/news/google-broadcom-partnership-compute)）。Counterpoint 预计 Google 在 2027 年仍将占全球 AI 服务器 ASIC 出货量的约 52%，是行业无可争议的体量锚（[Counterpoint](https://counterpointresearch.com/en/insights/AI-Server-Compute-ASIC-Shipments-to-Triple-by-2027)）。TPU v8 双供应商策略（Broadcom 管训练、MediaTek 管推理）的另一层含义是成本：Google 通过自设计算裸片 + MediaTek 提供 I/O 裸片的解耦模式，消除了 Broadcom 整包模式中 HBM 采购 15–20% 的加价（[Counterpoint](https://counterpointresearch.com/en/insights/MediaTek-to-Contribute-1-in-4-AI-ASIC-Server-Compute-Shipments-in-2028)）。

### 4.2 AWS、微软、Meta 与 OpenAI：第二梯队的四种打法

AWS 的 Trainium3 采用台积电 3nm，配 144GB HBM3E 与 4.9TB/s 带宽，较 Trainium2 计算翻倍、能效提升 40%，通过 EC2 Trn3 实例对外出租，是除 TPU 外唯一形成外部收入流的自研芯片；Trainium4 预计 2026 年底至 2027 年初交付，将在 UltraServer 集群规模上大幅扩展（[The Next Platform](https://www.nextplatform.com/compute/2025/12/03/with-trainium4-aws-will-crank-up-everything-but-the-clocks/1700879)；[Spheron](https://www.spheron.network/blog/hyperscaler-custom-ai-chips-2026-trainium-tpu-maia-mtia-vs-nvidia-gpu/)）。微软 Maia 200 于 2026 年 1 月 26 日发布——台积电 3nm、1400 亿晶体管、FP4 超 10 PFLOPS、216GB HBM3e、272MB 片上 SRAM、单集群上限 6144 颗，已在 Azure 内部推理负载部署；而 10 月 12 日刚发布的 **Maia 300** 进一步跳到 N2P 制程与 288GB HBM4、18TB/s 带宽，2027 年投产，号称每兆瓦 token 数较"领先 GPU 系统"高 40%（[YouTube/Maia 200](https://www.youtube.com/watch?v=WdIIEWJzvKk)；[GadgetSalvation](https://www.gadgetsalvation.com/blog/microsoft-ai-chips-maia-300-vs-maia-200)）。

Meta 的 MTIA 走"内部效率芯片"路线：300 代已量产承担推荐排序负载，400 代在测，450/500 代在路线图上，不对外提供任何形式租用（[Spheron](https://www.spheron.network/blog/hyperscaler-custom-ai-chips-2026-trainium-tpu-maia-mtia-vs-nvidia-gpu/)）。最具野心的新进入者是 OpenAI：与 Broadcom 合作的首款自研推理芯片 **Jalapeño** 从设计到流片仅用九个月，工程样品已在目标频率与功耗下运行 GPT-5.3-Codex-Spark，目标较典型 AI GPU 推理成本节约约 50%；该芯片锚定双方 **10GW** 的战略合作（2026 下半年开始部署、2029 年底完成），据报道微软将采购首批约 40% 的产量（[MLQ](https://mlq.ai/news/openai-and-broadcom-unveil-jalapeno-a-custom-inference-chip-targeting-late-2026-deployment/)；[OpenAI](https://openai.com/index/openai-and-broadcom-announce-strategic-collaboration/)）。

### 4.3 渗透率的三种数法：度量纪律

"ASIC 超越 GPU"的说法在 2026 年已不罕见，但三种口径给出三个截然不同的答案。**出货量口径**：J.P. Morgan 预计 ASIC/XPU 占 AI 加速器出货量的份额 2027 年升至 54%、2028 年 55%，正式超过 GPU（[Webull](https://www.webull.com/news/15613772749751296)）；Counterpoint 预计 ASIC 出货 2024–2027 年翻三倍、2028 年突破 1500 万颗（[Counterpoint](https://counterpointresearch.com/en/insights/AI-Server-Compute-ASIC-Shipments-to-Triple-by-2027)）。**AI 服务器结构口径**：TrendForce 预计 ASIC 方案占 AI 服务器出货 2026 年 27.8%、2030 年接近 40%（[TrendForce](https://www.trendforce.com/news/2026/03/20/news-csps-accelerate-asic-push-in-2h26-challenging-nvidia-as-mediatek-guc-alchip-benefit/)）。**美元口径**——唯一触及收入、毛利与资本开支压力的尺子：Goldman Sachs 的表述是"2027 年 ASIC 的 AI 需求与 GPU 持平"，但这同样混合了台数与金额（[BigGo](https://finance.biggo.com/news/EN-jYp4BpwxG186NrCxt)）。

度量纪律的要害在于：一颗云端推理 ASIC 的价格可能只有商用 GPU 的几分之一，出货量"超越"不等于价值量"超越"。对场景算术而言，只有美元口径可以进入收入倍数的乘法；出货量口径只用于约束物理产能的上限。Broadcom 管理层给出的一个锚点是：XPU 部署的收入密度约为每吉瓦 **200–300 亿美元**（芯片功耗上升抵消 ASP 上涨）（[AlphaSense](https://www.alpha-sense.com/earnings/avgo/)）——这把"GW 叙事"翻译成了可审计的美元语言。

---

## 五、ASIC 设计服务链：新"卖铲人"格局

### 5.1 Broadcom：定制硅片时代的旗舰收费站

Broadcom 的 Q3 FY2026（截至 2026 年 8 月 2 日）是 ASIC 设计服务商业模式的最强证明：合并收入 296 亿美元（同比 +86%），其中 AI 半导体收入 **167 亿美元**（同比 +221%、环比 +54%），占总收入 56%；Q4 指引 AI 收入 217 亿美元（同比 +236%）；FY2026 全年 AI 收入预计 580 亿美元（同比 +186%），管理层进一步给出 FY2027 约 **1150 亿美元**、FY2028 约 **2300 亿美元** 的翻倍路径（[PRNewswire](https://www.prnewswire.com/news-releases/broadcom-inc-announces-third-quarter-fiscal-year-2026-financial-results-and-quarterly-dividend-302868129.html)；[AlphaSense](https://www.alpha-sense.com/earnings/avgo/)）。结构上，XPU 出货同比增长超 3.5 倍、占 AI 收入 73%；AI 网络收入同比增长超 2.5 倍——Broadcom 同时在"计算"与"互联"两条收费站上收钱。

客户结构上，Broadcom 的 XPU 特许经营权覆盖六家以上合格客户，当季向 Anthropic 与 Google 大批量交付 Ironwood TPU v7，并开始量产出货 Google TPU 8i，同时交付了 OpenAI 的 Jalapeño——管理层称其推理负载表现优于 Grace Blackwell（[AlphaSense](https://www.alpha-sense.com/earnings/avgo/)）。Counterpoint 预计 Broadcom 2027 年保持约 **60%** 的 AI 服务器 ASIC 设计伙伴份额（[Counterpoint](https://counterpointresearch.com/en/insights/AI-Server-Compute-ASIC-Shipments-to-Triple-by-2027)）。风险同样清晰：Google 一家贡献的比重从未披露，而 Google 恰是最早启动双供应商策略的客户；非 AI 半导体业务多年停滞，公司估值几乎完全绑定 AI 叙事（[Enertuition](https://enertuition.substack.com/p/broadcom-is-not-likely-to-fly-on)）。

![Broadcom AI 收入](assets/fig3_broadcom_ai_revenue.png)

### 5.2 MediaTek 的突袭与台湾设计服务双雄

MediaTek 是 2026 年 ASIC 格局最大的变量。凭借 ISSCC 获奖的 212.6Gb/s SerDes 技术，MediaTek 先是为 Google Ironwood 供应 I/O 裸片 IP，继而拿下 TPU 8i（Zebrafish）的完整共同设计；公司将 2026 年 AI 数据中心 ASIC 收入指引上调至 **20 亿美元**，并把 2027 年 700–800 亿美元 TAM 的目标份额定在 15–20%（[MediaTek](https://www.mediatek.com/tek-talk-blogs/from-silicon-to-scale-inside-mediateks-ai-data-center-solution)；[Yahoo Finance](https://finance.yahoo.com/technology/ai/articles/mediatek-wants-20-custom-ai-182411966.html)）。Counterpoint 预计，受 Zebrafish 及其后继 v8e（Humufish）拉动，MediaTek 2028 年将占全球 AI ASIC 服务器计算出货量的 **26%**、接近 500 万颗，成为仅次于 Broadcom 的第二大设计伙伴（[Counterpoint](https://counterpointresearch.com/en/insights/MediaTek-to-Contribute-1-in-4-AI-ASIC-Server-Compute-Shipments-in-2028)）。

台湾设计服务双雄是链条上的"台积电近邻"：世芯（Alchip）已获得 AWS Trainium 3 订单，3nm 芯片 2026 年 Q2 量产、Q3 收入放量，多个 2nm AI/HPC 项目推进中（[TrendForce](https://www.trendforce.com/news/2026/03/20/news-csps-accelerate-asic-push-in-2h26-challenging-nvidia-as-mediatek-guc-alchip-benefit/)）；创意电子（GUC）则拿下 Google 与 Meta 的下一代 CPU 项目，车用 ADAS 已量产（[TrendForce](https://www.trendforce.com/news/2026/03/20/news-csps-accelerate-asic-push-in-2h26-challenging-nvidia-as-mediatek-guc-alchip-benefit/)）。这一层商业模式的本质是"卖通往闸门的门票"——NRE 设计费领先量产收入一到两年，收入确认的节奏天然锯齿化；两家公司在上一轮加密货币周期中都曾印出过年收入腰斩的锯齿，本轮承载的是云厂商订单，周期属性更平滑但并未消失。

![ASIC 设计伙伴份额](assets/fig6_asic_partner_share.png)

---

## 六、供给四道闸门：HBM、制程、封装与互联

### 6.1 HBM：最刚性的闸门与正在松动的寡头座次

HBM 是 AI 加速器物料清单中最大的单一成本项：在 H200/B200/GB200 等主力 SKU 中，HBM 占制造成本的 **46–48%**；在 AMD MI325X 中高达 **64%**（[Silicon Analysts](https://siliconanalysts.com/analysis/hbm4-market-share-race-2026)）。BofA 估计 2026 年 HBM 市场总规模 **546 亿美元**（同比 +58%），Goldman Sachs 预计定制 ASIC 对 HBM 的需求增长 82%、占总需求三分之一（[Silicon Analysts](https://siliconanalysts.com/analysis/hbm4-market-share-race-2026)）。供给端只有三家厂商，2026 年产能已全部售罄：美光 2026 年 HBM 全部以固定价格合同锁定，且 2027 年大部分产能已被客户以"显著高于 2026 年"的价格预订，CEO 明言 2027 与 2028 年需求都将超过供给（[Tickeron](https://tickeron.com/blogs/micron-technology-mu-sold-out-hbm-supply-and-ai-tailwinds-point-to-strong-2026-growth-12100/)；[BigGo](https://finance.biggo.com/news/005d09f6-60ed-41cc-99e7-f81919b78e7d)）。

价格是这轮周期最灵敏的温度计：SK 海力士在 HBM4 早期谈判中的报价较 HBM3E 溢价约 70%；三星 2027 年 HBM4 合约报价已达每 Gb 4.50 美元起，而当前主流 HBM3E 约每 Gb 1.50 美元——单代涨价超过三倍，研究机构预计 2027 年 HBM 混合 ASP 同比上涨 **121%**（[BigGo](https://finance.biggo.com/news/005d09f6-60ed-41cc-99e7-f81919b78e7d)；[Tech-Insider](https://tech-insider.org/hbm4-memory-shortage-dram-inventory-2026/)）。份额层面正在发生十年未见的再平衡：SK 海力士的季度收入份额从 2026 Q1 的 58% 降至 Q2 的 50%，三星从 21% 升至 33%——三星 2026 年 2 月 12 日率先宣布 HBM4 量产出货（11.7Gbps），而 SK 海力士 2025 年 9 月已完成 HBM4 开发并备产，预计拿下 NVIDIA Rubin 平台约 70% 的 HBM4 份额（[Silicon Analysts](https://siliconanalysts.com/analysis/hbm4-market-share-race-2026)）。挤压效应已外溢到传统 DRAM：三星与 SK 海力士成品 DRAM 库存跌破 10 天，DDR4/DDR5 价格向 PC 与消费电子传导（[Tech-Insider](https://tech-insider.org/hbm4-memory-shortage-dram-inventory-2026/)）。

![HBM 市场份额](assets/fig4_hbm_share.png)

### 6.2 先进制程与 CoWoS：一个人的军备赛

先进制程是"政治经济学意义上的稀缺"：3nm 级节点事实上只有台积电一家可供记录，N−1/N−2 节点的绕行方案需付出 20–30% 的性能与功耗税。台积电 Q3 2026 收入 467.2 亿美元（同比 +41.2%），毛利率 66.4%，HPC 平台已占收入 66%；Q4 指引 523–543 亿美元；管理层在 7 月法说会上直言"封装产能紧张到正在限制我客户的增长"（[TSPA](https://tspasemiconductor.substack.com/p/tsmcs-2026-q3-earnings-call-ai-demand)；[Gotrade](https://www.heygotrade.com/en/news/tsmc-q3-earnings-preview-faces-high-bar-amid-ai-stock-jitters/)；[Silicon Analysts](https://siliconanalysts.com/analysis/foundry-allocation-status-q1-2026)）。Morgan Stanley 预计台积电 2027 年资本开支 750–800 亿美元、2027 年先进制程涨价 5–10%。

CoWoS 是"算术意义上的稀缺"：产能以约每季度一万片的"板坯"节奏增加，而订单领先产能约两个季度。月产能从 2024 年底约 3.5 万片爬至 2025 年底约 7.5–8 万片，2026 年底目标 12–13 万片（第三方估计，台积电不披露）；总需求 2026 年逼近 100 万片/年，供需缺口预计从约 20% 收窄至年底约 10%，2027 年进一步缓解——但产线依然保持满载预订（[GlobalSemiResearch](https://globalsemiresearch.substack.com/p/tsmcs-cowos-capacity-scaling-up-outsourcing)；[TrendForce](https://www.trendforce.com/news/2026/06/15/news-tsmc-cowos-supply-demand-gap-reportedly-seen-narrowing-from-20-to-10-by-end-2026-as-capacity-expands/)）。外溢订单正在重塑 OSAT 格局：台积电 2026 年起将 24–27 万片/年的 CoW 工序外包给 Amkor 与日月光/矽品，OSAT 合计"类 CoWoS"月产能年底约 4 万片；更下一代的 CoPoS（面板级封装）已完成研发线建设，NVIDIA Feynman 平台预计成为首个客户，2028–2029 年量产（[TrendForce](https://www.trendforce.com/news/2026/06/15/news-tsmc-cowos-supply-demand-gap-reportedly-seen-narrowing-from-20-to-10-by-end-2026-as-capacity-expands/)；[X/jukan05](https://x.com/jukan05/status/2000395081304658182)）。

![CoWoS 产能](assets/fig5_cowos_capacity.png)

### 6.3 互联：从 plumbing 到性能乘数

当单 Pod 规模逼近一万颗芯片，互联 Fabric 本身就是计算机。这场战争在三条战线同时展开。**私有生态**：NVIDIA 以 NVLink Fusion 向第三方 XPU 开放机架级 Fabric，并通过对 MediaTek 39 亿美元可转债的共同投资（2026 年 8 月 31 日，Alphabet 同为投资方）把 MediaTek 确立为 NVLink Fusion 的主要 XPU 集成门户（[TechTimes](https://www.techtimes.com/articles/326276/20260902/nvlink-fusion-vs-ualink-why-alphabet-funding-both-sides-ai-chip-interconnect-war.htm)）。**开放标准**：UALink 联盟（AMD、Broadcom、Cisco、HPE、Intel、Meta、微软与 Alphabet 共同发起）2026 年 4 月发布 2.0 规范、成员超 115 家，支持单 Pod 1024 颗加速器；但截至 2026 年 9 月，原生 UALink 交换芯片尚未量产，AMD Helios 的 H2 2026 系统以 UALink-over-Ethernet（800GbE 物理层）作为过渡（[TechTimes](https://www.techtimes.com/articles/326276/20260902/nvlink-fusion-vs-ualink-why-alphabet-funding-both-sides-ai-chip-interconnect-war.htm)；[UALink Consortium](https://ualinkconsortium.org/wp-content/uploads/2026/01/UALink_White_Paper_Publication_FINAL_UPDATED.pdf)）。

**以太网阵营**则由 Broadcom 领跑：Tomahawk 6（100Tbps）发布逾半年无竞争对手，200G SerDes 大规模部署，且 Broadcom 是目前唯一支持 1.6Tbps DSP 的厂商——OpenAI 的 10GW 自研芯片集群选择全以太网架构，是对这条路线的最大背书（[Enertuition](https://enertuition.substack.com/p/broadcom-is-not-likely-to-fly-on)；[OpenAI](https://openai.com/index/openai-and-broadcom-announce-strategic-collaboration/)）。值得玩味的是 Alphabet 的三面下注：既是 UALink 创始董事，又采购 MediaTek 设计的 TPU 8i，还与 NVIDIA 共同投资 MediaTek 可转债——头部买家故意不在互联标准上站队，说明这场战争的胜负远未分出，而"被锁定在某一种 Fabric 上"本身已成为采购决策中的显式风险项。

---

## 七、终极约束：电网

### 7.1 排队即瓶颈

把约束沿产业链追到底，就离开了半导体行业本身。IEA 口径下全球数据中心用电量 2024 年约 415TWh，2030 年将达约 945TWh；2026 年预计约 1100TWh——约等于日本全国用电量（[JamesM Blog](https://jamesm.blog/ai/ai-energy-crisis-data-center-power/)；原报告引 IEA《Energy and AI》2025）。真正卡脖子的不是发电量而是并网：LBNL《Queued Up: 2026》统计美国约 2060GW 的发电与储能项目在排队并网，2025 年建成项目从申请到商运的中位时间超过五年；北弗吉尼亚、凤凰城、达拉斯等数据中心热点区域的并网等待达 **4–7 年**（[Global Data Center Hub](https://www.globaldatacenterhub.com/p/us-data-center-infrastructure-the)）。

德州 ERCOT 是最极端的样本：大负荷并网申请超过 438GW、近九成来自数据中心，仅 2026 年 Q1 新增申请就有 198GW——约等于 ERCOT 整个系统的峰值负荷；PJM 区域 2027/28 容量拍卖首次出现全网可靠性缺口（约 6625MW），Monitoring Analytics 测算数据中心贡献了 2025/26 拍卖价格上涨的 63%（约 93 亿美元新增成本）（[Forbes](https://www.forbes.com/sites/guneyyildiz/2026/06/30/the-energy-transition-just-hit-the-wall-ai-compute-cannot-ignore/)；[Global Data Center Hub](https://www.globaldatacenterhub.com/p/us-data-center-infrastructure-the)）。设备链同样堵塞：标准电力变压器平均交期 128 周，发电机升压变压器 144 周，特种型号最长四年（[Global Data Center Hub](https://www.globaldatacenterhub.com/p/us-data-center-infrastructure-the)）。Goldman Sachs 估计明年计划投产容量只有约 60% 能按期交付，之后两年降至 50%。

### 7.2 吉瓦经济学

机架级算术把抽象约束翻译成美元：一座 GB200 NVL72 机架功耗约 120kW，1GW 的 AI 容量约等于 8300 个机架、约 60 万颗封装芯片、约 500 亿美元的全口径资本开支（原报告方法论）；Broadcom 给出的 XPU 口径是每吉瓦 200–300 亿美元的芯片收入（[AlphaSense](https://www.alpha-sense.com/earnings/avgo/)）。对照已具名的承诺——Stargate 规划约 7GW/4000 亿美元以上、OpenAI–Oracle 4.5GW、Meta Hyperion 约 5GW、xAI Colossus、AWS Project Rainier、Anthropic–Google 3.5GW、Anthropic–AMD 2GW、OpenAI–Broadcom 10GW、OpenAI–AMD 6GW——行业正在讨论的总量达数十吉瓦，而每个区域电网每年只能消化个位数吉瓦（[OpenAI](https://openai.com/index/openai-and-broadcom-announce-strategic-collaboration/)；[AMD](https://ir.amd.com/news-events/press-releases/detail/1260/amd-and-openai-announce-strategic-partnership-to-deploy-6-gigawatts-of-amd-gpus)）。

电网约束的投资含义是双重的。对多头：它给"算力短缺"叙事提供了最持久的物理支撑——HBM 四年扩四倍、CoWoS 按季度加板坯，而输电互联研究以 4–7 年为周期，是唯一无法被资本开支在两年内买开的闸门。对空头：它意味着任何需求侧的失望都会首先以"园区停工、电力协议重谈"的形式暴露在公开文件里——这给了市场一个比财报更早的预警信号。选址逻辑已经反转：园区建在能搞到电的地方，算力跟着兆瓦走。

---

## 八、中国：出口管制、国产替代与平行供应链

### 8.1 管制的双向化

美国对华 AI 芯片管制在 2025–2026 年经历了史上最密集的反复：H20 于 2025 年 4 月被要求"无限期"许可（NVIDIA 单季计提 45 亿美元损失），7 月又在稀土贸易协议框架下恢复发证，附带向美国政府分成 15% 收入的条件；2026 年 1 月 15 日起 H200 进入"个案审批、附量帽与测试要求"的有条件许可状态，而整个 Blackwell 家族对华出口仍是"推定拒绝"（[GPUSmith](https://gpusmith.com/articles/en/nvidia-gpu-export-restrictions)）。中国一侧同样加码：2025 年 9 月网信办禁止大型科技企业采购 NVIDIA AI 芯片，11 月进一步要求所有使用国家资金的新建数据中心项目只用国产芯片——2021 年以来中国 AI 数据中心项目获得的国家资金超过 1000 亿美元，该指引覆盖面极大，连已获美方许可的 H20/H200 也在排除之列（[GPUSmith](https://gpusmith.com/articles/en/nvidia-gpu-export-restrictions)）。

结果是 NVIDIA 在中国这个曾经占其收入 13%（FY2025 约 170 亿美元）的市场份额从制裁前峰值 95% 跌至不足 60%，黄仁勋公开表示中国市场份份额"从 95% 跌到零"（先进产品口径），Q3 FY27 指引完全不假设中国数据中心计算收入（[GPUSmith](https://gpusmith.com/articles/en/nvidia-gpu-export-restrictions)；[Fortune](https://fortune.com/2025/10/29/nvidia-first-5-trillion-company-ceo-jensen-huang-500-billion-revenue-blackwell-rubin-gpus-china/)；[NVIDIA](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027)）。加速器市场正在事实上分裂为两个拥有独立供应链与独立清算文法的平行市场——这正是原报告情景树中那条"政策分隔"虚线分支的现实化。

### 8.2 国产阵营：华为的全栈对赌与寒武纪的万亿市值

华为 2025 年 9 月 18 日首次公开三年昇腾路线图：910C（2025）→ 950PR/950DT（2026 年 Q1/Q4）→ 960（2027 Q4）→ 970（2028 Q4）。950PR 单芯片 FP8 1 PFLOPS/FP4 2 PFLOPS、144GB 自研 HBM（HiBL 1.0）、4TB/s 带宽；950DT 用 HiZQ 内存面向解码与训练——从 950 代起华为全面切换自研 HBM，摆脱对韩系内存的依赖（[Tom's Hardware](https://www.tomshardware.com/tech-industry/semiconductors/huawei-unveils-ascend-roadmap-backed-by-in-house-hbm)；[Convequity](https://convequity.substack.com/p/huawei-ascend-ai-chip-roadmap-and)）。单芯片层面，950 大致对标 Hopper、960 对标 Blackwell、970 瞄准 Rubin+；华为的对赌是把单芯片劣势用系统级互联补回来——Atlas SuperPoD 2027 年将扩展至 15488 卡，以集群总算力对抗 NVIDIA 的单卡优势（[X/ruima](https://x.com/ruima/status/1968592824380878931)；[Convequity](https://convequity.substack.com/p/huawei-ascend-ai-chip-roadmap-and)）。

二级市场已经给出定价：寒武纪 2025 年收入 65 亿元（同比 +453%）并首次全年盈利，2026 年 Q1 收入 28.8 亿元（同比 +159.6%）、净利 10.1 亿元（同比 +185%），6 月 30 日市值突破 **1 万亿元人民币**，成为中国首家万亿级 AI 芯片公司；公司 2026 年出货目标 50 万颗（2025 年约 11.6 万颗），最大瓶颈是中芯国际 7nm 级产能（良率据报道约 20%）（[Yahoo Finance](https://finance.yahoo.com/sectors/technology/articles/chinese-gpu-maker-cambricons-q1-103000723.html)；[X/TechBuzzChina](https://x.com/TechBuzzChina/status/2072170682390036491)；[SCMP](https://www.scmp.com/tech/article/3362223/chinese-ai-chip-giant-cambricon-sets-us148b-revenue-goal-tied-staff-incentive-plan)）。2026 上半年整个国产阵营爆发：海光收入破 90 亿元、壁仞同比增长近 20 倍、摩尔线程半年超去年全年——但经营性现金流普遍恶化、库存激增，行业面临"确定的 demand 与不确定的 supply"悖论，百万颗级产能缺口预计让供给紧张持续至少 24 个月（[BigGo](https://finance.biggo.com/news/3f45dd95-9fda-45e1-bf43-6290b9fbaa22)）。IDC 数据显示，中国厂商 2025 年交付 165 万颗 AI GPU、占国内 AI 服务器市场 41%（[Yahoo Finance](https://finance.yahoo.com/sectors/technology/articles/chinese-gpu-maker-cambricons-q1-103000723.html)）。

---

## 九、创业公司的清算文法：从 Cerebras 到 Groq

### 9.1 同一枚硬币的两面

2025 年 12 月 24 日的 Groq 交易与 2026 年 5 月 14 日的 Cerebras IPO，构成了 AI 芯片创业公司退出路径的光谱两极。Groq 端：NVIDIA 以约 **200 亿美元现金**（CNBC 报道口径，公司未确认）获得其推理技术的永久非独家授权，创始人 Jonathan Ross、总裁 Sunny Madra 及核心工程团队加入 NVIDIA，Groq 作为独立实体保留 GroqCloud 继续运营——一宗被分析师称为"反向人才收购"（reverse acqui-hire）的交易，结构上规避了正式并购的反垄断审查；交易后 Groq 估值从 2025 年 9 月的 69 亿美元降至 2026 年 8 月的 35 亿美元（[InferenceChips](https://www.inferencechips.com/companies/groq/)；[More Than Moore](https://morethanmoore.substack.com/p/ho-ho-ho-groq-nvidia-is-a-gift)；[Groq](https://groq.com/newsroom/groq-and-nvidia-enter-non-exclusive-inference-technology-licensing-agreement-to-accelerate-ai-inference-at-global-scale)）。Groq 花近十年建立的架构，最终以"NVIDIA Groq 3 LPU"的身份由别人量产——这是非 GPU 商用推理架构商业化难度的标志性案例。

Cerebras 端则是创业硅片罕见的公开市场胜利：2026 年 5 月 14 日以 185 美元/股登陆纳斯达克（代码 CBRS），募资约 55 亿美元，首日上涨 108%，估值从 3 月 S-1 申报时的 336 亿美元升至近 500 亿美元（[Cerebras](https://www.cerebras.ai/cbrs)；[Morningstar](https://www.morningstar.com/stocks/why-ai-chip-designer-cerebras-is-2026s-hottest-ipo-yet)）。支撑 IPO 的是 2026 年 1 月与 OpenAI 签订的多年期、超 **200 亿美元** 算力协议——OpenAI 将部署 750MW 的 Cerebras 高速推理算力（[SEC S-1](https://www.sec.gov/Archives/edgar/data/2021728/000162828026025762/cerebras-sx1april2026.htm)）。两条路径的共同底色是：**活下来并卖得贵的，都是绑定了前沿实验室真实 workloads 的公司；卖不掉的，不是死于硅片，而是死于工具链**。

### 9.2 历史的韵脚：FPGA 与光通信周期

原报告（《Forty-Two Years of Inference Silicon》）最有价值的贡献，是把本轮周期放进 42 年的清算文法里比较，本报告继承这一框架并更新其数据。两个历史锚点值得反复引用：其一，2000–2001 年光通信泡沫中，Xilinx 收入从 1996 年的 5.6 亿美元增至 2001 财年的 16.59 亿美元、Altera 从 1995 年 4.02 亿美元增至 2000 年 13.77 亿美元，随后双寡头合计收入单年回撤约 **-39%**——需求是真的（互联网流量年翻倍），错误在于把 S 曲线外推成直线（原报告 K17–K18）。其二，FPGA 双寡头的最终清算都是"奖励式"的：Altera 2015 年以 167 亿美元售予 Intel，Xilinx 2022 年以约 490 亿美元并入 AMD；而 Intel 对 Altera 的十年持有以 2025 年 9 月向 Silver Lake 出售 51% 股权（估值 87.5 亿美元，较买入价近乎腰斩）告终——同一资产类别，一次短缺超级周期之间，定价相差近三倍（[Intel](https://www.intc.com/news-events/press-releases/detail/1736/intel-announces-strategic-investment-by-silver-lake-in)；[Reuters](https://www.reuters.com/markets/deals/intel-sell-51-stake-altera-silver-lake-2025-04-14/)；[Altera](https://www.altera.com/newsroom/altera-silver-lake)）。

清算文法的当代版本已经写在 Groq、Graphcore（2024 年约 6 亿美元售予软银）、Habana（2019 年 20 亿美元售予 Intel）、Nervana（约 3.5 亿美元被 Intel 收购后产品线解散）与 Cerebras 的路径分叉里：**没有一家重要公司死于破产清算；输掉的工具链被折叠进赢家组合，是唯一的历史规律**。2026 年需要盯防的新变量是"授权+人才"式清算（Groq 模式）——它在监管灰色地带创造了一种比并购更快、比破产更体面的出清方式，且几乎肯定会被复制。

---

## 十、情景框架与监测触发器

### 10.1 两条路径与一个 kill switch

**基准情景（延续）**：加速器支出沿 AMD"2028 年 TAM 超 5000 亿美元"的公司口径路径扩张，定制硅片美元份额从 2025 年约 12% 升至 2028 年约 20%——对应定制硅片加速器收入约 **2.5 倍** 的增长（区间 2.0–4.7 倍，方法论沿用原报告的双因子乘法：支出倍数 × 份额倍数）。支撑证据：四大云厂商 2026 年指引已落地约 7250 亿美元且仍在逐季上修；Broadcom FY2028 年 AI 收入 2300 亿美元的公司目标与 J.P. Morgan"ASIC 市场 2026 年约 600–700 亿美元、CAGR 40–50%"的独立估计相互印证（[AlphaSense](https://www.alpha-sense.com/earnings/avgo/)；[Webull](https://www.webull.com/news/15613772749751296)）。**收缩情景（清算）**：若 2027 年指引增速跌破约 +15%，则触发 2001 年文法——出清以减记、并购与授权交易而非破产完成，库存修正首先落在闸门环节（HBM 长协与 CoWoS 预订的不可取消条款会放大波动）。

两条情景共享同一个无法定价的虚线分支：**政策分隔**。中国市场已在事实上与全球市场脱钩（NVIDIA 指引不含中国、华为自研 HBM、寒武纪万亿市值），若分隔固化，两个情景中的 TAM 都要永久性扣减一块（[GPUSmith](https://gpusmith.com/articles/en/nvidia-gpu-export-restrictions)）。所有场景乘法都必须使用相容的分母——加速器美元乘以加速器份额；原报告曾撤回"总资本开支 × 定制份额"的错误链（分母不相容），这一教训本报告原样继承：任何把建筑物、土地、电力与通用服务器的美元混进加速器份额乘法的模型，结论一律作废。

### 10.2 八个可证伪触发器（截至 2026-10-19 的时点台账）

下表把全部论证压缩为可季度复核的仪器表。每个触发器都写成"杀死论点"而非"讨好论点"的形式，读数均来自本报告引用来源：

| # | 触发器 | 证伪条件 | 当前读数（2026-10） | 下一观察窗 |
|---|---|---|---|---|
| 1 | 四大云厂商资本开支指引 | 2027E 增速 < +15% → 基准情景作废 | 2026E 约 +77%；Evercore/BofA 预计 2027 破 1 万亿（[AI Weekly](https://aiweekly.co/alerts/amazon-microsoft-alphabet-meta-plan-725b-ai-capex-in-2026)） | 2027 年 1–2 月财报季 |
| 2 | NVIDIA 数据中心增速 | 连续两季 < +20% | Q2FY27 +117%，Q3 指引隐含约 +60%+（[NVIDIA](https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-second-quarter-fiscal-2027)） | 2026 年 11 月财报 |
| 3 | HBM 价格 | HBM3E/HBM4 ASP 环比转跌 > 15% | 反向：2027 合约价较现价涨 3 倍，混合 ASP 预计 +121%（[BigGo](https://finance.biggo.com/news/005d09f6-60ed-41cc-99e7-f81919b78e7d)） | 2027 年合约谈判季 |
| 4 | CoWoS 利用率 | 跌破 85% / 交期显著缩短 | 满载，缺口约 20%→10%（[TrendForce](https://www.trendforce.com/news/2026/06/15/news-tsmc-cowos-supply-demand-gap-reportedly-seen-narrowing-from-20-to-10-by-end-2026-as-capacity-expands/)） | 季度供应链追踪 |
| 5 | 定制硅片美元份额 | 2027 统计中 < 15% | JPM：ASIC 出货份额 2027 年 54%；美元口径显著更低（[Webull](https://www.webull.com/news/15613772749751296)） | 券商年度模型更新 |
| 6 | TPU 出货收敛 | 独立估计收敛至 < 800 万颗/年 | Counterpoint：Google 2027 年占 ASIC 出货 52%（[Counterpoint](https://counterpointresearch.com/en/insights/AI-Server-Compute-ASIC-Shipments-to-Triple-by-2027)） | 供应链拆解 |
| 7 | 电网并网 | 吉瓦级审批连续两季停滞 | ERCOT 排队 438GW+，热点区域等 4–7 年（[Forbes](https://www.forbes.com/sites/guneyyildiz/2026/06/30/the-energy-transition-just-hit-the-wall-ai-compute-cannot-ignore/)） | 月度互联队列数据 |
| 8 | 定制 vs 商用美元拆分的披露缺口 | 仍无云厂商披露 → 维持"不可裁判"状态 | 缺口依旧；Anthropic–Google/Broadcom 多 GW 协议是间接证据（[Anthropic](https://www.anthropic.com/news/google-broadcom-partnership-compute)） | 持续 |

当前组合读数：**1 项确认**（HBM 售罄与涨价，供给挤压成立的成熟信号）、**7 项建设中/部分**、**0 项缺失**——对一轮年轻周期而言，"确认数少"本身是正确状态，因为确认是成熟挤压才具有的属性。触发器 1 是全表的 kill switch：它的证伪条件不是叙事，而是算术——低于 +15% 的增速使基准情景的支出路径在数学上不可达。

---

## 十一、结论

四十年的产业史只教一件事：**周期反复的是机制，变化的是约束的位置**。1985 年 FPGA 以"更好的采购决策"战胜门阵列；2001 年光通信以 -39% 的单年回撤示范了订单文法的破坏力；2019–2022 年短缺周期用 NCNR 订单演示了"每个买家理性、总体不稳定"的库存生成机制；2023–2026 年，同一副骨架在十倍的美元上重演——只是约束从晶圆厂迁移到了内存、封装与电网，清算方式从并购升级到了"授权+人才"。NVIDIA 的 20.8 倍数据中心收入增长、四大云厂商 7250 亿美元的年度资本开支、HBM 三倍的单代涨价、台积电"封装限制客户增长"的直言，都是真实的；OpenAI 收入口径的 200 亿美元"更正"、中国市场的政策性脱钩、以及电网 4–7 年的审批时钟，同样是真实的。

对产业参与者，本报告的建议与其方法论一致：**盯闸门，不盯头条**。HBM 合约价、CoWoS 交期、资本开支指引修正、并网队列，这四组数据的拐点会领先任何叙事拐点一到两个季度出现。对投资者，利润池的假设是"税基在云厂商、征税权在闸门"——产能不可在本周期时钟内复制的环节（HBM 良率学习曲线、台积电的节点领先与封装产能、SerDes/光 DSP 的 IP 积累、以及绑定了前沿实验室 workload 的 ASIC 设计伙伴关系）拥有本轮周期最持久的定价权；但该假设仍缺两年的分部毛利与 ROIC 披露来最终证实，应以触发器 1、3、4 作为先行裁判。

---

**免责声明**：本报告基于公开信息编制，所引数据均来自标注来源，预测性陈述（含情景倍数与触发器阈值）属于分析框架而非投资建议。半导体与 AI 产业具有高波动性与政策不确定性，任何投资决策应咨询持牌专业人士。本报告仅供一般信息参考，不构成证券推荐、要约或财务、法律、税务意见。
