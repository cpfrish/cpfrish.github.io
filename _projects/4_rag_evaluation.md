---
layout: page
title: RAG Evaluation Pipeline
description: 13 pipeline configurations, 75 labeled QA pairs, two audiences — which RAG stack actually wins?
img: assets/img/projects/rag.jpg
importance: 4
category: ""
---

**The question.** Everyone ships RAG; few measure it. For UC Berkeley's Generative AI course final, I built a retrieval-augmented generation proof of concept that answers AI/ML questions for two internal audiences (a several-hundred-person engineering org and a 40-person marketing team) — and then evaluated 13 pipeline configurations against 75 labeled question-answer pairs to find out what actually helps.

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mb-3">
        {% include figure.liquid loading="eager" path="assets/img/projects/full/rag_langgraph.png" title="The LangGraph pipeline as built" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The LangGraph state machine as actually built: retrieval into a shared reader, fanning out to parallel research and marketing persona nodes before a merge. Dashed nodes (query rewriter, cross-encoder reranker) are config-gated — the winning configuration runs without them.
</div>

**How it works.** The harness varies chunk size, query rewriting, reranking, and generator model (Cohere command-a vs. command-r vs. an optimized configuration), scoring each configuration per-persona with BERTScore (roberta-large embeddings), ROUGE, and faithfulness metrics — plus adversarial out-of-domain probes to catch confident nonsense.

**Results.** A *minimal* stack won: no query rewriter, no reranker, small chunks, Cohere Command A — BERT-F1 of 0.876 (engineering persona) and 0.881 (marketing), faithfulness above 0.87 for both, at a projected serving cost under 100 USD/month versus 1,500+ USD/month for reserved GPU capacity.

<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mb-3">
        {% include figure.liquid path="assets/img/projects/full/rag_results.png" title="Configuration comparison" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The full comparison: eleven configurations screened on a 4-question subset (left, sorted by mean BERT-F1), then the three finalists benchmarked on all 75 questions (right) — the Cohere baseline wins both metrics for both personas.
</div>

Two findings I'd carry into production: 128-token chunks score well in aggregate but truncate detail retrieval, and out-of-domain queries sail through with irrelevant context — the system needs a relevance gate before it can be trusted.

**Solo project.**

**Links.** [Repository](https://github.com/cpfrish/rag-evaluation-pipeline) · [Full evaluation report (PDF)](https://github.com/cpfrish/rag-evaluation-pipeline/blob/main/final_report.pdf)
