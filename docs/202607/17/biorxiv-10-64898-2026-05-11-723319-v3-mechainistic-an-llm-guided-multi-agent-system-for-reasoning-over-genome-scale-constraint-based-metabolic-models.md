---
title: "MechAInistic: An LLM-guided Multi-Agent System for Reasoning over Genome-Scale Constraint-Based Metabolic Models"
authors: "Loecker, J., Pujara, N., Bryant, W., Puniya, B. L., Packrisamy, P., Hamed, A. A., Helikar, T."
date: 2026-07-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.11.723319v3.full.pdf"
tags: ["query:agent-lsh"]
score: 7.0
evidence: 包含规划与评审代理的多智能体科学推理系统
tldr: 针对LLM代理在科学推理中可能产生不可验证输出，提出MechAInistic多智能体系统。系统由独立配置的评审代理监督规划架构代理，所有推理基于可执行代谢模型分析而非纯文本。评审代理按预设标准评分并触发重规划，生成可审计的推理链，在基因组规模代谢模型推理中显著提高了可靠性。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1697, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1692, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 723, \"height\": 742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 906, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1661, \"height\": 861, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 864, \"height\": 736, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 683, \"height\": 340, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 971, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1705, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1555, \"height\": 561, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1712, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-05-11-723319-v3/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1715, \"height\": 871, \"label\": \"Table\"}]"
motivation: 包含规划与评审代理的多智能体科学推理系统。
method: 方法与实现细节请参考摘要与正文。
result: 结果与对比结论请参考摘要与正文。
conclusion: 总体而言，该工作在所述任务上展示了有效性，并提供了可复用的思路或工具。
---

## Abstract
LLM agents are increasingly used for scientific reasoning, but their fluent-sounding outputs can diverge from verifiable computational evidence, limiting their reliability for biomedical hypothesis generation. We developed MechAInistic, a multi-agent system in which an independently configured Reviewer agent supervises a planning Architect agent at each stage of the workflow, with all reasoning grounded in executable mechanistic-model analyses rather than language-model text alone. The Reviewer scores plans and intermediate results against pre-specified rubrics and triggers re-planning or re-execution when scores fall below threshold, producing an auditable chain from a natural-language question to model-derived evidence and cited literature. We instantiate the system over paired constraint-based metabolic models using COBRApy, supporting pathway comparison, perturbation analysis, drug-target exploration, and literature interpretation across healthy and disease states. We evaluated MechAInistic on two immune-cell therapeutic hypothesis-generation tasks. For rheumatoid arthritis versus healthy naive B-cell models, it identified mitochondrial metabolic rewiring and nominated Devimistat/CPI-613 as an investigational OGDH-centered hypothesis. For multiple sclerosis CD4+ Th17 versus healthy models, it identified NADP-dependent isocitrate dehydrogenase as a candidate target and proposed ivosidenib, with vorasidenib as a mechanistically complementary alternative. Comparator analyses against general-purpose LLM systems showed that plausible biological narratives can lack auditable model grounding, whereas MechAInistic preserves the computational reasoning path from prompt to result.

GRAPHICAL ABSTRACT

O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=83 SRC="FIGDIR/small/723319v3_ufig1.gif" ALT="Figure 1">
View larger version (19K):
org.highwire.dtl.DTLVardef@1f645eorg.highwire.dtl.DTLVardef@f68bb3org.highwire.dtl.DTLVardef@4da08corg.highwire.dtl.DTLVardef@6751bd_HPS_FORMAT_FIGEXP  M_FIG C_FIG