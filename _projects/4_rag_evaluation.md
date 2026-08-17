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
    <div class="col-sm-8 mt-3 mb-3">
        {% include figure.liquid loading="eager" path="assets/img/projects/rag.jpg" title="RAG pipeline architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The pipeline under test: document store with caching, retrieval, optional query rewriting and reranking, and the generator.
</div>

**How it works.** The harness varies chunk size, query rewriting, reranking, and generator model (Cohere command-a vs. command-r vs. an optimized configuration), scoring each configuration per-persona with BERTScore (roberta-large embeddings), ROUGE, and faithfulness metrics — plus adversarial out-of-domain probes to catch confident nonsense.

**Results.** A *minimal* stack won: no query rewriter, no reranker, small chunks, Cohere Command A — BERT-F1 of 0.876 (engineering persona) and 0.881 (marketing), faithfulness above 0.87 for both, at under $100/month projected serving cost versus $1,500+ for reserved GPU capacity. Two findings I'd carry into production: 128-token chunks score well in aggregate but truncate detail retrieval, and out-of-domain queries sail through with irrelevant context — the system needs a relevance gate before it can be trusted.

**Solo project.**

**Links.** [Repository](https://github.com/cpfrish/rag-evaluation-pipeline) · [Full evaluation report (PDF)](https://github.com/cpfrish/rag-evaluation-pipeline/blob/main/final_report.pdf)
