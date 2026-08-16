---
layout: page
title: CA Code Downloader
description: A polite, cache-everything scraper for California statute text — the data layer behind Vantage AI
importance: 7
category: ""
---

**The problem.** Vantage AI's legal grounding needed the full text of California statutes (Civil Code, Code of Civil Procedure, FEHA). The state's Legislative Information site publishes them — public domain under Government Code §10248.5 — but behind a stateful JSF navigation tree that breaks naive scrapers and punishes hand-constructed URLs.

**How it works.** The downloader walks the site's real navigation tree the way a browser would — never fabricating URLs — respects robots.txt, throttles politely, and caches every response so a full corpus rebuild costs the source site almost nothing. The module documentation explains each of those choices, because scraping etiquette is a design requirement, not an afterthought.

**Why it matters.** Statute text feeds Vantage AI's retrieval corpus and its deterministic compliance rules — the parts of the system that must never hallucinate. Clean, reproducible acquisition is where that reliability starts.

**Solo project.**

**Links.** Code release in progress — being published as part of this portfolio's rollout. See it in context in the [Vantage AI case study](/projects/1_vantage_ai/).
