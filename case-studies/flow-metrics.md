---
layout: default
title: "From Flow Metrics to Better Planning"
permalink: /case-studies/flow-metrics/
---

# From Flow Metrics to Better Planning

*Technical Business Analysis · Platform Teams · Delivery Predictability · Retrospective Forecasting*

## About this case study

As a Technical Business Analyst in a platform team, I used **flow and delivery metrics** to question planning assumptions, identify workflow bottlenecks and support practical improvements with the Product Owner (PO), Tech Lead and team.

This case study brings together two distinct experiences:

- **During the project:** I used historical delivery data and investigated specific work items to inform planning and improve how we worked.
- **Afterwards:** I explored **Monte Carlo forecasting** in Google Sheets as a retrospective learning exercise. I did not use Monte Carlo in the original project.

### Explore the analysis

The supporting workbook models a fictional team, **Team Aqueduct**, using synthetic data—not historical records from my employer. It contains the metric calculations, charts and forecasting simulations.

- **[Download the Excel workbook](https://github.com/Jenbn/technical-ba-platform-portfolio/blob/main/03-flow-metrics-forecasting/data/team_aqueduct_metrics.xlsx)** — Data, calculations and visualisations.
- **[Read the dataset README](https://github.com/Jenbn/technical-ba-platform-portfolio/blob/main/03-flow-metrics-forecasting/README.md)** — Modelling context, AI assistance and limitations.
- **[Explore the Analysis in Google Sheets](https://docs.google.com/spreadsheets/d/1PH6bDGx60KW_-77tscZUf3W54xKOBAM4CkPxAl1xB3I/edit?usp=sharing)** - View the metrics, charts and Monte Carlo simulations.

## Flow metrics at a glance

| Metric | What it tells us | How I used it |
| --- | --- | --- |
| **Sprint delivery & spillovers** | How planned, completed and changed scope compare; how often work carries into another sprint | Spotted a pattern of overcommitment and supported more realistic planning |
| **Throughput** | Number of work items completed in a given period, irrespective of story points | Used previous sprints and PIs as a historical reference for future planning |
| **Time in status** | Where items spend time, including waiting and handoffs | Identified queues around QA and sign-off |
| **Cycle time** | How long work takes from a defined starting status until completion | Investigated outliers and recurring external dependencies |

*The charts and detailed breakdowns are in the workbook tabs `Sprint_Delivery`, `Throughput`, `Time_In_Status`, `Time_Per_Work_Item` and `Cycle_Time`, along with their comparison tabs.*

## From insights to improvements

### 1. Improving sprint planning

**Metrics:** Throughput + sprint delivery

**The challenge.** We were regularly carrying approximately **five items into the next sprint**. Story points were expected in the project and had become a major reference for forecasting, even though estimates couldn't capture all the time spent waiting for reviews, feedback or other teams.

**What I did.** I built eazyBI views of throughput and sprint delivery across previous Program Increments (PIs), shared the historical completion patterns with our PO and used them as an additional reference in planning conversations. Inspired by the book, [*When Will It Be Done?* by Daniel S. Vacanti](https://leanpub.com/whenwillitbedone), I also facilitated knowledge sharing about the limits of story-point forecasting. I didn't suggest removing story points: with the Tech Lead, I helped define a **Fibonacci reference table**, including explanations and example stories, so points could remain useful for discussing relative complexity and uncertainty.

**What changed.** As we began using historical delivery alongside our other planning inputs, spillovers **fell from approximately five to two per sprint**. This was an observed team outcome, not proof that one specific intervention caused the reduction.

### 2. Reducing waiting time

**Metric:** Time in status

**The challenge.** Work items spent substantial time waiting for **QA desk-checks and sign-off**.

**What I did.** I brought the bottlenecks to the PO, Tech Lead and team. The team proposed dedicated desk-check and sign-off slots **twice a week**, and I suggested a **first-in, first-out (FIFO)** default for these queues, while allowing legitimate urgent exceptions. I also encouraged colleagues to update Jira statuses accurately so our workflow data reflected what was really happening.

**What changed.** We introduced clearer review practices and a more transparent approach to queues. I didn't separately quantify the resulting reduction in waiting time, so I wouldn't claim a measured improvement in this metric.

### 3. Shortening feedback loops

**Metric:** Cycle time

**The challenge.** The PO and I found work items with unusually long cycle times. A recurring pattern involved changes that needed validation by **stream-aligned teams**, such as a Java 11-to-17 transition across testing and production environments.

**What I did.** We discussed specific outliers with the team and decided to split testing-environment and production-environment changes into **separate work items**. We allowed a short feedback window—typically **one or two working days**—then directed later issues through support tickets rather than keeping the original story open indefinitely. We also worked on smaller, valuable stories and spikes with a time-box scope.

**What changed.** Work and external dependencies became easier to track, with shorter feedback loops as a guiding principle. The feedback window was a workflow agreement, **not** evidence that a production change was risk-free after two days.

## Monte Carlo forecasting — retrospective exercise

I had already worked with throughput and percentiles during the project, but **I hadn't implemented Monte Carlo forecasting**. I built the following examples later to learn how a BA or PO could communicate delivery uncertainty rather than presenting a single estimate as a promise.

### How it works and what data it needs

Monte Carlo forecasting repeatedly samples **historical throughput** to simulate a range of future delivery outcomes. It helps answer two different planning questions:

- **How Many?** How much work could be completed within a fixed timebox?
- **When?** How many sprints might be needed to finish a fixed backlog?

My synthetic workbook contains **four PIs of six two-week sprints**. Sprints **1–5** represent normal development; Sprint **6** includes one week of carryover work and one innovation week. To reflect that difference, I sampled from two pools: **20 regular sprints** and **four Sprint 6 observations**, across **1,000 simulations**.

### How Many? — One PI

**Question:** How many items could be completed in one six-sprint PI?

| Estimated chance of delivering *at least* | Completed items | Share in saved simulation |
| --- | ---: | ---: |
| 50% | 54 | 51.4% |
| 70% | 52 | 72.1% |
| 85% | 50 | 87.5% |
| 95% | 47 | 96.3% |

**How I interpret it:** In the saved simulation, delivering at least **50 items** occurred in **87.5%** of runs, whereas delivering at least **54** occurred in **51.4%**. This gives a PO different scope options to discuss, each with a different level of uncertainty.

**Visualisation:** Open the workbook's `Monte_Carlo_Snapshot` (fixed results) and `Monte_Carlo_How_Many` (live histogram and calculations).

![Monte Carlo How Many forecast: distribution of completed work items]({{ '/assets/images/monte-carlo/how-many.png' | relative_url {: .chart-image }
<p class="figure-caption">
    Figure 1 — Distribution of completed work items across 1,000 simulated PIs, using synthetic historical throughput.
</p>

### When? — A backlog of 60 items

**Question:** How many sprints might be needed to complete **60 items**?

| Completion by the end of | Share of simulated runs |
| --- | ---: |
| Sprint 5 | 0.6% |
| Sprint 6 — one PI | 2.9% |
| Sprint 7 | 85.1% |
| Sprint 8 | 99.9% |
| Sprint 9 | 100% |

**How I interpret it:** Finishing all 60 items within one PI was unlikely under this model. **Seven sprints** offered about an **85% simulated chance**, while **eight** provided more contingency. The 100% shown at Sprint 9 describes these sampled outcomes—it is **not a guarantee** for a real project.

**Visualisation:** See `Monte_Carlo_When` for the cumulative completion-probability chart and sprint-by-sprint calculations.

![Monte Carlo When forecast: probability of completing the backlog by sprint]({{ '/assets/images/monte-carlo/when.png' | relative_url }}){: .chart-image }
<p class="figure-caption">
    Figure 2 — Estimated number of sprints required to complete a backlog of 60 work items, showing the cumulative probability of completion based on 1,000 Monte Carlo simulations.
</p>

### How I'd apply this in planning

I would use these forecasts as **conversation starters** in PI planning and roadmap discussions: compare a few scope and date options, make their assumptions explicit, and revisit the forecast as team capacity, work mix and dependencies change. I'd also compare forecasts against actual outcomes over time.

These results use a **small synthetic history**, particularly for Sprint 6. They assume broadly comparable future conditions and don't explicitly model new scope, dependencies or related delays. The *How Many?* figures above come from a saved snapshot; the live simulations can change when recalculated. **These are demonstrations of the method, not validated predictions for my former team.**

## Key takeaways

For me, the value of metrics isn't the chart itself. It's being able to **ask better questions, make bottlenecks visible and bring evidence into conversations** with the PO, Tech Lead and team.

The retrospective Monte Carlo exercise extended that learning: instead of treating a forecast as a single number, I learned to communicate **different possible outcomes, their estimated likelihoods and the assumptions behind them**.
