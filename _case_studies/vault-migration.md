---
layout: default
title: "Understanding Users Before Migrating Secrets"
summary: "How user research, story mapping and collaborative planning informed a migration from HashiCorp Vault to AWS Secrets Manager."
permalink: /case-studies/vault-migration/
order: 1
---

# Understanding Users Before Migrating Secrets

*Technical Business Analysis · User Research · Platform Teams*

## About this case study

Migrating from HashiCorp Vault to AWS Secrets Manager (AWS SM) wasn't just a technical change. It also required understanding how different users interacted with the service, what challenges they faced and which existing workflows needed to be preserved or improved.

This case study explores how user research and collaborative story mapping informed migration requirements and an agreed Minimum Viable Product (MVP) strategy.

The supporting materials include reconstructed examples and retrospective proposals. Confidential information has been anonymised or omitted, and the proposed success metrics are not presented as measured project outcomes.

## Context & Challenge

My internal platform team was responsible for maintaining the HashiCorp Vault implementation and managing access to it across a large software programme. This included onboarding and offboarding project members, maintaining access and denial policies, applying software updates, and overseeing the security of the service. Development teams remained responsible for managing their own secrets.

Although the wider project already relied heavily on AWS services, secrets management was still supported by a heavily customised Vault implementation.

Over time, this implementation had become increasingly difficult to maintain:

- **Operational risk:** Vault represented a single point of failure within the platform.
- **Legacy complexity:** The solution had been developed more than five years ago and contained considerable legacy code. The current team also had limited familiarity with its customisation.
- **Manual processes:** Common activities, such as onboarding users and updating access policies, required multiple manual steps.
- **Maintenance costs:** Maintaining or refactoring the existing implementation was considered more expensive than migrating to AWS SM.

Moving to AWS SM offered an opportunity to reduce these challenges and align secrets management with the wider AWS environment.

However, replacing the technology was only part of the challenge. Different user groups interacted with Vault in different ways, and the team needed to understand their workflows, permissions and pain points before defining requirements for the new solution.

**The key question was: How could we make the migration technically beneficial while ensuring the new solution supported the people using it?**

## My Contribution to Discovery and Planning

I worked within the Platform Team responsible for maintaining Vault and planning its replacement with AWS Secrets Manager.

My contributions included:

- **Stakeholder research:** Partnered with a Platform Owner to identify stakeholder groups and prepare interview questions.
- **Interview facilitation:** Led 12 individual interviews and one Platform Team group interview, supported by a UX designer who documented the conversations.
- **Research synthesis:** Reviewed and categorised findings with the UX designer, then presented the insights to our Platform Team.
- **Story mapping:** Prepared and facilitated a Mural workshop, working with the team to translate user needs into activities, potential work items and release planning.

I also participated in agreeing the initial MVP and second-release split with the Tech Lead, Product Owner and Platform Owners.

## Discovery

Our research involved **12 individual interviews** across six stream-aligned stakeholder groups, each lasting approximately 30–45 minutes, plus **one group interview with our Platform Team**. This helped us understand how users consumed the service and how our team administered and maintained it.

### Different Users, Different Needs

The research revealed distinct usage patterns across the seven stakeholder groups:

| User groups | Typical interaction with Vault |
| --- | --- |
| Developers, Tech Leads and Architects | Primarily used the CLI to create, update and retrieve secrets for development and integration workflows. |
| Project Managers, Product Owners and Quality Analysts | Primarily used the UI for role-specific workflows, including accessing test credentials, reading secrets and, for some roles, maintaining shared test-user credentials. |
| Platform Team | Administered Vault, managed user onboarding and offboarding, maintained user-synchronisation workflows, updated access and denial policies, and supported the service's operation and security. |

These differences highlighted the importance of considering both user-facing workflows and platform administration when planning the migration.

### Key Research Findings

The research revealed recurring challenges, differences in user workflows and aspects of Vault that users wanted to preserve.

| Research theme | What we learned | Implication for migration planning |
| --- | --- | --- |
| **Discoverability** | Users often needed to know the exact path to find a secret. | Consider how users could locate authorised secrets without memorising paths. |
| **Ownership and duplication** | Shared credentials were sometimes duplicated, causing inconsistent values and errors. Ownership wasn't always clear. | Explore clearer ownership, naming conventions and management practices. |
| **Permissions and administration** | Some users were unaware of their existing permissions. Our Platform Team also relied on cumbersome custom processes for membership and policy management. | Improve permission awareness and investigate simpler administrative workflows. |
| **Developer workflows and integrations** | CLI users valued their existing workflows. Developers, Tech Leads and Architects also wanted better CI/CD integration. | Preserve important technical workflows and investigate integration requirements. |
| **Authentication and migration safety** | Many users wanted access without requiring a VPN. Concerns were also raised about migration errors and the need for a controlled transition. | Evaluate secure access options and plan a gradual migration with appropriate validation. |

