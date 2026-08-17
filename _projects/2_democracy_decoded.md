---
layout: page
title: Democracy Decoded
description: The 119th U.S. Congress by generation, party, and geography — 13 interactive visualizations
img: assets/img/projects/democracy.png
importance: 2
category: ""
---

**The question.** Who actually represents us — by generation, party, and place — and how does that shape what Congress works on? Democracy Decoded is an end-to-end pipeline and visualization suite over the 119th U.S. Congress, built for UC Berkeley's Data Visualization course.

<div class="row justify-content-center">
    <div class="col-sm-11 mt-3 mb-3">
        {% include figure.liquid loading="eager" path="assets/img/projects/full/democracy_member_activity.png" title="Member legislative activity by birth year and generation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Every member of the 119th Congress, plotted by birth year and bills sponsored, colored by generation — <a href="https://colinfrishberg.com/democracy-decoded/visualizations/member_activity_scatter_interactive.html">explore it live</a>.
</div>

<div class="row justify-content-center">
    <div class="col-sm-11 mt-3 mb-3">
        {% include figure.liquid path="assets/img/projects/full/democracy_bill_tracker.png" title="Congressional bills tracker" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    From the bill tracker: the 119th Congress's 11,634 bills by type — House bills dominate at 6,486, with an inline legend decoding every bill class from HR to SCONRES — <a href="https://colinfrishberg.com/democracy-decoded/visualizations/congress_bill_tracker.html">explore the full tracker live</a>.
</div>

**How it works.** Numbered Python pipeline scripts fetch member, bill, and vote data from the Congress.gov API (with caching and rate-limit courtesy), join it to GeoJSON congressional district boundaries, and emit 13 standalone interactive visualizations — Altair charts and D3 maps — including a district-level choropleth, a dual-chamber state map, a party-loyalty ranking, a bill tracker, and the generational dashboard above.

**My role.** Data pipeline design and the generational/topic analyses, with the team: Banjot Saini, Jane Lai, and Sarah Ki.

**Links.** [Repository](https://github.com/cpfrish/democracy-decoded) · **Live demos:** [generational dashboard](https://colinfrishberg.com/democracy-decoded/visualizations/congress_generational_dashboard.html) · [district map](https://colinfrishberg.com/democracy-decoded/visualizations/congress_district_map.html) · [bill tracker](https://colinfrishberg.com/democracy-decoded/visualizations/congress_bill_tracker.html) · [all 13](https://github.com/cpfrish/democracy-decoded#findings--live-demos)
