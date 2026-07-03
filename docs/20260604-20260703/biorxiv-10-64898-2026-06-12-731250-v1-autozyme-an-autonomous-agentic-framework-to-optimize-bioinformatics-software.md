---
title: "AutoZyme: An Autonomous Agentic Framework to Optimize Bioinformatics Software"
title_zh: AutoZyme：一种自主智能体框架，用于优化生物信息学软件
authors: "Xie, E., Cheng, L., Cai, Y., Shireman, J., Kendziorski, C."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731250v1.full.pdf"
tags: ["query:agent-lsh"]
score: 8.0
evidence: 自主代理随时间迭代改进代码
tldr: "基因组学和生物信息学软件随着数据规模增大出现性能瓶颈，人工优化难以扩展。为此提出AutoZyme智能体框架，自动构建基准、识别瓶颈并迭代优化代码。在45个函数测试中，超过95%实现运行时间提升，其中38个函数中位数加速8.52倍，最大超676倍。优化函数以即插即用方式通过AutoZyme-Library分发，为科学软件优化提供可复用的自动化方案。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有生物信息学软件性能优化依赖专家手动，难以扩展至大规模软件栈。
method: AutoZyme通过代理自动构建基准测试、分析瓶颈并迭代应用代码变更，保留有效优化。
result: "在45个函数中95%以上提升性能，38个函数中位数加速8.52倍，最大676倍。"
conclusion: AutoZyme作为可复用框架，通过优化函数库实现即插即用，显著降低生物信息学软件优化门槛。
---

## 摘要
随着生物数据集在大小和数量上的持续增长，广泛使用的基因组学和生物信息学软件中的性能瓶颈带来了日益沉重的负担。缓解这些瓶颈主要依赖专家的手动优化，因此难以规模化。在此，我们提出AutoZyme，一个用于科学软件优化的智能体框架。给定一个目标函数，AutoZyme构建基准测试、识别瓶颈并迭代测试代码更改，仅保留那些能提高运行时间且保持输出的更改。我们在45个函数上评估了AutoZyme，在超过95%的情况下提高了运行时间且未显著增加内存消耗。针对来自Seurat、Scanpy及基因组学和生物信息学相关包的38个函数，AutoZyme将运行时间中位数降低了8.52倍，最大降低超过676倍。优化后的函数通过AutoZyme-Library作为现有分析管线的即插即用替代方案分发。我们还发布了AutoZyme作为一个可重用的框架，用于优化用户指定的其他包和函数。

## Abstract
Performance bottlenecks in widely used genomics and bioinformatics software present a substantial and growing burden as biological datasets continue to increase in size and number. Relieving these bottlenecks relies largely on expert manual optimization and therefore remains difficult to scale. Here we present AutoZyme, an agentic framework for scientific software optimization. Given a target function, AutoZyme builds benchmarks, identifies bottlenecks, and iteratively tests code changes, retaining only those that improve runtime while preserving output. We evaluated AutoZyme on 45 functions, improving runtime without substantial memory increases in over 95% of cases considered. Across 38 functions from Seurat, Scanpy and related packages in genomics and bioinformatics, AutoZyme reduced runtime by a median of 8.52-fold, with the largest reductions exceeding 676-fold. The optimized functions are distributed through AutoZyme-Library as drop-in replacements for existing analysis pipelines. We also release AutoZyme as a reusable framework for optimizing additional user-specified packages and functions.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：广泛使用的基因组学和生物信息学软件（如Seurat、Scanpy）存在大量性能瓶颈（运行慢、内存高、无法扩展），且随着生物数据集规模持续增长，问题日益严重。作者手动审计了18个常用工具，发现468个性能相关投诉，其中104个长期未解决（中位年龄约2年），表明瓶颈是**长期维护负担**。
- **现有方法不足**：
  - 手动优化（重写、编译内核）依赖专家，难以规模化。
  - 后端替换库（如BPCells）需大量适配，可能改变执行路径。
  - GPU加速（如rapids-singlecell）依赖专用硬件，与现有CPU工作流不兼容。
  - 直接使用LLM编码智能体易导致“agent hacking”（改变语义、过拟合）或需要大量人工干预。
