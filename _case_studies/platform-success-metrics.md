---
layout: default
title: "Measuring What Matters in Platform Teams"
summary: "Exploring platform success through support patterns, self-service usage and developer feedback."
permalink: /case-studies/platform-success-metrics/
order: 3
---


# Measuring What Matters in Platform Teams

*Platform Teams · Developer Experience · Product Thinking · Metrics*

## About This Case Study

How do we know whether an internal platform is successful? Is delivering features enough, or should we also understand whether those features make developers' work easier?

Supporting development teams involves more than delivering new capabilities. It also means understanding how people use them, where they encounter friction and whether they can work independently.

This case study explores how I used support ticket analysis, self-service usage data and developer feedback to identify recurring challenges, communicate the value of platform capabilities and inform improvements.

It also reflects on measurement approaches I considered but did not implement, and the limitations of interpreting metrics without sufficient context.

The examples are based on professional experience and recollections. Confidential information has been omitted, and observed patterns are distinguished from quantitatively verified outcomes.

## Context & Challenge

Our internal platform provided shared capabilities to stream-aligned development teams, including CI/CD, cloud infrastructure, access management and support services.

While delivery metrics helped us understand how work progressed, they didn't show the full picture of how developers experienced our platform.

I wanted to better understand whether teams were using our services independently, where they encountered recurring friction and what we could learn from their feedback.

To explore these questions, I combined support-ticket analysis, self-service usage data and direct conversations with developers.

## From Signals to Improvements

### 1. Support Tickets

#### Analysing Support Patterns

Our Platform Team used support tickets to handle questions, requests and issues from stream-aligned teams.

I regularly reviewed ticket classifications and created an eazyBI report showing ticket volumes by category, sprint and Program Increment (PI). This helped me identify recurring topics and potential gaps between the services we provided and how teams understood or used them.

Several patterns emerged:

- Some teams were unaware that they should use the relevant self-service pipeline to obtain production database access rather than requesting it directly from the Platform Team.
- Teams frequently requested assistance with their own CI/CD pipelines, even though operating those pipelines was their responsibility under our shared responsibility model.
- Questions about database provisioning, AWS services and database queries appeared repeatedly.

#### Improving Documentation and Communication

These findings highlighted opportunities to improve communication and make existing information easier to find.

I took several actions:

- Updated FAQ answers to address recurring questions and shared relevant documentation links in Slack.
- Reorganised Confluence documentation by archiving outdated content, separating internal technical guidance from user-facing information and making frequently needed information more prominent.
- Co-presented a project-wide technical huddle explaining where to find documentation, when to contact the Platform Team and what to check before raising a support ticket.

#### Understanding the Causes Behind Support Requests

The analysis suggested that some support requests were driven by unclear responsibilities, limited awareness of existing capabilities or difficulty finding relevant information.

I observed changes in support behaviour following these improvements, but did not establish a quantified reduction in tickets or prove that the documentation changes caused those changes.

The experience reinforced an important lesson: **support tickets aren't just operational work. They can also provide useful signals about documentation, discoverability and the developer experience.**

### 2. Temporary Production Database Access

#### Tracking Feature Usage

One of my team's offerings was a self-service capability that allowed stream-aligned teams to request temporary access to production databases for troubleshooting.

Before this capability was available, teams relied on the Platform Team to arrange access manually.

I regularly reviewed an existing dashboard that tracked access requests, usage frequency and access duration. The underlying Python script, which used the GitHub API, had been developed by a previous Product Owner. My contribution was analysing and communicating the available data, rather than implementing the tracking solution.

During one go-live period, the dashboard recorded **approximately 400 access requests in a single month**.

#### Making Demand Visible

I shared the dashboard's usage chart with our Platform Team to make demand for temporary database access visible, particularly during periods of increased production activity.

#### Understanding the Limits of Usage Data

The approximately 400 monthly requests demonstrated substantial demand, but they didn't establish how much time the self-service capability saved or how satisfied developers were with it.

The number also couldn't be interpreted as 400 avoided support tickets, since we hadn't established a direct comparison with the previous manual process.

### 3. Developer Feedback

#### Investigating the User Experience

While the usage dashboard showed demand for temporary production database access, it didn't tell us how developers experienced the feature or whether it met their needs.

After the capability was fully released, I identified frequent users and interviewed them about ease of use, documentation, potential improvements and unresolved issues. I also invited wider feedback through our project Slack channel.

#### Evaluating Feedback and Feature Requests

The feedback was generally positive. Users found the capability straightforward to use and the documentation helpful.

However, one PO wanted to use the feature for analytical JOIN queries across different databases, beyond its intended purpose of troubleshooting production issues.

We explored the request but found limited evidence of similar needs among other users, so we decided not to expand the feature's scope at that point.

#### Informing Product Scope Decisions

I shared the findings with our PO and team, helping us better understand the experience behind the usage metrics.

