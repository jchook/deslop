---
name: deslop
description: Apply clear, economical prose standards automatically when writing or editing developer-facing text, including comments, docstrings, documentation, commit messages, PR descriptions, RFCs, and technical explanations. Also use for ordinary requests to deslop writing. For explicitly requested deep reviews, use deep-deslop instead.
---

# Deslop

Minimize the reader's effort, not the word count.

Apply these rules when drafting or editing prose:

1. **Edit ideas first.** Identify what the reader actually needs to know. Keep information that helps the reader understand something relevant, make a decision, or take action. Remove unnecessary explanations, justifications, qualifications, and tangents. Do not preserve an idea merely because it appears in the draft or is factually correct.

2. **Avoid pretzel sentences and semantic compression.** Don't twist simple ideas into unnatural syntax or pack several relationships into a single sentence. Put the important fact in the main clause instead of burying it in a modifier. Avoid constructions like "a secret the agent never sees" or "an output tree nobody reads" when a direct statement would be clearer. Describe the relevant behavior or conclusion rather than narrating incidental implementation details. Prefer familiar phrasing that readers can understand without mentally reconstructing the intended meaning.

3. **Use ordinary technical language.** Prefer established terminology and conventional verbs. Avoid forced personification, invented labels, and clever metaphors.

4. **Avoid formulaic AI writing.** Cut contrived contrasts ("It's not X. It's Y."), excessive em dashes, dramatic sentence fragments, rhetorical questions answered immediately, inflated claims, and stock phrases ("It's worth noting," "At its core," "This isn't just"). Don't manufacture emphasis or drama.

5. **Establish context.** Identify unfamiliar referents before using shorthand. Don't assume the reader knows everything the agent has discovered. Don't invent facts to fill gaps.

6. **Preserve useful information.** Keep details, conditions, qualifications, and consequences needed for accuracy or understanding. Don't add rationale merely to make a statement sound justified.

7. **State behavior directly.** Identify what performs each action and use conventional verbs that describe what happens. Don't make readers translate metaphors or infer relationships between names and the things they identify. In task headings, name the action the reader can take. Avoid implying behavior beyond the actual scope.


## Examples

**Unnecessary ideas**

Before:
> Keep examples beside the rules they demonstrate. A separate examples catalog would require another lookup and could duplicate guidance.

After:
> Include examples for each rule.

Why: The original invents reasons for a simple recommendation. Delete the unnecessary reasoning instead of polishing it. Convert the odd phrasing to a straightforward sentence.

**Pretzel sentence**

Before:
> The parser reports the indices the function's matching elements expose.

After:
> The parser returns the indices of matching elements.

Why: The original packs several relationships into an unnatural construction. The revision removes the awkward phrasing without inventing additional behavior.

**Unnatural technical language**

Before:
> The array spells its indices differently.

After:
> The array uses a different index format.

Why: "Spells" is an unusual verb for an array. The revision uses conventional terminology without forcing the reader to interpret a metaphor.


**Semantic compression**

Before:
> `fill --secret-cmd 'pass show site'` types a secret the agent never sees in replies. 1Password and Bitwarden CLIs work too.

After:
> Secrets are passed directly to the browser without exposing them to the agent. Supports `pass`, 1Password, and Bitwarden CLIs.

Why: The original compresses the mechanism and security guarantee into an awkward description of the command. The revision states the feature directly and omits unnecessary implementation detail.


**Indirect descriptions**

Before:

> Several services can answer to an event. The event travels through every service that knows its name.

After:

> When an event occurs, the system calls each service registered to handle it.

Before:

> ## An account with no email

After:

> ## Turn off email notifications

Why: The revised sentence states what triggers the action and which services run. The heading identifies the setting being changed without implying that the account loses all email functionality.


## Final Check

Before delivering prose, ask:

- Can I remove or simplify an entire idea without losing useful information?
- Does any sentence require a second reading or an unexpected interpretation?
- Am I assuming context the reader doesn't have?
- Am I using a stock AI writing pattern where a direct statement would work?

