---
fonts:
  sans: Ubuntu
  mono: Ubuntu Mono
---

# From backlog to pull request

Building an AI-augmented development lifecycle

---

# This presentation

<br />

[<carbon-logo-github /> GitHub](https://github.com/fabioscagliola/from-backlog-to-pull-request)

<qr value="https://github.com/fabioscagliola/from-backlog-to-pull-request" />

---

# Intro

I wanted to start with the classic opening question, but...

## Definitions

<v-clicks>

- Agentic factory
- Software delivery/development lifecycle = SDLC
- Vibe coding = 🤢
- Dark factory = 😱

</v-clicks>

---

# Hands up, please ✋

<br />

- Who has seen or built an agentic factory?

<v-clicks>

- Who has seen one succeed?

</v-clicks>

---

# Two real-world projects

<br />

## The factory

An attempt at autonomous software delivery

## Sally

Human-driven AI-augmented SDLC

---
layout: section
---

# The factory

---

# Architecture

<br />

![](/factory-architecture.jpg)

---
layout: two-cols-header
---

# Challenges

<br />

::left::

<v-clicks depth="2">

- The human bottleneck
- Auditability, identity attribution.
  -	Who wrote that code?
  -	Who created that merge request?
  -	Who added that comment to Jira?
  -	What were the permissions of&nbsp;&nbsp;🎃? 
  -	On behalf of whom was&nbsp;&nbsp;🎃 acting?
  -	Who executed that `drop database` in prod?
- Lack of guardrails

</v-clicks>

::right::

<v-clicks depth="2">

- No definition of success
  -	Faster code?
  -	More code?
  -	Lower cost?
  -	More backlog items completed?
  -	Fewer defects?
  -	Less review effort?

</v-clicks>

---

# Main focus

SPIFFE ( https://spiffe.io ) + SPIRE

-	Getting rid of system accounts and shared personal access tokens.
-	Introducing delegated and on-behalf-of identity patterns, currently experimenting with Microsoft Entra Agent ID and agent identity blueprints.
-	Propagating identity attribution beyond the gateways, so that when an agent performs an action on GitLab, Jira, or another system, we can still establish who initiated it and under whose authority it happened.
-	Allowing agents to retrieve current information from the web through an AgentCore Web Search Tool instead of simply giving them unrestricted internet access.
-	Sitting in long meetings with the security folks discussing guardrails, prompt filtering, personally identifiable and highly confidential information, and what may or may not end up in prompts and logs.
-	And last but not least, defining how to measure success after rollout.

---
layout: section
---

# Sally

---

# Where Sally came from

- The documentation was outdated.
- The original architectural principles had been lost over time.
- No one really knew the whole system anymore.
- The only reliable source of truth was the codebase.

pressure on dev team

“Add more developers and give them AI!”

New joiners’ nightmare + veterans’ bottleneck

AI already in use, but mostly for code generation and not consistently

And the backlog kept growing...

---

# Lifecycle

<br />

![](/sally-lifecycle.jpg)

Each agent comes with specific <span v-mark.highlight.yellow>skills</span>, such as <span v-mark.yellow>retrieving the backlog item</span>, <span v-mark.yellow>querying the code graph</span>, or <span v-mark.yellow>creating the pull request</span>, and with guidelines and **templates** for producing the artifacts passed from one stage to the next.

---

# Code graph

in June the costs of AI skyrocketed

search the huge codebase vs. query a structured representation of the codebase and its relationships

query a structured representation of the codebase and its relationships

two custom ingestion pipelines: .NET using Roslyn + React → common graph representation stored in Neo4j

different branches → different graphs

multiple disposable graph databases on one Neo4j instance in the cloud, rebuilding them from the relevant branches on a schedule

custom MCP server + skill

---

# Challenges

balance between introducing the AI-augmented lifecycle and meeting compliance requirements in a highly regulated environment

pragmatic option was to use the models already available through GitHub Copilot

Running the agents on developers’ computers also simplified the problem of identity attribution, delegation, and authorization

centralized LLM and MCP gateways, but approval, policies, politics

Cultural resistance

- “AI stole my job”
- becoming dependent on AI
- no longer building their own understanding of the system. Concerns about
- code quality, maintainability, security, and whether
- anyone would still understand generated code six months later.

---

# Metrics

defining success and deciding how to measure it

built a baseline and then compared results against it over time

delivery, quality, review effort, adoption, and cost

- Time spent clarifying requirements.
- Time spent reviewing agent outputs.
- Time from “ready for development” to “done”.
- Number of backlog items completed per sprint.
- Number of backlog items carried over between sprints.
- Findings during code review, quality assurance, and user acceptance testing.
- Rework required before acceptance.
- Developer feedback on usefulness and friction.
- AI cost per completed backlog item.

precise numbers vs. hard to quantify

---

# Developer feedback

strongest value before coding even started. In refinement, planning, understanding the domain, and getting to a useful first implementation

(quote feedback here!)

development time had been reduced by about 50%

first implementation as roughly 70% good

areas for improvement:

- attachments and visuals
- overkill for small changes such as bug fixes
- model choice

---

# Wrapping up

responsible adoption, regulation

existential risks

(books)

practical risks

- lock a bunch of agents in a dark room and hope they behave
- a factory where nobody really knows what’s happening inside their manufacturing plants
- use AI ethically, responsibly, and with humans being accountable for the outcome

medicine and transportation

---

# Takeaways

- Augment people, don’t replace them.
- Give agents context.
- Build identity attribution, delegation, authorization, accountability, and auditability around agents.
- Measure if and how AI can actually help.
- Always keep human hands on the steering wheel.

---
layout: end
---

# That's all, folks!

<br />

THANKS

