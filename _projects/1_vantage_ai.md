---
layout: page
title: Vantage AI
description: Production-grade lease analysis — web + Android — with PII redaction before any LLM call
img: assets/img/projects/vantage.png
importance: 1
category: ""
---

**The problem.** Residential leases are dense, one-sided documents that most renters sign unread. Vantage AI — our UC Berkeley MIDS capstone — analyzes a lease PDF (web upload or Android photo capture) and returns a structured report: rights and risks, missing disclosures, cross-clause conflicts, and a negotiation plan, grounded in a California statute and guidance corpus.

<div class="row justify-content-center">
    <div class="col-sm-10 mt-3 mb-3">
        {% include figure.liquid loading="eager" path="assets/img/projects/vantage.png" title="Vantage AI analyzing a demo lease" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The Rights & Risk view on the built-in demo lease: every claim carries evidence quotes from the document, and risk badges distinguish legal conflicts from negotiable one-sided language.
</div>

**How it works.** PII is redacted (Microsoft Presidio + spaCy) before any text reaches an LLM. Eight lease aspects are analyzed concurrently through a retrieve → generate → judge loop over hybrid keyword + vector retrieval (Qdrant), with deterministic Risk and Disclosure engines layered on top so compliance findings never depend on model mood. FastAPI/asyncio backend, provider-agnostic LLM layer (LiteLLM), vanilla-JS web client, Kotlin/Compose Android app with on-device ML Kit OCR, deployed via Docker and Kubernetes.

**My role.** I owned the evaluation harness, the Android app, the compliance rules, and the legal corpus (33 merged PRs of the team's 86). The eval harness is the part I'm proudest of: a three-arm benchmark (deterministic vs. RAG-LLM vs. no-RAG baseline) over a 58-case labeled dataset spanning 7 California lease templates with cross-template trap replants, scored with seeded bootstrap confidence intervals and exact McNemar tests.

**Results — including the honest ones.** From the 2026-07 three-arm run: zero hallucinated evidence in both pipeline arms; retrieval hit@1 of 0.60 vs. 0.52 for the no-RAG baseline (McNemar p = 0.0003, n = 218 — though baseline-dependent: p = 0.089 against an older model's bare arm); trap recall 1.00 for the RAG arm vs. 0.25 deterministic; compliance precision 1.00; median latency 5.8 s deterministic vs. ~39 s LLM. We report the negative findings too — the LLM lease-review layer over-flags on clean templates (0/43 trap precision there), which is exactly the kind of thing an eval harness exists to catch.

**Team.** Built with Evan Powell, Terra Jiang, Trenton Carlson, and Adam Valadez.

**Links.** [Official capstone listing (UC Berkeley I School)](https://www.ischool.berkeley.edu/programs/mids/capstone/2026b-summer/vantage-ai) · [CA Code Downloader](/projects/7_ca_code_downloader/) — the statute-acquisition utility I built for the legal corpus. The application source is private.
