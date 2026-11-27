---
layout: default
title: "Your Developers Are Users Too: What I Learned as a BA in a Platform Team"
summary: "Reflections on product thinking, self-service and developer experience from both sides of an internal platform."
date: 2026-11-27
permalink: /ideas-and-insights/platform-as-a-product/
---


# Your Developers Are Users Too: What I Learned as a BA in a Platform Team

*Reflections on product thinking, self-service and developer experience from both sides of an internal platform.*

## From Reactive Support to Product Thinking

Before becoming a Business Analyst in a Platform Team, I had already experienced the platform from the other side.

I worked as a Quality Analyst in a stream-aligned team within the same project, and during my initial onboarding, I had also spent some time shadowing the Platform Team.

Back then, my understanding of their role was mostly reactive. Teams would raise issues in the support channel, and the Platform Team would step in to solve infrastructure-related problems. From my perspective, they were the people you contacted when something wasn't working.

I knew they provided shared infrastructure and technical capabilities, but I couldn't quite imagine what a roadmap for a platform team would look like. I hadn't experienced them proactively asking us what we needed. Instead, it seemed that the platform capabilities were largely defined by what the team believed the consuming teams required.

That perspective began to change when I returned to the project as a Business Analyst, this time joining the Platform Team itself.

My Delivery Lead and Product Owner had a strong product-thinking mindset. Through conversations with them and resources they recommended, including Team Topologies, Platform Strategy: Innovation Through Harmonization by Gregor Hohpe, and the Product Talk blog, I gradually started to see the platform differently.

I realised that a platform team didn't have to be defined by support tickets and reactive work. It could have its own roadmap, understand its users, investigate their needs and proactively develop capabilities that made their daily work easier.

And those users were the same developers, Quality Analysts and other delivery colleagues I had previously worked alongside.

**That was the shift for me: seeing the platform not just as the infrastructure behind other products, but as a product in its own right, with users whose needs deserved to be understood.**

## Understanding Developers as Users

One of the things I appreciated most about working in an internal platform team was how close we were to our users. **I used to say that our users were just a click away**. I could simply open their calendars and arrange a conversation with the developers, QAs, BAs or other colleagues using our services.

That proximity gave me a great opportunity to understand how they worked, what frustrated them and what could make their daily tasks easier. Instead of making assumptions about their needs, I could ask them directly.

For specific initiatives, such as the migration from HashiCorp Vault to AWS Secrets Manager, I conducted user interviews to understand existing workflows, pain points and expectations. I also interviewed frequent users of our temporary production database access capability to understand their experience after its release.

But learning about our users didn't always require a formal interview. During PI Planning or other team events, I took opportunities to ask colleagues about our platform services and their experiences using them. Whenever we introduced changes, I also encouraged feedback through our Slack channel and reminded my teammates to keep their ears open for questions, frustrations or suggestions.

I learned that **user discovery doesn't have to be limited to scheduled research sessions**. Informal conversations, recurring support questions and spontaneous feedback can reveal valuable insights too.

