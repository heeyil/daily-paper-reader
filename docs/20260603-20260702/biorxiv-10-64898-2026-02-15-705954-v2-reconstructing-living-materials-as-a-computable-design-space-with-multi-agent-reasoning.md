---
title: Reconstructing living materials as a computable design space with multi-agent reasoning
title_zh: 基于多智能体推理将活体材料重构为可计算的设计空间
authors: "Xiao, Y., Zeng, X., Yang, Z., Gu, J., Lu, Y., Wang, Y., Wen, H., Chen, M., Huang, Z., Hu, J., Liu, J., Sha, C., Xie, J., Li, H., Zhu, X., Zheng, S., Zhang, J., Zong, W., He, Z., Xu, Y., Zhou, X., Li, F., Liu, H., He, Q., Liu, L., Yu, Z."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.15.705954v2.full.pdf"
tags: ["query:agent-lsh"]
score: 7.0
evidence: 多智能体推理框架用于复杂科学发现
tldr: 活体材料因细胞、基质、工艺和评估条件间的上下文依赖耦合，其设计空间计算建模极具挑战。LiveMat多智能体推理框架将非结构化文献转化为可计算空间，标准化34215条记录并构建知识图谱。通过约束分解、来源感知提取、一致性与专家排名，克服跨域特征集成瓶颈。在伤口愈合任务中优先选出体内性能最先进的设计，为可解释、证据驱动的活体材料发现奠定基础。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI框架局限于分子或蛋白空间，活体材料因上下文依赖耦合而难以计算化，需要新方法将非结构化文献转化为可设计空间。
method: LiveMat多智能体框架通过约束分解、来源感知提取、一致性检查及专家锚定排名，将文献标准化为包含微生物、聚合物和性能指标的知识图谱。
result: 在伤口愈合任务中，LiveMat优先推荐的四组分设计在体内实验中达到最先进性能，证明其可发现高性能活体材料。
conclusion: 建立了可解释、证据驱动的活体材料发现基础设施，为跨域复杂材料系统提供可扩展计算设计范式。
---

## 摘要
人工智能正越来越多地用于加速科学发现，但大多数成功的框架仅在定义明确的分子、蛋白质或材料空间内运行。活体材料提出了更具挑战性的计算问题，因为其功能源于细胞、基质、制造工艺和评估条件之间依赖于环境的耦合。在此，我们介绍LiveMat，一个多智能体推理框架，它将非结构化的文献转化为活体材料的可计算设计空间。LiveMat标准化了34,215条活体材料记录，将16,769条微生物条目和17,446条聚合物条目整合到一个知识图谱中，该图谱连接了活体组分、非生物基质、功能输出、评估环境及性能指标。在五个大语言模型上的基准测试表明，活体材料推理的主要限制在于跨领域特征集成，而非粗粒度分类。LiveMat通过约束分解、来源感知提取、一致性检查和专家锚定排名克服了这一限制。在一项前瞻性的伤口愈合任务中，它优先选择了具有最先进体内性能的四组分设计，为可解释、有证据依据的活体材料发现建立了可扩展的基础设施。

## Abstract
Artificial intelligence is increasingly used to accelerate scientific discovery, but most successful frameworks operate within well-defined molecular, protein or materials spaces. Living materials present a more formidable computational problem because functions emerge from context dependent coupling among cells, matrices, fabrication processes and evaluation conditions. Here we introduce LiveMat, a multi-agent reasoning framework that transforms unstructured literature into a computable design space for living materials. LiveMat standardizes 34,215 living material records, integrating 16,769 microorganism and 17,446 polymer entries into a knowledge graph linking living components, abiotic matrices, functional outputs, evaluation contexts and performance metrics. Benchmarking across five large language models shows that living material reasoning is limited mainly by cross-domain feature integration rather than coarse classification. LiveMat overcomes this limitation through constraint decomposition, provenance-aware extraction, consistency checking and expert-anchored ranking. In a prospective wound-healing task, it prioritizes a four-component design with state-of-the-art in vivo performance, establishing a scalable infrastructure for interpretable, evidence-grounded living material discovery.