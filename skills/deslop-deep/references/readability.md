# Readability: reduce the reader's work

Use this reference during an explicitly requested deep deslop pass when a passage is technically intelligible but takes unnecessary effort to understand. Diagnose the *source of the effort*, then edit at the level of ideas before fixing sentences.

## Editing order

1. **Find the point.** What does the intended reader need to know, decide, or do?
2. **Delete dispensable ideas.** Remove invented rationale, tangents, repetition, and implementation details that do not serve that point.
3. **Put the point first.** State the important fact directly instead of burying it in a modifier or narrating a mechanism.
4. **Unwind the sentence.** Use familiar syntax, clear referents, and conventional technical verbs.
5. **Verify meaning.** Preserve necessary conditions, scope, caveats, and factual claims. Don't invent a missing causal relationship or strengthen a guarantee.

These are diagnostic categories, not a checklist to apply mechanically. A passage may have several problems, or none.

## 1. Unnecessary ideas and manufactured rationale

**Symptom:** The text explains why an obvious recommendation is good, but the explanation adds no information relevant to the decision. The agent may have constructed a plausible justification simply because recommendations often come with one.

**Before**
> Keep examples beside the rules they demonstrate. A separate examples catalog would require another lookup and could duplicate guidance.

**After**
> Include examples for each rule.

**Why:** The actual recommendation fits in one sentence. The extra speculation about lookups and duplication is unnecessary for this context. Don't preserve it just because it was in the draft.

**Watch for:** invented tradeoffs; defensive justifications; explanations of obvious consequences; descriptions of how the agent arrived at a recommendation when the reader only needs the recommendation.

**Exception:** Keep the rationale when the reader must evaluate a genuine tradeoff or understand a non-obvious decision.

## 2. Brain ollies: unexpected parsing or interpretation

**Symptom:** A reader initially assigns a word the wrong grammatical role, loses track of a referent, or must reinterpret an odd verb to make the sentence work. A *brain ollie* is the mental maneuver required to recover the intended meaning.

**Before (illustrative)**
> The parser reports the indices the function's matching elements expose.

**Possible after, only if confirmed by the code**
> The parser returns the indices of matching elements.

**Why:** The original makes the reader unpack stacked noun phrases and an unusual use of “expose.” The revision states the result directly. The original also mentions the function; don't remove that relationship if it matters.

**Look for:** words used in unexpected noun/verb roles; surprising subject–verb pairings; stacked possessives; unclear pronouns; sentences that become clear only after rereading.

**Do not:** rewrite unfamiliar but standard technical terms merely because the editor doesn't recognize them.

## 3. Pretzel sentences: tangled relationships

**Symptom:** Several relationships are folded into one clause, often with nested modifiers. The reader must reconstruct the sequence of events or dependencies.

**Before (illustrative)**
> The parser reports the indices the function's matching elements expose.

**After, if the intended behavior is that the parser returns indices**
> The parser returns the indices of matching elements.

**Why:** The important relationship is now the main clause. If the function's role is necessary, state it separately after checking the implementation.

**Editing tactic:** Identify the main actor, action, and result. Put those in a plain sentence. Add a second sentence only for relationships the reader actually needs.

**Do not:** split every long sentence. A long sentence with a familiar structure can be easier to read than several cryptic fragments.

## 4. Semantic compression and misplaced emphasis

**Symptom:** The writer packs the main point into a relative clause, or combines mechanism and consequence in a way that forces the reader to infer why the detail matters.

**Before**
> **Passwords stay out of the transcript.** `fill --secret-cmd 'pass show site'` types a secret the agent never sees in replies. 1Password and Bitwarden CLIs work too.

**After, only if the security guarantee is verified**
> Secrets are passed directly to the browser without exposing them to the agent. 1Password and Bitwarden CLIs are supported.

**Why:** The original foregrounds the command's mechanics and hides the useful security property in “a secret the agent never sees.” For a feature overview, state the capability. Put command syntax in a usage example if readers need it.

**Accuracy check:** “Never appears in replies” is not necessarily equivalent to “the agent cannot access it.” Do not strengthen the claim without evidence.

**Look for:** “X returns Y that Z never uses”; “A does B the user never sees”; main points buried in *that/which/where* clauses; implementation narration where the reader needs a feature or conclusion.

## 5. Unnatural technical language and false agency

**Symptom:** A software component is given an odd human action, or a human term is used for a relationship between software components. The sentence is decodable but not conventional developer English.

**Before**
> The array spells its indices differently.

**After, if accurate**
> The array uses a different index format.

**Why:** “Spells” is a distracting verb for an array. Name the actual formatting difference when known.

**Before (illustrative)**
> The function returns an output tree that nobody reads.

**After, if `meta` is the unused part**
> No callers use the `meta` field in the returned value.

**Why:** “Nobody” suggests people, but the intended claim concerns software consumers. The rewrite names the specific unused part rather than implying the entire return value is unused.

**Important distinction:** Conventional technical agency is fine: “the function returns,” “the buffer holds 64 bytes,” “the request arrives,” and “the compiler rejects the program” are ordinary expressions. Don't replace them with awkward human actors.

## 6. Unexplained referents and private shorthand

**Symptom:** The agent uses a label it learned while inspecting the repository, but the reader hasn't been told what it refers to. The sentence may be grammatically simple and still be incomprehensible.

**Before (illustrative)**
> Fix the list front run before updating the barrel.

**After**
> Identify the specific list operation and export file, then describe the required change using their actual names.

**Why:** The original does not establish what “list front run” means or which barrel file is involved. This is an editing instruction, not a factual rewrite: the missing details must come from the source material.

**Terminology note:** A *barrel file* is a legitimate JavaScript/TypeScript term for a module that re-exports symbols. Don't treat established jargon as invented. Define or identify it when the audience needs that context; don't call an entire styling library a “barrel” unless that is actually what the term refers to.

**Look for:** “the list front run,” “that path,” “the latter,” unnamed components, ambiguous abbreviations, or labels meaningful only to an agent that just read several files.

## 7. Agent-centric abstraction

**Symptom:** The text describes ordinary reader activity using the vocabulary of search, retrieval, resolution, or internal workflow, adding distance without adding precision.

**Before**
> A separate examples catalog would require another lookup.

**Better, if that detail genuinely matters**
> Readers would need to open another file to find the examples.

**Best, if it doesn't matter**
> Delete the sentence.

**Why:** First ask whether the claim belongs in the document at all. Only then translate the abstract operation into the actual reader experience.

**Do not:** ban “lookup,” “resolve,” or “retrieve” when they name real technical operations.

## Editing safeguards

- **Deletion beats paraphrase** when an idea is irrelevant. Do not turn one unnecessary sentence into two elegant unnecessary sentences.
- **Precision beats brevity** when a condition, security guarantee, failure mode, or API contract matters.
- **Reader context beats agent context.** The agent's investigation history is not shared knowledge.
- **Familiar language beats clever language**, unless the unusual phrasing is established terminology or genuinely clarifies the concept.
- **Don't manufacture specificity.** If the original is ambiguous, consult the code or flag the uncertainty rather than guessing.
- **Avoid blanket bans.** Passive voice, inanimate subjects, relative clauses, em dashes, and long sentences can all be appropriate.

## Final test

Read the revision as someone who has not seen the agent's investigation. Can they identify the main point immediately, understand every necessary referent, and avoid rereading? Is every retained idea useful? Did the edit preserve the technical meaning?
