+++
categories = ["Blog Posts", "Traveldoo", "Work"]
date = "2020-03-09T19:02:59+02:00"
description = "This is the start of a series of regular updates from myself on different topics that are important to our customers. In this blog post, I’m going to focus on how we have been organising ourselves as we go global. Traveldoo is now present in 65 countries and the amount of daily traffic is growing significantly outside of Europe. We have invested in our people in order to maintain our platform, for T&E, in both India and Paris. We are onboarding dedicated support team members into our team in India this quarter. As well as a major reboot of the tooling for how we monitor our platform and respond to incident, we are about to roll out a completely new process for how we handle incidents and bugs. Finally, we are going through a major change for our engineers in Paris and India as more of our teams will be going on call to provide additional 24/7 coverage."
draft = "false"
keywords = ["Traveldoo", "CTO"]
slug = "cto-update-going-global"
title = "CTO Update - Going Global"
type = "post"

+++

![Traveldoo Reception](/img/cto-update-going-global/header.jpg)

Hi Folks, I’ve now been at Traveldoo for six months and wanted to introduce myself and give you an update on what we are doing. It has really been great to be onboard with the team at Traveldoo.

<!--more-->

A little about me: I’m Northern Irish and live in Paris with my family. I’ve been working in technology my whole career – with quite a diverse background. I started out as a developer but have done all sorts of fun things; including starting my own business, launching a co-working space and startup incubator for Cameroonian entrepreneurs and I’ve even worked in sales! That said, I have never worked in the Travel and Expense industry. I’m enjoying the new challenge and particularly, getting to know each of you. I learn so much from every interaction I have with you, our customers and partners. If we haven’t met, I hope to meet you in the coming months. Don’t hesitate to get in touch – whatever the topic you have in mind.

This is the start of a series of regular updates from myself on different topics that are important to our customers. In this blog post, I’m going to focus on how we have been organising ourselves as we go global. Traveldoo is now present in 65 countries and the amount of daily traffic is growing significantly outside of Europe.

_We have invested in our people in order to maintain our platform, for T&E, in both India and Paris. We are onboarding dedicated support team members into our team in India this quarter. As well as a major reboot of the tooling for how we monitor our platform and respond to incident, we are about to roll out a completely new process for how we handle incidents and bugs. Finally, we are going through a major change for our engineers in Paris and India as more of our teams will be going on call to provide additional 24 / 7 coverage._

Here is a look at Traveldoo updates in terms of People, Process and Technology.
## People

There are four key teams in our business that you rely on for 24 / 7 global coverage and uptime for our platform.

*     Platform Team (Infrastructure and our shared services)
*     Engineering (the application itself)
*     Technical Support (Engineers that provide support to our Support team and who coordinate around our major projects)
*     Support (first and second line customer support)

Most of our Travel product’s engineering team is based in India and our Expense product’s engineering team is based in Paris. To date all of our other teams (Support, Technical Support, Platform) have only been in Paris. This has required a small team of very dedicated individuals to provide out of hours support for our product. Since September we have been hiring into our team in India so that we can have two major parts of the world covered by regular office hours.

Our current progress is:

*     Platform Team – we now have dedicated engineers on our Platform team in India. They have been fully onboarded into the team.
*     Engineering – we still have all of our Expense engineers collocated in Paris but Traveldoo does have engineers in both Paris and India. More on this in the process section below.
*     Technical Support – we have onboarded new members into our Technical Support team in India.
*     Support – we have also been hiring for these roles in India. It has taken some time due to the quality of the profile we have been looking for.

In addition, we are kicking off a major change for our engineers. We are going to have engineers on-call 24 / 7. As you can imagine this is a significant change for all of us. This means we have added significant new capacity to our teams to provide global coverage. Through this, we are standing up a much wider team to provide full 24 / 7 out of office hours coverage through an on-call rota.
## Process

As you can imagine, the changes to be able to provide this level of service has an impact on our processes:

*     We have just been through a major piece of work at all levels of the company to define how we handle incidents and have established a brand-new process that we are starting to roll out. This should significantly improve our response time as well as provide a general level of improvement in customer communication and responsiveness.
*     We have been testing a new bug prioritisation and analysis process with our Expense teams that has resulted in a major catchup on bugs. We have now rolled this change out to our other product teams as well.
*     We have been using the learnings in dealing with some of our customers to learn and improve how our support, technical support and engineers are working together.
*     Our team in support have also made significant progress in adopting a new methodology in support called Swarming and the results in terms of response time on tickets and meeting our SLA as well as reducing our backlog have been really promising.

Honestly these simple bullet points can’t fully summarise the level of impact that all of these changes we’re currently making will have on our internal processes – but it is vast.
## Technology

On a tools and technology level we have made many changes and continue to invest in this area:

*     We have made changes to the configuration of Zendesk to improve how the tool serves you.
*     As an organisation, we are part way through integrating Zendesk with the ticketing system our engineers use (Jira) so that the two can be automatically linked – we are currently relying on a manual process in our support team to keep things up to date and this is often letting the service down. We are about to trial an integration between the two tools. Our goal is to give all customers much better visibility on where their bugs are.
*     Recently we have tested a new synthetic monitoring tool (Catchpoint) for our products and seen good success with it; we are now putting this in place for all areas of our product. This means we will be monitoring how our product performs from a user perspective, not only for users in France but we will be monitoring our product’s performance from all locations where we have deployed users. The goal is to have full coverage by the end of this quarter.
*     We have also trialed several Application Performance Monitoring (APM) tools and are in the final process of selecting one. This is primarily for our engineers to be able to better monitor and debug how our applications are performing. Through the trial phase we have already discovered and fixed several performance issues in our applications, and so are planning to have this tool fully implemented by the end of March for all our environments.
*     Currently, we are part way through implementing a new alerting tool (PagerDuty). All of our alerts from our different monitoring tools are fed into this tool and managed. This tool is the basis for helping us manage our 24 / 7 coverage as we will use it to put people on a rota, and we will be implementing escalation tiers for incidents that go untouched (for example if a pool of engineers don’t respond, then the alert will go to their manager, then to myself and then to our CEO).
*     As part of the new tooling, we are going to be allowing you to subscribe to alerts for incidents or outages that impact on you with a new page we have been development; our plan is to also integrate this page into Zendesk so that both tools are linked. This tool will eventually be used to provide a timeline and root cause analysis of every major event with each of our customers. Currently we don’t have a definite timeline on this as we are dependent on PagerDuty being fully operational first, but it is very much part of our strategy for driving this forward. This is one of the most significant changes we have planned and will take some time to fully implement. It requires us to invest in training our engineers to be able to communicate better with you, our customers and users.
*     As part of this initiative we will eventually have to implement a new SLA calculation tool. We will put this in place after the other tools above are working well. Our goal here is to give customers better visibility in how we meet our SLAs and the incidents that affected the SLA.

## Wrapping up
## 
I hope you can see that we are making major efforts across the company to put in place a complete and robust approach to supporting our global customers. Of course, this will also improve the product experience for our European customers. The changes are significant, but we have made good progress and I believe you will be able to notice the improvements immediately and as we continue to roll these developments out.

This blog post originally appeared on the Traveldoo Blog [here](https://www.traveldoo.com/en/cto-update-going-global/) and also in [French](https://www.traveldoo.com/cto-update/).
