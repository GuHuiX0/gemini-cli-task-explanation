---
name: task-explanation
description: Use when the user asks to understand a technical mechanism, bug, design tradeoff, or code relationship, or says an explanation is unclear, jargon-heavy, or assumes missing background. Not for routine execution requests, command lookup, or brief status updates alone.
---

# Task explanation

Help the user build the smallest sufficient model for their current task. Apply this workflow after Gemini CLI activates the skill. Follow the user's requested language and depth.

## Establish the question

Identify the current goal, decision, or point of confusion from the conversation. Use explicit feedback as evidence of understanding; keep other assumptions tentative. If the task is clear, answer directly. Inspect available repository files, runtime evidence, and conversation context before inferring what remains unresolved. Ask only when the missing information cannot be obtained from the repo, runtime evidence, or the conversation and materially different interpretations would change the explanation. Do not ask the user to restate what could be inspected. When a question is necessary, ask one or two short diagnostic questions about a concrete event or prediction rather than "What is your level?"

## Choose a useful representation

Use the form that exposes the relationship the user needs:

| Question | Useful form |
| --- | --- |
| Why did this happen? | Causal chain |
| How does state change? | State transitions |
| Where does information go? | Data flow |
| Who invokes what? | Call relationships |
| Which event happens first? | Timeline |
| What must remain true? | Invariant: a condition the system must preserve |
| When should we choose A over B? | Decision conditions |
| What happens for this input? | Concrete example or behavior table |

Start with one compact representation, often three to seven concepts. Add another form or more detail when needed for correctness or the user's requested depth. A short paragraph, arrows, or a small table is sufficient; elaborate visuals are optional.

## Explain the mechanism

Connect the model to the current question, then introduce only the identifiers needed to locate or substantiate it. Briefly define any technical concept that is a prerequisite for following the current reasoning and whose meaning has not already been established in the conversation. Give a precise definition and its local role even when the concept is commonly assumed knowledge among developers. Separate observed facts from hypotheses. When code is available, inspect the relevant evidence before claiming how it works; otherwise state assumptions and do not invent identifiers or locations.

Select the relevant branch; these are reasoning guides, not mandatory headings:

- **Bug:** Connect expected behavior, observed behavior, the supported failure mechanism, the condition being violated, and the relationship a fix must change. For an unverified cause, explain what evidence would distinguish it.
- **Tradeoff:** Identify the user's decision and the conditions favoring each option. Give concrete thresholds only when supported; otherwise explain what would need measuring.
- **Code mapping:** Map previously explained concepts to verified functions, variables, or execution paths. Add file locations when available and useful.
- **Repair an explanation:** Use the user's stated difficulty to define the missing term, supply a prerequisite, or change representation. Do not repeat the same explanation with more words. If the gap remains unclear, follow the question rule above.

For a mechanism-level question, give the compact model, the terms needed to understand it, and the principle a fix must preserve. When the user requests implementation, expand into concrete changes and their correctness conditions. When the user asks about a particular missing prerequisite, resolve that prerequisite and reconnect it to the model. Let the requested layer determine the scope of the answer.

For example: `DB commit succeeds -> acknowledgment fails -> message is delivered again -> an unguarded write creates another order`. Acknowledgment tells the queue processing is complete; its failure does not undo the committed order. The fix must preserve one order per logical request across repeated deliveries.

## Control expansion and state

Finish the current explanation at a useful boundary. When helpful, name one next layer or a detail that can be ignored for this task, with its scope. Avoid routine follow-up menus. Continue authorized execution independently of explanatory depth.

Keep the goal, evidence, open questions, and user-confirmed understanding in the conversation. Show a compact state summary only when requested or helpful for a long task. Distinguish confirmed understanding from inferred understanding and unresolved questions. Save a task note when requested; do not persist a proficiency label or treat omitted details as permanently irrelevant.
