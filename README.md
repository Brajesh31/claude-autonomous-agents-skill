# claude-autonomous-agents-skill

A Claude Code skill for designing reliable autonomous agents that plan, use tools, execute multi-step tasks, and recover from failures.

## Overview

Autonomous agents can decompose goals, select actions, call tools, and revise plans based on results. Their reliability decreases as the number of dependent decisions grows. This skill focuses on building agents that are constrained, observable, testable, and safe before increasing their autonomy.

The guiding principle is simple: grant autonomy only when the system has demonstrated that it can use it reliably.

## Core Topics

- Agent loops and state transitions.
- ReAct and plan-execute patterns.
- Goal decomposition and task planning.
- Tool selection and tool execution.
- Reflection and self-correction.
- Memory and context management.
- Guardrails, approvals, and action boundaries.
- Reliability metrics and failure recovery.
- Logging, tracing, and production monitoring.

## Design Principles

### Start with a Narrow Goal

Define one measurable outcome. Avoid vague objectives that allow the agent to take unnecessary actions.

### Constrain Tools

Expose only the tools needed for the task. Validate arguments and permissions at the tool boundary.

### Make State Explicit

Track current goal, plan, completed steps, pending actions, and failure state. Do not rely on hidden conversational assumptions for critical workflow state.

### Add Human Approval for Risky Actions

Require confirmation before destructive, financial, external, or irreversible operations.

### Observe Every Important Step

Record tool calls, outcomes, retries, and errors without logging secrets or unnecessary personal data.

### Measure Reliability

Evaluate task success over repeated runs and realistic inputs. A single successful demonstration is not evidence of production readiness.

## Installation

```bash
git clone https://github.com/Brajesh31/claude-autonomous-agents-skill.git ~/.claude/skills/autonomous-agents
```

## Usage

Invoke the skill when designing or reviewing an autonomous workflow:

```text
/autonomous-agents
```

Provide the agent's goal, available tools, permitted actions, expected environment, and failure constraints.

## Recommended Architecture Workflow

1. Define the task and measurable success criteria.
2. Identify which steps require model judgment and which should be deterministic code.
3. Choose a simple loop or workflow architecture.
4. Define tool contracts and validation rules.
5. Add state tracking and bounded retries.
6. Introduce approval gates for high-impact actions.
7. Add observability and structured logs.
8. Build evaluation cases for normal and adversarial inputs.
9. Run repeated tests before expanding autonomy.
10. Monitor real-world failures and tighten the system.

## Reliability Checklist

- The agent has a bounded objective.
- Every tool has a narrow purpose and validated inputs.
- The agent cannot silently exceed its permissions.
- Retries and loops have explicit limits.
- State survives expected interruptions.
- Failures are visible and recoverable.
- Human approval is required for risky actions.
- Evaluation covers repeated and adversarial runs.
- Monitoring measures task outcomes, not just tool-call counts.

## Repository Contents

- `SKILL.md`: Main autonomous-agent design instructions.
- `README.md`: Architecture principles and reliability checklist.

## Important Note

More autonomy is not automatically better. If a deterministic workflow can complete the task more reliably, use that instead of introducing an agent loop.
