---
title: "CascadeMAP: Autonomous Closed-loop Optimization of Enzyme Cascades via Microfluidics, Machine Learning and Agentic AI"
title_zh: CascadeMAP：基于微流控、机器学习和自主AI的酶级联反应自主闭环优化
authors: "Vasina, M., Kovar, D., Kizovsky, M., Lacko, D., Vanacek, P., Herich, M., Volf, E., Drdla, L., Cabalova, S., Sikorova, P., Jirasek, M., Solansky, P., Jezek, J., Samek, O., Dousek, F., Walner, H., Zemanek, P., deMello, A., Pilat, Z., Damborsky, J., Stavrakis, S., Mazurenko, S., Prokop, Z."
date: 2026-06-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.730034v1.full.pdf"
tags: ["query:agent-lsh"]
score: 7.0
evidence: 多智能体AI自主闭环优化酶级联反应
tldr: 酶级联反应优化面临高维参数空间挑战，CascadeMAP平台集成微流控、贝叶斯优化与多智能体AI系统，实现7天无值守运行，处理约22万反应。在荧光和拉曼两种检测模式下，优化速度比传统实验设计快3倍，为生物催化路径自主优化提供通用框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 酶级联反应优化需探索大量参数组合，传统方法耗时耗力，亟需自动化闭环优化平台。
method: 结合高通量微流控、贝叶斯优化算法与多智能体AI系统，自主实验设计、执行与分析。
result: 7天内处理约22万反应，贝叶斯优化比实验设计快3倍，AI处理11GB数据并生成假说。
conclusion: CascadeMAP实现酶级联反应的自主优化，加速生物催化与合成生物学发展。
---

## 摘要
酶级联反应能够实现复杂的生物化学转化，但其优化过程资源密集，需要在包含反应条件、酶比例和缓冲液组成的高维参数空间中进行导航。本文介绍了CascadeMAP，一个用于酶级联反应闭环优化的自主微流控平台，该平台将高通量微流控技术与贝叶斯优化及多智能体AI系统相结合。我们通过两个级联反应演示了该平台：（i）由荧光监测的甘油检测途径，以及（ii）由无标记拉曼光谱监测的1,2,3-三氯丙烷降解途径，提供了正交检测模式。贝叶斯优化比实验设计快三倍找到最佳条件。多智能体AI系统自动进行假设生成，处理了11 GB的实验数据、模式识别和洞察综合。CascadeMAP在无需人工干预的情况下运行了7天，在约7,400种不同条件下处理了约220,000次反应。这一能力为酶级联反应和代谢途径的自主优化建立了一个可推广的框架，并加速了生物催化和合成生物系统的发展。

## Abstract
Enzyme cascades enable complex biochemical transformations, but their optimization is resource-intensive, requiring navigation through high-dimensional parameter spaces encompassing reaction conditions, enzyme ratios, and buffer composition. Here we introduce CascadeMAP, an autonomous microfluidic platform for closed-loop optimization of enzyme cascades, integrating high-throughput microfluidics with Bayesian optimization and multi-agent AI system. We demonstrate the platform across two cascades: (i) a glycerol detection pathway monitored by fluorescence and (ii) a 1,2,3-trichloropropane degradation pathway monitored by label-free Raman spectroscopy providing orthogonal detection modalities. Bayesian optimization identified optimal conditions three times faster than Design of Experiments. Multi-agent AI system automated hypothesis generation, processing 11 GB of experimental data, pattern recognition, and insight synthesis. Operating without human intervention for 7 days, CascadeMAP processed [~]220,000 reactions across [~]7,400 different conditions. This capability establishes a generalizable framework for the autonomous optimization of enzyme cascades and metabolic pathways and accelerates the development of biocatalytic and synthetic biological systems.