This reinforced an important lesson about product thinking: **a user request deserves investigation, but not every request justifies expanding a product's scope.**

The interviews provided useful qualitative insights, but they weren't a representative satisfaction survey or a quantified measure of developer experience.

## Other Signs of Platform Success

Platform success isn't only about feature adoption or developer satisfaction. Reliable services and clear onboarding also contribute to a positive developer experience.

### Maintaining Service Reliability During Migration

Our Platform Team completed a cluster migration with **no observed downtime**.

To reduce operational risks, the team tested the migration approach in advance, migrated non-production environments before production, and used monitoring dashboards and automated functional tests.

We also gathered information about application dependencies and collaborated with QAs, Tech Leads, Architects and other relevant colleagues to support a coordinated migration.

This was a collective team achievement, rather than a reliability metric I personally introduced. Nevertheless, it illustrated another important dimension of platform success: enabling technical changes while maintaining service availability.

### Clarifying Responsibilities Through Onboarding

I also adapted onboarding information for POs working in stream-aligned teams.

The material explained what our Platform Team was responsible for, how stream-aligned teams could interact with us and where they could find guidance or request support.

The feedback I received was positive, although I didn't formally measure onboarding effectiveness.

## Exploring Better Measures

Beyond the metrics I was already working with, I considered additional ways to evaluate platform success. These ideas were not implemented as a comprehensive measurement framework, but they helped me think more critically about what we could measure and what the results might tell us.

### Evaluating Support Trends After Changes

I considered two approaches to better understand support trends:

- **After feature releases:** Compare release dates with the volume and categories of subsequent support tickets to identify unexpected issues or areas requiring better guidance.
- **After documentation updates and technical huddles:** Compare recurring support questions before and after improvements to FAQs, documentation or knowledge-sharing sessions.

However, fewer tickets wouldn't automatically indicate a better experience. Teams might be unaware of a feature, find workarounds or stop reporting problems.

Any analysis would also need to consider changes in platform usage, the number of active teams and other improvements happening simultaneously.

### Looking Beyond Individual Metrics

I was also interested in exploring broader ways of evaluating platform success, particularly how our services influenced developer productivity, satisfaction and the ability to work independently.

Some of the measurement areas I considered included:

| Measurement area | Metrics I was interested in | What they could help us understand |
| --- | --- | --- |
| **DORA metrics** | Deployment frequency, lead time for changes, change failure rate and time to restore service | How reliably and efficiently we delivered platform changes. |
| **Developer experience** | Developer satisfaction, perceived productivity and friction points | Whether platform services made everyday development work easier. |
| **Platform adoption** | Active teams, capability usage and adoption rates | Whether teams were discovering and using the services available to them. |
| **Self-service efficiency** | Infrastructure provisioning time, configuration-change lead time and developer waiting time | Where manual processes or dependencies on platform support slowed teams down. |

These were areas I was interested in exploring, rather than metrics I had implemented as part of a comprehensive measurement programme.

The article [*Platform Team Metrics That Actually Matter: Beyond DORA*](https://platformengineering.com/features/platform-team-metrics-that-actually-matter-beyond-dora/) by Neel Shah provides a useful perspective on combining delivery, adoption, developer experience and operational metrics to evaluate platform value.

My main takeaway was that **no single metric can demonstrate platform success**. Usage, reliability, developer feedback and workflow efficiency need to be considered together to understand whether a platform is genuinely helping its users.

### Recognising Data Quality Limitations

One metric I wanted to explore was **support request lead time**: the elapsed time between a request being raised and resolved.

However, support pairs didn't consistently update Jira ticket statuses, making the timing data unreliable as a complete representation of the support process.

I reminded colleagues to maintain ticket statuses and facilitated a support-process huddle to discuss improvements.

This highlighted an important limitation: **before introducing a metric, we need shared definitions and reliable data collection practices.**

Without those foundations, even a well-designed dashboard can produce misleading conclusions.

I did not establish a validated support lead-time baseline or measure an improvement in this metric.

## Outcomes & Reflections

What I found most valuable was learning to connect different sources of information rather than relying on a single metric.

Support tickets helped me recognise recurring friction. Usage data made the demand for self-service visible. Conversations with developers provided context that dashboards couldn't capture. Together, these insights informed documentation improvements and discussions about platform priorities.

I also became more critical of the conclusions we draw from numbers. High usage doesn't necessarily mean high satisfaction, and fewer support requests don't automatically mean fewer problems. Even a useful metric can be misleading if the underlying data is unreliable.

This experience strengthened my interest in treating internal platforms as products. For me, measuring platform success isn't simply about demonstrating how much a team delivers, but about understanding whether the services it provides genuinely help people work more effectively.

**Explore the supporting project:** [Platform Success Metrics on GitHub](https://github.com/Jenbn/technical-ba-platform-portfolio/tree/main/04-platform-success-metrics)
