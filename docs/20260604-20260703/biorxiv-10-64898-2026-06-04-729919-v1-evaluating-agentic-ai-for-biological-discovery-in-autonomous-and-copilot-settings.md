---
title: Evaluating agentic AI for biological discovery in autonomous and copilot settings
title_zh: 评估自主与副驾驶模式下用于生物发现的智能体AI
authors: "Johri, S., Pimenta, E. M., Yates, J., Fu, J., Bao, E. L., Jun, H., Reardon, B., Bacot, S., Shady, M., Fu, D., Mei, W., Camp, S. Y., Park, J., Van Allen, E."
date: 2026-06-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.729919v1.full.pdf"
tags: ["query:agent-lsh"]
score: 6.0
evidence: 评估智能体AI在复杂生物数据环境中的发现能力
tldr: 现有基于大语言模型的AI代理能执行标准生物信息学流程，但生物发现往往需要开放假设生成和迭代推理，尤其在多组学研究中。我们开发了多步多模态多组学代理（M3A）框架，在11种癌症类型的单细胞多组学数据上系统评估了AI代理在自主和人机协同场景下的能力。结果显示，AI代理擅长广泛系统性数据探索，而人类专家在方法论指导和跨分析生物综合方面仍不可或缺。本工作界定了当前AI代理在计算生物学中的潜力与边界，并为评估支持生物发现的AI系统提供了框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 评估AI代理在生物发现中自动化开放科学发现的能力与局限，特别是应对多组学数据的异质性和噪声。
method: 开发M3A框架，在11种癌症类型的多模态单细胞数据集上，评估自主细胞注释、基因程序假设生成及人机协同实验。
result: AI代理在广泛系统性探索中有效，但人类专家在方法指导和跨分析生物综合中仍为关键。
conclusion: 揭示了当前AI代理在计算生物学中的潜力和边界，建立了评估支持生物发现的AI系统的框架。
---

## 摘要
基于大型语言模型的人工智能智能体在执行结构化分析工作流程（包括用于生物发现的标准生物信息学流程）方面的能力已有所提升。然而，计算生物学很少仅由确定性流程执行组成。生物数据集具有异质性和噪声性，有意义的发现通常需要开放式的假设生成和对多模态证据的迭代推理。这些挑战在多组学研究中尤为明显，其中配对的分子模态和异质性临床背景为发现创造了机遇和障碍。新兴的智能体AI系统在多大程度上能够支持或自动化这种科学发现模式仍不甚明了。在此，我们利用涵盖11种癌症类型的多组学单细胞数据集，系统评估了智能体AI在生物发现中的能力与局限性。我们开发了多步骤多模态多组学智能体框架，以支持LLM驱动的对持久多模态数据状态的推理，并在自主和人机协同（副驾驶）设置中捕捉智能体推理行为。利用该框架，我们评估了AI智能体在互补任务上的表现，包括自主细胞类型注释、从基因程序生成可证伪的生物假设，以及测试人类参与和领域专业知识影响的副驾驶实验。我们发现，当前AI智能体擅长对复杂数据进行广泛、系统性的探索，而领域专家在跨分析的方法学指导和生物学综合中仍然至关重要。总之，我们的研究结果描绘了智能体AI在计算生物学中的当前潜力与边界，并建立了评估旨在支持生物发现的AI系统的框架。

## Abstract
Advances in large language models (LLMs)-based artificial intelligence (AI) agents have improved their ability to execute structured analytical workflows, including standard bioinformatic pipelines for biological discovery. However, computational biology rarely consists of deterministic pipeline execution alone. Biological datasets are heterogeneous and noisy, and meaningful discovery often requires open-ended hypothesis generation and iterative reasoning over multimodal evidence. These challenges are particularly evident in multi-omic studies, where paired molecular modalities and heterogeneous clinical contexts create both opportunities and obstacles for discovery. The extent to which emerging agentic AI systems can support or automate this mode of scientific discovery remains poorly understood. Here, we systematically evaluated the capabilities and limitations of agentic AI for biological discovery using multi-omic single cell datasets spanning 11 cancer types. We developed the Multistep Multimodal Multiomic Agentic (M3A) Framework to support LLM-driven reasoning over persistent multimodal data states and to capture agentic reasoning behavior in autonomous and human-AI copilot settings. Using this framework, we assessed AI agents across complementary tasks, including autonomous cell-type annotation, generation of falsifiable biological hypotheses from gene programs, and copilot experiments testing the effect of human involvement and domain expertise. We found that current AI agents are effective at broad, systemic exploration of complex data, whereas domain experts remain critical for methodological guidance and biological synthesis across analyses. Together, our results delineate the current potential and boundaries of agentic AI in computational biology, and establish a framework for evaluating AI systems designed to support biological discovery.