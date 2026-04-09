---
author: Paritosh Baghel
title: "Skills "
date: 2026-04-09
description: "Agent Skills Need a Runtime, Not a Prompt"
tags : [
    "skills", "agent"
]
---

# Agent Skills Need a Runtime, Not a Prompt

Most "Agent Skills" are just large prompts in disguise. If you are using them to run real infrastructure, you are setting yourself up for failure.

Here is what actually happens when you trigger a skill today. Your application dumps the entire skill definition -- rules, instructions, maybe a bash script -- into the LLM's context window, steps back, and says "figure it out." The entire orchestration loop belongs to the AI.

This works fine for text. Ask an LLM to read a messy document and output clean JSON, and it will do it well. Text is its native habitat.

But developers are now using skills to run real workloads: CLI commands, API calls, live infrastructure. That is a different problem. When you load a side-effect-heavy skill into an LLM's context window, you are asking a probabilistic machine to orchestrate a deterministic environment.

Infrastructure does not tolerate a 1% hallucination rate -- especially in a long-running session.

## A Real Example

Let us  Look at [Adyntel Automation](https://github.com/ComposioHQ/awesome-claude-skills/blob/master/composio-skills/adyntel-automation/SKILL.md), a skill that teaches Claude to automate tasks using the Composio MCP. It is well-written. It has prerequisites, setup instructions, and a clear three-step workflow.

But scroll to the bottom and you find a "Known Pitfalls" section:

- "Always search first: Tool schemas change. Never hardcode tool slugs."
- "Check connection: Verify status shows ACTIVE before executing."
- "Memory parameter: Always include memory, even if empty."

That is not documentation. That is a prayer. The developer is begging the LLM to behave like a state machine by relying entirely on its probabilistic reading comprehension to enforce a strict sequence of infrastructure steps.

What happens when the context window fills up? The AI gets confident. It skips Step 1. It hallucinates a hardcoded tool slug from its training data. It forgets the empty `memory: {}` object. Your API crashes.

You wanted to update an address. Now you are debugging a botched JSON-RPC call.

## The Real Problem Is the Architecture

The LLM is not the villain here. The architecture is. We keep handing the AI the wheel for jobs that need a fixed track.

The obvious responses are to abandon Markdown entirely and write code in LangChain, or adopt some drag-and-drop UI builder. Both trade one set of problems for another. You lose the human-readable, version-controlled, agent-friendly format that makes skills useful in the first place.

We built Runeflow to take a different path: keep the Markdown, add the guarantees.

A skill is one `.runeflow.md` file -- YAML frontmatter, plain prose guidance for the LLM, and a fenced `runeflow` block that defines the executable workflow. The runtime owns sequencing, branching, retries, tool execution, and schema validation. The LLM sees only what it needs for its one step.

Here is what that Addresszen workflow looks like in Runeflow:

````md
---
name: addresszen-automation
inputs:
  user_request: string
outputs:
  result: string
llm:
  provider: cerebras
  model: qwen-3-235b-a22b-instruct-2507
---

# Addresszen Automation

Map the user's request to the correct tool payload. Be precise.

```runeflow
step check_connection type=tool {
  tool: composio.manage_connections
  with: { toolkit: "addresszen" }
  out: { status: string }
}

step get_schema type=tool {
  tool: composio.search_tools
  with: { use_case: "Addresszen operations" }
  out: { schema: string, slug: string }
}

step format_payload type=llm {
  prompt: "Map this request to the exact tool schema: {{ inputs.user_request }}"
  input: { schema: steps.get_schema.schema }
  schema: { payload: string }
}

step execute type=tool {
  tool: composio.execute_tool
  with: { slug: steps.get_schema.slug, payload: steps.format_payload.payload }
  out: { result: string }
}

output {
  result: steps.execute.result
}

````

The LLM touches exactly one step. It does not manage state. It does not decide what runs next. It formats a payload and hands off. The runtime handles everything else.

There is no chance it forgets the memory object. There is no chance it skips a step. The sequence is enforced by code, not by suggestion.

## The Assemble Mode

Runeflow has one more trick worth calling out. Run `runeflow assemble` before invoking an agent, and it executes all the deterministic setup steps first -- git reads, API calls, tool discovery. Then it resolves the prompt with real values and writes a clean Markdown context file. The agent loads that file instead of the raw skill. It sees only what it needs for one focused LLM call.

This is how Runeflow cuts input tokens by 82% on orchestration-heavy tasks in our benchmarks. The agent never sees orchestration instructions, tool schemas, or retry logic. It just sees a tight prompt with real data already filled in.

## The Shift

The Markdown skill puts the AI in charge and hopes it reads your pitfalls list. Runeflow moves control flow into the runtime, shrinks the context the LLM has to process, and lets you inspect every step after the fact in a structured run artifact.

That is the right model. Not better prompts. Not longer warning sections. A runtime that treats the LLM as a component, not a conductor.

Agent Skills are a good idea. They just need a proper execution engine behind them.

We are still early and iterating fast. If this problem resonates with you or if you have hit this exact wall with your own skills we would love to hear from you. Open an issue, start a discussion, or just star the repo and follow along on [Runeflow](https://github.com/paritoshmmmec/runeflow).
