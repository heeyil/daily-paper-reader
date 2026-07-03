---
title: "ChatSpatial: Schema-Enforced Agentic Orchestration for Reproducible and Cross-Platform Spatial Transcriptomics"
title_zh: ChatSpatial：基于模式强制编排的可重复、跨平台空间转录组学分析
authors: "Yang, C., Zhang, X., Chen, J."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.26.708361v3.full.pdf"
tags: ["query:agent-lsh"]
score: 7.0
evidence: 通过模式强制编排在复杂环境中利用LLM智能体
tldr: "空间转录组学分析常需协调Python和R方法，但临时脚本或LLM生成的代码导致工作流难以检查、复现和比较。ChatSpatial通过模式强制执行，让LLM选择版本化工具和参数而非代码，基于MCP协议集成65种方法到20个类型化工具。在两种癌症案例中，它恢复了已发表分析的结构和结论；参数有效性从20%提升至98%，方法选择趋于稳定。相比代码生成方案，执行成功率和输出一致性更高，为可复现、跨平台的空间转录组分析提供了可靠方案。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有工作流依赖临时脚本或LLM代码，难以检查、复现和比较，需一种可复现、跨平台的分析框架。
method: ChatSpatial基于模式强制执行，LLM选择版本化工具和参数，而非生成代码；集成65种方法到20个类型化工具，使用MCP协议。
result: "在卵巢癌和口腔鳞癌案例中恢复分析结构；参数有效性从20%升至98%，端到端执行成功率和输出一致性优于代码生成。"
conclusion: ChatSpatial实现了可复现、可比较的跨平台空间转录组分析，提升了LLM辅助分析的可靠性和稳定性。
---

## 摘要
空间转录组学分析通常需要协调专门的Python和R方法。当分析意图通过临时脚本或不受约束的LLM生成代码来传达时，工作流程可能难以检查、重新运行或比较。我们提出了ChatSpatial，一个模式强制编排框架，其中LLM选择版本化的工具和参数，而非可执行代码。基于模型上下文协议，ChatSpatial将15个分析类别的65种方法整合到20个带有精选默认值的类型化工具中。在两个癌症案例研究中，ChatSpatial协调了跨生态系统的工作流程，恢复了已发表的卵巢癌和口腔鳞状细胞癌分析的分析结构和核心结论。在三个LLM上，模式强制将参数有效性从20%提高到98%，并稳定了方法选择。在与两种代码生成替代方案的端到端基准测试中，它产生了更高的执行成功率和输出一致性。

## Abstract
Spatial transcriptomics analyses often require coordinating specialized Python and R methods. When analytical intent is translated through ad hoc scripts or unconstrained LLM generated code, workflows can be difficult to inspect, rerun, or compare. We present ChatSpatial, a schema enforced orchestration framework in which an LLM selects versioned tools and parameters rather than executable code. Built on the Model Context Protocol, ChatSpatial integrates 65 methods across 15 analytical categories into 20 typed tools with curated defaults. In two cancer case studies, ChatSpatial coordinated cross ecosystem workflows that recovered the analytical structure and central conclusions of published ovarian cancer and oral squamous cell carcinoma analyses. Across three LLMs, schema enforcement raised parameter validity from 20% to 98% and stabilized method selection. In end to end benchmarks against two code generation alternatives, it yielded higher execution success and output concordance.