- **整体含义**：需要一种可扩展、自动化、能保证输出一致性的软件优化方法。

---

### 2. 论文提出的方法论：核心思想、关键技术细节

- **框架名称**：AutoZyme，基于多智能体（multi-agent）的大语言模型（LLM）框架。
- **核心思想**：将优化分解为多个确定性/推理步骤，由5个主智能体 + 1个审计智能体协作完成，并由`zyme`命令行工具处理所有可重复的确定性操作，减少agent幻觉和hacking风险。
- **关键技术细节**：
  1. **Task Setup智能体**：接收目标GitHub仓库和函数，创建版本控制的任务目录。
  2. **Benchmark Initialization智能体**：
     - 识别优化函数，获取不同规模数据集（小、中、大）。
     - 运行函数建立基线结果，估计噪声，设定**一致性门（concordance gates）**：输出结构门、连续结果门（Spearman/ Pearson + 逐点漂移）、决策结果门（Jaccard、召回率）。
     - 对函数进行性能分析，提出前3个候选优化方向。
  3. **Optimization智能体**：
     - 根据候选方向提出具体补丁（patch），通过`zyme run`执行完整基准测试。
     - 若补丁通过一致性门、运行时改善超过噪声水平、内存未显著增加，则接受；否则拒绝并回滚。
     - 迭代最多50轮。
     - 遵循“阿姆达尔优先并行纪律”：先优化串行路径，再添加并行。
  4. **Validation智能体**：
     - 使用两个额外的独立数据集（OOD-large, OOD-xlarge），在1、4、8线程下测试。
     - 检查加速比是否保持（与开发加速比比较），以及线程行为是否合理。
     - 失败则返回优化智能体（最多30轮修复）。
  5. **Packaging智能体**：将验证通过的优化转换为可安装的补丁（R/Python包），保持原始公共API。
  6. **Auditor智能体**：在基准初始化后和优化后独立审核，查找agent hacking模式（如修改基准、绕过代码路径等）。高严重性发现需人工审查。
- **防止agent hacking的措施**：
  - `zyme` CLI强制执行冻结的基准和脚本，拒绝零改动、检查运行真实性、记录完整轨迹。
  - Auditor智能体只读审核。
- **输出优化历史**：每次接受的补丁及其基准证据均可追溯。

---

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - 基因组/生物信息学：PBMC 68K、PBMC 208K（青光眼）、Heart 486K、Tabula Muris Senis 110K、gastrulation 139K、SPLiT-seq 156K等。
  - 非生物领域：astropy、ObsPy、sarsen、xclim、FiPy、MDAnalysis、statsmodels。
  - 每个函数使用小、中、大三种规模数据集（开发集），外加两种验证集（OOD-large, OOD-xlarge）。
- **基准**：
  - 运行时（墙钟时间）、峰值内存、输出一致性度量（Spearman/Jaccard/漂移等）。
  - 对比的是**原始未优化代码**（相同输入、种子、线程、参数）。
- **对比方法**：没有与其他自动化优化工具进行直接比较，但文中提及了手动重写、BPCells、GPU框架作为背景，并解释了AutoZyme的优势。实验重点是与原始baseline的对比，以及跨函数、跨任务的泛化能力展示。
- **平台**：优化在MacBook Pro M3 Max 36GB上进行；评估在Windows工作站（AMD Ryzen 9 7950X, 16核, 32线程, 128GB DDR5）和MacBook Pro上，使用1、4、8线程（Windows为主报告平台）。

---

### 4. 资源与算力

- **LLM驱动**：使用Claude Code with Opus 4.7（可替换为其他编码智能体，如Codex、Cursor）。
- **硬件**：
  - 优化开发环境：MacBook Pro M3 Max, 36GB RAM。
  - 评估环境：Windows 11工作站（AMD Ryzen 9 7950X, 128GB DDR5）；未使用GPU。
- **未明确说明**：训练LLM的算力、优化每个函数的具体耗时（如调用LLM次数、总计算时间）。但文中提到优化轮次最多50轮，每轮运行基准测试。算力需求相对节制（CPU-only）。

---

### 5. 实验数量与充分性

