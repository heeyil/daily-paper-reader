---
title: "OmniGene-4: A Unified Bio-Language MoE Model with Router-Level Interpretability"
title_zh: OmniGene-4：一个具有路由器级别可解释性的统一生物语言MoE模型
authors: "Wang, L."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.12.724542v3.full.pdf"
tags: ["query:moe-routing"]
score: 6.0
evidence: 生物MoE模型中的路由器可解释性
tldr: "多模态大模型在回答生物序列问题时，其内部机制如同黑箱。OmniGene-4采用MoE架构，通过路由器状态分解发现：预训练贡献96%的跨任务专家分化，路由门负责选择模态，专家负责计算答案。模型在远程同源性上达82.60%，超越ESM-2等专用模型；扩展至视觉模态后仍保持同源性能力，且计算量降低四个数量级，实现了高性能、可解释且经济易复现的多模态生物基础模型。"
source: biorxiv
selection_source: fresh_fetch
motivation: 探索多模态大模型如何利用生物序列知识回答序列相关生物学问题，并实现模型内部机制的透明化。
method: 基于Gemma-4-26B-A4B构建MoE模型OmniGene-4，通过钩取路由器状态分析专家分化，并扩展视觉模态。
result: "远程同源性82.60%，标准99.40%，BixBench93.66%；多模态扩展保留同源性且计算量降低四个数量级。"
conclusion: 揭示了生物基础模型通过路由门选择模态、专家计算答案的机制，实现了高性能与可解释性。
---

## 摘要
多模态大语言模型如何联合处理自然语言和生物序列（DNA、蛋白质、结构字母表），并实际回答生物问题，尤其是那些基于残基层次模式而非文献回忆的序列接地问题？我们提出了OmniGene-4，一个基于Gemma-4-26B-A4B（每层128个专家，前8路由）的统一生物语言混合专家基础模型，并利用其离散路由器状态来剖析这一问题。通过跨八个任务族钩取每个路由器，我们首次提供了生物MoE的路由器级分解：持续预训练（CPT）占跨任务专家差异化的96%，监督微调（SFT）占4%，分别重塑中间层和输出层。在蛋白质同源任务族内，每对路由差异低于0.04（跨任务为0.23），这表明序列接地决策发生在专家计算内部而非门控处——门控选择模态，专家计算答案。该流程取得了强有力的基准：远程同源性82.60%（优于ESM-2 3B、MMseqs2、DIAMOND 28-31个百分点）；标准同源性99.40%；BixBench（通用生物学知识）93.66%。一种双头架构增加了每个残基的3Di/DSSP分类器（78.6%/100%）。为了探究所发现的迁移机制在模态扩展下是否鲁棒，我们进一步将模型扩展到OmniGene-4-MM，通过视觉塔和三阶段LoRA流程（总计1.5 GPU天）添加了四种视觉模态（化学结构图像、医学/病理图像、图表）。多模态模型保持了同源能力（标准85%，远程69.5%），并获得了化学家可读的结构理解（Vis-CheBI20功能组标注96%），同时消耗的计算量约为近期专用MoE生物模型的四个数量级。该工作描述了多模态生物基础模型如何获取、路由和保留序列感知能力——这对下一代科学大语言模型至关重要。

## Abstract
How do multi-modal large language models that jointly process natural language and biological sequences (DNA, protein, structural alphabets) actually answer biological questions, especially sequence-grounded questions whose answer depends on residue-level patterns rather than literature recall? We introduce OmniGene-4, a unified bio-language Mixture-of-Experts foundation model on Gemma-4-26B-A4B (128 experts/layer, top-8 routing), and use its discrete router state to dissect this question. By hooking every router across eight task families, we provide the first router-level decomposition for a biological MoE: continued pretraining (CPT) accounts for 96% of cross-task expert differentiation and supervised fine-tuning (SFT) for 4%, reshaping middle and output layers respectively. Within the protein-homology task family, per-pair routing divergence stays below 0.04 (vs 0.23 cross-task), implying that sequence-grounded decisions occur inside expert computation rather than at the gate -- the gate selects the modality, the experts compute the answer. The pipeline yields strong benchmarks: remote-homology 82.60% (vs ESM-2 3B, MMseqs2, DIAMOND by 28-31 pp); standard homology 99.40%; BixBench (general biological-knowledge) 93.66%. A dual-head architecture adds per-residue 3Di/DSSP classifiers (78.6%/100%). To probe whether the discovered transfer mechanism is robust under modality scaling, we further extend the model to OmniGene-4-MM, adding four vision modalities (chemical-structure images, medical/pathology imagery, charts) via a vision tower and a three-stage LoRA pipeline at 1.5 GPU-days total. The multi-modal model preserves the homology capability (85% standard, 69.5% remote) and acquires chemist-readable structure understanding (96% on Vis-CheBI20 functional-group captioning) while consuming roughly four orders of magnitude less compute than recent specialized MoE bio-models. The work characterizes how multi-modal bio-foundation models acquire, route, and preserve sequence-aware capability -- central to the next generation of scientific large language models.

O_TEXTBOXThe bigger picture.

Modern AI models that read both human language and biological sequences (DNA, proteins) often behave like black boxes: we see their answers but not the inner mechanism that produced them. This matters for biology, where a wrong but confidently worded answer can mislead an experiment that costs months and tens of thousands of dollars. We use Mixture-of-Experts architecture -- a transformer where each token is routed to a small subset of 128 specialized sub-networks at every layer -- to make this internal mechanism legible. By logging which experts are activated for each input, we show that adding biology-specific pre-training to a general-purpose language model causes the routing to spontaneously partition the network into modality-specific sub-networks, and that the same partitioning re-emerges when we further extend the model to also process molecular images, medical images, and chart images. The same model achieves protein-homology accuracy that surpasses classical sequence-alignment tools (MMseqs2, DIAMOND) and recent protein language models (ESM-2 3B), at roughly four orders of magnitude less compute than recent specialized MoE bio-models. The work is a step toward foundation models for biology that are simultaneously broad in modality coverage, mechanistically transparent, and economically reproducible by groups outside the largest industrial labs.

C_TEXTBOX