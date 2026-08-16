---
layout: page
title: Offshore Leaks — Mapping the Shadow Economy
description: Graph algorithms over 800k+ offshore entities in Neo4j — finding the "offshore factories"
img: assets/img/projects/offshore.png
importance: 5
category: ""
---

**The question.** The ICIJ Offshore Leaks database (Panama Papers and successors) links more than 800,000 offshore entities and 750,000 people and companies across 200+ countries. Relational queries struggle with "who is connected to whom through what" — so we loaded it into a graph database and asked the network itself. UC Berkeley MIDS data engineering final project; I led the team.

<div class="row justify-content-center">
    <div class="col-sm-10 mt-3 mb-3">
        {% include figure.liquid loading="eager" path="assets/img/projects/offshore.png" title="Louvain community detection on the Offshore Leaks graph" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Louvain community detection reveals the "offshore factory" pattern: dandelion-shaped clusters where a single intermediary mass-produces shell entities.
</div>

**How it works.** The ICIJ dump is loaded into Neo4j and interrogated with graph algorithms: degree centrality and PageRank to find the load-bearing nodes, then Louvain community detection to expose cluster structure. We paired the graph analysis with NoSQL architecture cases — where MongoDB (heterogeneous future leak ingestion, geo/text search) and Redis (real-time risk leaderboards) would extend an investigative platform.

**The finding.** Centrality and PageRank both point at Portcullis TrustNet (BVI) Limited — founded by a former Cook Islands Solicitor General who helped write the offshore laws, then sold navigation of them. Community detection around it exposed an assembly line: 80+ entities jointly formed by Portcullis (intermediary) and signed by DirectCorp (officer) — a deliberate, repeatable shell-company production pattern, visible only at the graph level.

**Team.** Led by me, with Ryan Castillo, Ani Sreekumar, and Jenny Park.

**Data note.** The ICIJ Offshore Leaks database is publicly available from ICIJ under the Open Database License; we analyze it and link to it rather than redistribute it.

**Links.** Code release in progress — the cleaned repository (notebooks + slides) is being published as part of this portfolio's rollout.
