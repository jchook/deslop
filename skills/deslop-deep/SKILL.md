---
name: deslop-deep
description: Perform an intensive, independent editorial review of human-facing prose using detailed rules and examples. Use only when the user explicitly requests deslop-deep, a deep deslop pass, or this skill by name. Do not activate for ordinary writing, editing, or routine deslop requests.
---

# Deslop Deep

Minimize the reader's effort, not the word count. Edit the ideas before editing the sentences. Preserve facts, necessary qualifications, and the author's intent; do not invent details to make a rewrite sound more specific.

Use this skill for a deliberate editing or audit pass. Ordinary drafting should follow the lightweight core `deslop` policy instead. Do not load every reference by default: read only the files relevant to the problems you find.

## Editing procedure

1. **Find the point.** Determine what the intended reader needs to know or do. Distinguish essential facts from incidental implementation details, speculative rationale, and repetition.
2. **Delete before rewriting.** Remove ideas that add no useful information. Don't polish a sentence that should not exist. Retain necessary conditions, caveats, evidence, and causal explanations.
3. **Fix comprehension costs.** Rewrite brain ollies, pretzel sentences, semantic compression, unnatural wording, and unexplained references. Put the important fact in the main clause.
4. **Remove stylistic slop.** Cut filler, formulaic contrasts, artificial drama, stock metaphors, and repetitive formatting. Do not substitute a different trope.
5. **Verify meaning.** Compare the revision with the source. Check technical claims, scope, negation, conditions, and terminology. If the source is ambiguous, don't silently resolve it by inventing behavior.

For an editing request, return the revised text without a lengthy diagnosis unless the user requests one. For an audit, identify concrete passages and explain the reading burden they impose. Do not rewrite code identifiers, API names, or quoted source material unless asked.

## Failure modes

### 1. Unnecessary ideas and manufactured rationale

A passage can be readable sentence by sentence yet still waste the reader's attention. Delete explanations that do not affect understanding or decisions, especially rationales invented to support an obvious recommendation.

**Before:**
> Keep examples beside the rules they demonstrate. A separate examples catalog would require another lookup and could duplicate guidance.

**After:**
> Include examples for each rule.

**Why:** The additional rationale contributes nothing necessary. Deleting it is better than paraphrasing it.

### 2. Brain ollies and pretzel sentences

A **brain ollie** is an unexpected parsing or interpretation maneuver: a word initially reads as one part of speech, a referent is unclear, or an unusual construction forces rereading. A **pretzel sentence** twists a simple relationship into dense nesting or unnatural word order. Prefer conventional syntax, explicit relationships, and familiar phrasing. A longer sentence is worthwhile if it is easier to understand on the first pass.

**Before:**
> The parser reports the indices the function's matching elements expose.

**Possible rewrite, if confirmed by the code:**
> The parser returns the indices of matching elements.

**Why:** The original nests several relationships and assigns an unusual action to the elements. Verify the actual behavior before removing the function's role.

### 3. Semantic compression and misplaced emphasis

Don't bury the important fact in a relative clause or narrate a mechanism when the reader needs its consequence. State the useful fact directly. Keep implementation details only when they matter to the audience.

**Before:**
> `fill --secret-cmd 'pass show site'` types a secret the agent never sees in replies. 1Password and Bitwarden CLIs work too.

**After, if the implementation supports this guarantee:**
> Secrets are passed to the browser without exposing them to the agent. 1Password and Bitwarden CLIs are supported.

**Why:** The feature and its security property matter more than a compressed account of the command. Check the guarantee: not appearing in replies is not automatically the same as never being visible to the agent.

### 4. Unnatural technical language and false agency

Use established terms in their established senses. Avoid fanciful subject-verb pairings, invented labels, and descriptions of software as human participants. Conventional expressions such as "the function returns," "the buffer holds," and "the request arrives" are fine. Do not ban words mechanically.

**Before:**
> The array spells its indices differently.

**After, if accurate:**
> The array uses a different index format.

**Before:**
> The function returns an output tree that nobody reads.

**After, if accurate:**
> No callers use the `meta` field in the returned value.

**Why:** Describe the actual technical relationship. Avoid "nobody" when referring to software consumers, and name the specific unused portion when known.

### 5. Missing context and cryptic shorthand

The agent may have read files, logs, and prior messages that the reader has not. On first mention, identify unfamiliar symbols, components, terms, or decisions when their identity matters. Do not explain standard terminology unnecessarily or fabricate context. Prefer a concrete referent over phrases such as "the list front run" when the reader cannot identify the thing being discussed.

### 6. Formulaic AI prose

Remove patterns that add performance rather than information:

- Throat-clearing and meta-commentary: "Here's the thing," "It's worth noting," "In this section, we'll explore."
- Contrived contrasts: "It's not X. It's Y," "Not X. Not Y. Z."
- Dramatic fragments and self-answered questions: "The result? Devastating."
- Inflated or vague claims: "game-changing," "important implications," "serves as a testament."
- Magic adverbs and fashionable vocabulary: "quietly," "delve," "tapestry," when they do no real work.
- Repeated em dashes, bold-first bullets, tricolons, and formulaic paragraph endings.
- Unnecessary analogies, over-explained transitions, and repeated summaries.

These are warning signs, not absolute bans. Remove a pattern when it makes the writing less direct, less precise, or more theatrical. Preserve a contrast, passive construction, list, or technical term when it genuinely helps.

## Reference routing

Load references selectively, based on the draft:

| Problem | Reference |
| --- | --- |
| Unnecessary ideas, pretzel sentences, semantic compression, false agency, missing context | `references/readability.md` |
| Filler, stock phrases, business jargon | `references/phrases.md` |
| Contrasts, fragments, rhetorical setups, rhythm, formatting | `references/structures.md` |
| Broader catalog of AI writing tells | `references/tropes.md` |
| Additional before/after rewrites | `references/examples.md` |

The legacy reference files can be retained during migration. Update or prune examples that enforce blanket bans on passive voice, inanimate subjects, em dashes, or three-item lists. The rules in this file take precedence when a reference conflicts with them.

## Final check

- Can an entire idea be deleted without losing useful information?
- Does any sentence force a second reading, unexpected interpretation, or reconstruction of a hidden relationship?
- Is the important point buried in a modifier or incidental mechanism?
- Does the reader have enough context to identify the referents?
- Are any stock AI patterns adding words, drama, or false precision?
- Did the revision preserve facts, qualifications, and technical meaning?

Return the simplest accurate version that serves the reader. Do not add commentary just to demonstrate that the rules were applied.
