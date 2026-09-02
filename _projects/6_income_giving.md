---
layout: page
title: Income and Charitable Giving
description: Are Americans with higher incomes more generous? An OLS study with robust inference
img: assets/img/projects/income.png
importance: 6
category: ""
---

**The question.** Research agrees that richer households give more dollars — but disagrees on whether they give a larger *share*. Testing the popular "U-shaped generosity" hypothesis, we modeled charitable-giving proportion against income using county-aggregated 2022 IRS Statistics of Income data. UC Berkeley MIDS statistics final project.

<div class="row justify-content-center">
    <div class="col-sm-9 mt-3 mb-3">
        {% include figure.liquid loading="eager" path="assets/img/projects/full/income_abstract.png" title="Are Americans with higher incomes more generous?" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

**How it works.** OLS regression in R with linear, quadratic, and logarithmic AGI specifications, robust standard errors (`sandwich`/`lmtest`), full CLM assumption diagnostics, and `stargazer` regression tables, in a reproducible `renv` project with peer-reviewed drafts.

**Results.** The data rejected the U-shape: we found a J-shaped *positive* relationship — giving proportion grows non-linearly with mean AGI. The preferred model (AGI terms plus dividend, capital-gains, and rent/royalty income) explains 78.5% of the variance in charitable contributions per return (adjusted R² = 0.785).

<div class="row justify-content-center">
    <div class="col-sm-8 mt-3 mb-3">
        {% include figure.liquid path="assets/img/projects/full/income_stargazer.png" title="Regression results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The model progression (stargazer, robust standard errors): from a linear AGI baseline (adj. R² = 0.602) through the quadratic specification to the preferred model (4), which adds dividend, capital-gains, and rent/royalty income — adj. R² = 0.785, n = 2,089 counties.
</div>

**Team.** With Fatema Alsaleh and WooJung Kim.

**Links.** [Repository](https://github.com/cpfrish/income_and_charitable_giving_analysis) · [Final report (PDF)](https://github.com/cpfrish/income_and_charitable_giving_analysis/blob/main/reports/Income_and_Charitable_Giving.pdf)
