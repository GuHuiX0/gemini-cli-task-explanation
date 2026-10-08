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

Choose the smallest representation that exposes the required relationship: prose, causal chain, state transition, data flow, call relationship, timeline, invariant, decision conditions, or concrete prediction. Select facts for the current question, using the broader evidence to verify them rather than summarize it. Before returning the answer, remove details whose removal leaves that question answered accurately and coherently; defer them to their own requested layer.

- **Term only:** Use the shape "[Term] means [precise functional definition]. Here, it [direct local function]." Put necessary prerequisite definitions inside those sentences. This is the complete default answer; variants, internal mechanisms, and architectural benefits belong to questions requesting them. Honor an explicitly requested format or deeper scope.
- **Overall model:** State the purpose, connect input or starting state to the result, and explain how the stages depend on one another. Use the domain terms already present. Finish with that connection; statement-by-statement mapping and worked examples belong to requests for those layers.
- **Bug mechanism:** Give the supported failure chain and the condition that permitted it. Concrete repair steps belong to a request for a fix.
- **Code mapping:** Inspect both the implementation and the actual caller. Map the established concept to verified code and identify an inactive or bypassed path. Do not re-teach the established concept.
- **Decision:** State when the current choice fits and when the alternative becomes preferable. When citing measurements, retain the statistic, value, unit, and workload: a percentile is not a fixed duration or an average. Connect meaningful failure modes to the choice; retain uncertainties rather than inventing thresholds.
- **Application:** Propose the first observation tied to the model, then check whether another cause could produce that same observation. A signal shared by competing causes is a clue, not confirmation. Identify the additional identity or event-sequence linkage needed to distinguish them, using available observations or explicitly required instrumentation.
- **Relevance:** Give the relationship needed for the task and the scope of details that can be deferred. A request about what to understand before a fix is not a request for patch instructions; provide those when the user asks for implementation.

Check the technical prerequisites of the chosen relationship against meanings already established in the conversation. Mere mention of a term, or its commonness among developers, does not establish its meaning. Briefly define missing necessary links, including prerequisites used inside a definition, or use equally precise wording that avoids them. Prefer direct descriptions of behavior to unnecessary new labels. Use analogies only when requested.

Provide complete implementation detail, background, examples, or multiple layers when explicitly requested. When an explanation misses the gap, change the intervention instead of making the same explanation longer.

## Preserve collaboration

Continue authorized work without comprehension checks; respect explicit teaching or discussion-only requests. Keep confirmed understanding distinct from inference. Keep task-specific goal, evidence, open questions, and understanding in the conversation; show or save a task note when useful for continuity or requested. Do not infer a permanent proficiency label.