An important finding was that users generally found Vault straightforward once they had the necessary access and understood how to use it. The migration therefore needed to preserve useful existing experiences, not simply introduce new functionality.

These findings represented users' experiences with our implementation, rather than limitations inherent to HashiCorp Vault. They informed subsequent technical discussions and user story mapping, but did not automatically become approved implementation requirements.

## From Research Findings to Migration Planning

Following the discovery activities, I prepared and facilitated a story-mapping workshop in Mural to help our Platform Team translate research findings into actionable work and define an initial migration strategy.

### Mapping User Activities and Dependencies

Before the workshop, I prepared the stakeholder groups, high-level activities and narrative flow, incorporating insights from our discovery.

During the Mural workshop, our Platform Team reviewed these activities, identified missing steps and broke the workflows into more specific tasks and capabilities.

This gave us a shared view of the migration scope, covering user-facing needs, operational responsibilities and technical considerations.

### Defining the MVP and Release Strategy

Together with the Tech Lead, Product Owner and Platform Owners, we agreed on an initial two-release approach, which we subsequently presented to the wider team for feedback.

| Release | Focus |
| --- | --- |
| **Release 1 — MVP** | Enable core AWS SM workflows and onboard the Platform Team and two pilot stream-aligned teams with different technology stacks. Use dummy secrets to validate permissions, workflows and integration before wider adoption. |
| **Release 2** | Extend automation, support broader migration across teams and work towards retiring Vault. |

The objective was to validate the essential workflows with a small group of users before expanding the migration.

The story map gave us a shared reference for discussing work items, dependencies and release priorities. Technical investigation tasks were tracked separately as spikes.

### Defining Responsibilities and Automation

Alongside release planning, we considered how AWS SM could simplify existing workflows and reduce manual administration.

The intended approach separated the management of secret structures from the management of their values:

| Actor | Intended responsibility |
| --- | --- |
| **CI/CD workflows** | Create and delete secret structures through predefined automation. |
| **Authorised users** | Add, read and update secret values through the AWS Management Console. |
| **Applications and services** | Retrieve authorised secrets during execution. |
| **Platform Team** | Maintain shared capabilities, access patterns and supporting workflows. |

This approach aimed to standardise secret provisioning, clarify responsibilities and reduce the risk of exposing sensitive values through CI/CD pipelines.

It also connected several findings from our research, particularly around permissions, ownership, developer workflows and the need to reduce manual operational tasks.

*The story map and release slices presented in this portfolio are reconstructed and anonymised. They reflect the planning approach, not a claim that every mapped capability was implemented or delivered exactly as planned.*

### Supporting Artifacts

The following reconstructed artifacts provide more detail about how we translated discovery into migration planning:

- [User Story Map](https://github.com/Jenbn/technical-ba-platform-portfolio/tree/main/02-vault-to-aws-sm-migration/story-map) — Workshop approach, agreed release slices and technical investigations.
- [Work Item Examples](https://github.com/Jenbn/technical-ba-platform-portfolio/tree/main/02-vault-to-aws-sm-migration/work-items) — Examples of a user story, technical spike, support ticket and bug, including requirements and acceptance criteria.

*These artifacts are reconstructed and anonymised for portfolio purposes and should not be interpreted as verbatim project records or evidence of completed implementation.*

## Outcomes & Reflections

### What We Achieved

Our discovery and planning work gave the Platform Team a more informed foundation for the migration.

Instead of relying solely on technical assumptions, we could consider real user workflows, operational challenges and integration needs when discussing requirements and priorities.

The story-mapping workshop provided a shared reference for migration planning, resulting in an agreed initial MVP and release strategy. We also discussed ways to assess adoption, workflow reliability and readiness to retire Vault.

These were discovery and planning outcomes. I left the project before adoption began, so I cannot confirm which capabilities or metrics were eventually implemented or how successful the migration was.

### Measuring Success Beyond Delivery

Reflecting on the project, I explored additional ways to evaluate whether the migration improved the experience of the people using and maintaining the service.

My retrospective proposals included monitoring support requests, identifying documentation gaps and collecting developer feedback during and after migration.

Together with adoption and operational metrics, these could help answer a broader question: **Did the migration make secrets management easier, more reliable and more understandable for its users?**

### Key Takeaways

This experience reinforced three lessons for me:

- **Understand users before defining solutions.** Even technically motivated migrations can significantly affect people's daily workflows.
- **Make decisions collaboratively.** Combining user research with technical expertise helps connect needs, constraints and release priorities.
- **Think beyond implementation.** Migration success should also consider adoption, usability and operational impact.

For me, this project demonstrated the value of product thinking within an internal platform team: recognising developers and other internal stakeholders as users whose needs deserve attention.

**Explore further:** [Migration Evaluation & Success Metrics](https://github.com/Jenbn/technical-ba-platform-portfolio/tree/main/02-vault-to-aws-sm-migration/migration-evaluation)
