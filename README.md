# Gemini CLI Task Explanation

English customization instructions for technically accurate, task-centered explanations in Gemini CLI.

The goal is to reduce assumed background knowledge while preserving real technical mechanisms. Explanations start with the smallest sufficient model for the current task and expand according to the user's requested depth.

## Contents

- [`GEMINI.md`](GEMINI.md): persistent communication preferences, including contextual terminology definitions, task relevance, progressive expansion, and concrete decision conditions.
- [`skills/task-explanation/SKILL.md`](skills/task-explanation/SKILL.md): an on-demand workflow for explaining mechanisms, bugs, design tradeoffs, and code relationships, or repairing an unclear explanation.

All instructions are written in English. Responses follow the user's requested language.

## Installation

### Persistent preferences

Merge the contents of `GEMINI.md` into `~/.gemini/GEMINI.md` to apply the preferences across projects. Preserve any existing instructions. For project-only preferences, merge into the project's `GEMINI.md` instead.

On Windows, `~` refers to your user profile directory.

### Explanation skill

Copy the `skills/task-explanation` folder into `~/.gemini/skills/task-explanation`. For project-only installation, use `<project>/.gemini/skills/task-explanation` instead.

Start a new Gemini CLI session, or refresh the current session:

```text
/memory reload
/skills reload
```

Check that the preferences and skill were discovered:

```text
/memory show
/skills list
```

Gemini CLI also discovers skills in `~/.agents/skills` and `.agents/skills`. Within the same discovery tier, that alias takes precedence over `.gemini/skills`. Check for a same-name skill there if the wrong version appears. Workspace skill discovery depends on workspace trust.

## Usage

The skill can activate when a request matches its description. You can also request it by name:

```text
Use the task-explanation skill to explain why this request can create duplicate orders.
```

Other example requests:

```text
Give me the smallest sufficient model for this bug.
Map the concepts you just explained to the actual code.
I still do not understand. Identify the missing prerequisite rather than expanding everything.
Under what concrete conditions should we choose A instead of B?
Summarize the current goal, evidence, open questions, and what I have explicitly confirmed I understand.
```

The skill uses Gemini CLI's native activation mechanism, which may present a consent prompt. This repository does not register custom slash commands or change host settings.

## Design boundaries

Persistent instructions establish everyday communication preferences. The skill provides the deeper explanation workflow only when relevant. Task-specific understanding stays in the conversation; an optional task note can be saved when requested.

Simple command lookups remain direct. Controlling explanation depth does not require stopping authorized implementation for comprehension checks. Explicit teaching, discussion-only, or checkpoint requests still control how work proceeds.

## Validation status

This revision is under active behavioral validation; full acceptance has not been established.

Both skill manifests pass the frontmatter and naming validator, and the instruction files are English. Real Codex CLI tests of the shared workflow covered causal mechanisms, actual caller mapping, grounded decision conditions, explanation repair, prerequisite definitions, understanding-state summaries, and relevance pruning. A native test loaded the current skill and answered in the user's requested Chinese.

An earlier Gemini CLI candidate was discovered and activated successfully. Earlier Gemini responses still showed scope and accuracy failures, including excessive architecture detail, lost measurement qualifiers, and unsupported inferences; these informed the current revision. The latest headless generation tests did not return responses, including a minimal request containing only "Reply with exactly OK." Consequently, the latest Gemini behavior remains unverified.

The protocol supplies instructions, not a guarantee that every model response will comply. Use the installation checks above, and evaluate the explanations in your own runtime. No global proxy, model, authentication, or approval settings are changed by these files.

## Official references

Platform conventions were checked on October 7, 2026.

- [Persistent context with GEMINI.md](https://geminicli.com/docs/cli/gemini-md/)
- [Agent Skills lifecycle and discovery](https://geminicli.com/docs/cli/skills/)
- [Creating and troubleshooting skills](https://geminicli.com/docs/cli/creating-skills/)