This also resonated with what I'd been learning from Teresa Torres's work on [continuous discovery](https://www.producttalk.org/), particularly the importance of making interactions with users a regular part of product development.

## Self-Service: Helping Teams Work Independently

Before joining the Platform Team, I wasn't particularly familiar with the concept of self-service in software delivery. I knew our platform provided infrastructure and technical capabilities, but I hadn't fully appreciated how much difference it could make when teams could access those capabilities independently.

Our platform offered workflows that allowed stream-aligned teams to perform activities such as provisioning databases without having to raise a support ticket and wait for someone from our team to handle every request.

What might previously have involved several messages, handovers and waiting time could instead be handled through a standardised workflow.

I began to understand that the value of a platform wasn't just about providing the right infrastructure or technology. It was also about **reducing friction and allowing development teams to focus on delivering their own products**.

### Documentation Is Part of the Developer Experience

One thing I learned was that self-service isn't really self-service if people don't know it exists or can't figure out how to use it.

We sometimes received support requests for activities that could already be completed through existing platform workflows. This made me realise that providing a capability wasn't enough. Teams also needed to know where to find it, understand how it worked and feel confident using it.

I contributed by reorganising our Confluence documentation, separating internal Platform Team procedures from guidance intended for stream-aligned teams, updating FAQs and making frequently needed information easier to find.

For me, this reinforced that **developer experience isn't just about automation and technology**. Clear documentation, understandable processes and accessible support information are just as important in helping people work independently.

## Why a Platform Shouldn't Support Everything

Another important lesson I learned was that a platform team doesn't necessarily need to accommodate every request from every stream-aligned team.

At first, this seemed counterintuitive. If our goal was to help developers work more effectively, shouldn't we provide them with the technologies and services they needed?

Over time, I understood that there was a difference between **meeting a user's needs and taking ownership of every solution they requested**.

For example, if one stream-aligned team needed a particular technology that wasn't part of our platform's standard offerings, it didn't automatically mean our team should adopt and maintain it. Instead, we could provide the necessary foundations, such as access to AWS capabilities or the flexibility to extend a supported base image, allowing that team to manage the technology independently.

This helped me understand the balance between **standardisation and flexibility**, a challenge also explored by Gregor Hohpe in [*Platform Strategy: Innovation Through Harmonization*](https://architectelevator.com/book/platformstrategy/). A platform should provide reusable capabilities that benefit multiple teams, while giving individual teams enough autonomy to address their specific needs.

### Making Responsibilities Clear

Another challenge was ensuring that everyone understood where the Platform Team's responsibilities ended and those of the stream-aligned teams began.

We regularly received support tickets or Slack messages about issues that fell under the consuming teams' responsibilities, particularly around their own CI/CD pipelines.

This wasn't always a technical problem. Often, people simply didn't know where to find our shared responsibility model or other relevant information.

I helped improve the visibility of our shared responsibility model through documentation, FAQs and conversations with colleagues.

I began to see that **clear responsibilities aren't just about defining boundaries. They're also about enabling autonomy**.

When teams understand what they can manage themselves, what the platform provides and when they need support, they can make decisions more independently.

For me, this was another important part of product thinking: understanding not only what the platform should offer, but also what it shouldn't own, and how to help its users succeed within those boundaries.

## The Challenge of Working Across Teams

One thing I hadn't fully appreciated before joining the Platform Team was how challenging it could be to introduce changes that affected multiple development teams.

Our platform supported 14 stream-aligned teams, each with its own priorities, deadlines and dependencies. A change that seemed straightforward from the platform's perspective could have a significant impact on the teams using our services.

For example, retiring an existing technology wasn't simply a matter of deciding to stop supporting it. We first needed to understand which teams were still using it, what they depended on and what would be required for them to move to an alternative.

This meant communicating upcoming changes, identifying dependencies, listening to concerns and coordinating the transition with teams that were also busy delivering their own products.

I learned that even when the technical solution was clear, getting everyone ready for a change could be the more complicated part.

It also made me appreciate the importance of looking beyond our own backlog. As a platform team, our priorities had to account for the needs and capacity of the teams depending on us. You can read more about one of these initiatives in my [Vault to AWS Secrets Manager case study]({{ '/case-studies/vault-migration/' | relative_url }}).

For me, this was another valuable lesson in product thinking: **building a useful platform isn't just about choosing the right capabilities. It's also about understanding how changes affect the people and teams relying on them.**

## Why Platform Teams Still Interest Me

Working in a platform team changed the way I think about building products and supporting the people who use them.

What I find particularly rewarding is the opportunity to make other people's work easier. Developers and other stream-aligned team members should be able to focus on building their products rather than spending unnecessary time navigating complicated processes, waiting for access or figuring out where to find help.

I also enjoy the mix of challenges that platform teams bring. There's technical complexity, but also plenty of opportunities to understand people's needs, question assumptions, bring different perspectives together and make thoughtful product decisions.

And that's what makes the idea of Platform as a Product so interesting to me. It's about remembering that, behind every pipeline, workflow or shared service, there are people trying to get something done.

## Further Reading & Influences

Some of the ideas explored in this article were shaped by conversations with my colleagues and the following resources:

- [*Team Topologies: Organizing Business and Technology Teams for Fast Flow*](https://teamtopologies.com/) — Matthew Skelton and Manuel Pais. A framework for understanding different team responsibilities, interactions and the role of platform teams in enabling stream-aligned teams.
- [*Platform Strategy: Innovation Through Harmonization*](https://architectelevator.com/book/platformstrategy/) — Gregor Hohpe. Insights into platform strategy, standardisation, flexibility and the trade-offs involved in building shared capabilities.
- [*Product Talk*](https://www.producttalk.org/) — Teresa Torres. Articles and resources about continuous discovery, understanding user needs and making product decisions informed by research.

### AI Assistance Note

I used ChatGPT to help structure, refine and edit this article. The experiences, observations and reflections are my own, and I reviewed the final content to ensure it accurately represents my perspective.