- **优化函数数量**：45个函数（38个生物信息学 + 7个其他科学领域）。
- **生物信息学函数覆盖**：Seurat（8个函数，如FindAllMarkers、SCTransform）、Scanpy（7个函数）、CellChat、InferCNV、WGCNA、Slingshot、fgsea、NicheNet等。
- **实验维度**：
  - 每个函数在多个数据集（3个开发 + 2个验证）上测试。
  - 多个线程设置（1, 4, 8）。
  - Windows和Mac平台分别测试。
  - 输出一致性：每个函数都有明确的一致性门（如Spearman≥0.99、Jaccard≥0.95等）。
- **消融/机制分析**：将接受的补丁分类为5种优化机制（冗余去除、执行路径改变、内核工程等），并统计每种机制的速度贡献。
- **端到端工作流测试**：将一个完整Seurat分析（5个步骤）替换为优化版本，验证加速比（6.1倍）。
- **充分性与客观性**：
  - 实验覆盖多种主流工具和不同数据规模，具有代表性。
  - 所有比较均在相同条件下进行（种子、线程、参数、数据集）。
  - 审计机制防止agent hacking，结果可信。
  - 但缺少与其他自动化优化方法（如SWE-agent直接应用）的定量对比。

---

### 6. 论文的主要结论与发现

- **性能提升显著**：在45个函数中，超过95%的运行时间得到改善。对于38个生物信息学函数，运行时中位数降低8.52倍，最大降低超过676倍。
- **内存使用**：97.4%的优化函数（37/38）内存增加小于15%，部分函数内存也降低。
- **输出一致性**：89%的优化函数（40/45）输出与原始完全一致或漂移<0.6%，其余也在一致性门内。
- **通用性**：不仅适用于生物信息学，也适用于天文学、地震学、气候科学等其他科学领域（7个函数中位数加速9倍）。
- **可重用性**：优化函数通过AutoZyme-Library作为即插即用包发布；框架本身也可用于优化用户自定义函数。
- **优化机制发现**：主要贡献来自“冗余工作去除与重用”（最多补丁）和“内核工程”（最大加速贡献33.8%）；多数优化属于精确计算，而非数值松弛。

---

### 7. 优点：方法或实验设计上的亮点

1. **自动化与可扩展**：无需专家知识，自动完成基准构建、瓶颈定位、迭代优化和验证。
2. **防止agent hacking**：多重机制（冻结基准、zyme CLI强约束、独立Auditor）确保优化结果真实可靠。
3. **输出一致性保障**：通过一致性门（结构、连续值、决策）确保优化不改变语义，且能在噪声水平内评估。
4. **即插即用部署**：优化作为补丁包发布，保留原始API，用户无需修改分析流程。
5. **社区驱动扩展**：提供网站供用户请求和投票，优先解决高影响瓶颈。
6. **跨领域迁移**：展示了从生物信息学到其他科学计算的可移植性。
7. **优化轨迹可审计**：每次补丁的代码、基准证据、一致性结果均记录在版本控制中。

---

### 8. 不足与局限

- **缺乏与其他自动化方法的直接对比**：未与SWE-agent、GPT-Engineer等通用编码智能体在相同基准上比较，难以评估AutoZyme增量优势。
- **LLM依赖性**：优化质量受限于所使用LLM的能力；不同模型（如Claude Code vs. Codex）可能导致不同结果，但文中提到兼容性可能引入变异性。
- **仅限CPU优化**：未涉及GPU加速或分布式计算；对于本已使用GPU的工作流可能不适用。
- **验证范围有限**：虽然使用了OOD数据集和多线程测试，但未在不同操作系统、BLAS库、编译器版本等极端异质环境下验证稳定性。
- **长期维护风险**：优化补丁可能随着上游软件的更新（API改变）而失效，需要持续适配。
- **内存开销**：极少数优化函数（1/38）超过了15%的内存增加，未详细说明原因。
- **社区投诉审计的偏差**：手动审计可能遗漏部分投诉，且分类存在主观性（但作者使用了规则和LLM辅助筛选）。
- **未报告优化耗时**：框架运行每个函数需要多少LLM调用和计算时间未量化，不利于评估实际成本。

---

（完）
