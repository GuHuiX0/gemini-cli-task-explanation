---
name: task-explanation
description: Use when the user asks to understand a technical mechanism, bug, design tradeoff, or code relationship, or says an explanation is unclear, jargon-heavy, or assumes missing background. Not for routine execution requests, command lookup, or brief status updates alone.
---

# Task explanation

Resolve the immediate comprehension gap in the user's requested language. Keep technical accuracy and task execution independent of explanation length.

## Identify the gap and inspect evidence

Use the question and explicit feedback to distinguish a missing definition, missing overall model, missing code mapping, unclear relevance, unclear decision, or difficulty applying an understood model. Address that gap first; this is internal reasoning, not a questionnaire.

Inspect the relevant repository, runtime evidence, and conversation before inferring what remains unresolved. Ask only for material information that cannot be obtained from those sources. Do not ask the user to restate inspectable facts. When a business requirement is genuinely missing, ask one or two concrete questions.

Ground each causal relationship or guarantee in evidence. Preserve measurement qualifiers. Describe transformations the source actually performs, and label inferred intent. A diagnostic observation must distinguish the suspected cause from alternatives, using available fields or explicitly identified instrumentation.

## Match the answer to the gap

Choose the smallest representation that exposes the required relationship: prose, causal chain, state transition, data flow, call relationship, timeline, invariant, decision conditions, or concrete prediction.

- **Term only:** Give one connected paragraph defining what the term denotes and what it does here. Use a functional definition that remains true across the known implementations. Finish after that definition; listing implementations or explaining architectural benefits is a different question.
- **Overall model:** State the purpose, connect input or starting state to the result, and explain how the stages depend on one another. Use the domain terms already present. Finish with that connection; statement-by-statement mapping and worked examples belong to requests for those layers.
- **Bug mechanism:** Give the supported failure chain and the condition that permitted it. Concrete repair steps belong to a request for a fix.
- **Code mapping:** Inspect both the implementation and the actual caller. Map the established concept to verified code and identify an inactive or bypassed path. Do not re-teach the established concept.
- **Decision:** Explain the concrete conditions favoring each option, using measurements and meaningful failure modes. Retain uncertainties rather than inventing thresholds.
- **Application:** Give the first discriminating observation or prediction tied to the model, rather than repeating the explanation.
- **Relevance:** Give the relationship needed for the task and the scope of details that can be deferred. A request about what to understand before a fix is not a request for patch instructions; provide those when the user asks for implementation.

Check the technical prerequisites of the chosen relationship against meanings already established in the conversation. Mere mention of a term, or its commonness among developers, does not establish its meaning. Briefly define missing necessary links, including prerequisites used inside a definition, or use equally precise wording that avoids them. Prefer direct descriptions of behavior to unnecessary new labels. Use analogies only when requested.

Provide complete implementation detail, background, examples, or multiple layers when explicitly requested. When an explanation misses the gap, change the intervention instead of making the same explanation longer.

## Preserve collaboration

Continue authorized work without comprehension checks; respect explicit teaching or discussion-only requests. Keep confirmed understanding distinct from inference. Keep task-specific goal, evidence, open questions, and understanding in the conversation; show or save a task note when useful for continuity or requested. Do not infer a permanent proficiency label.
