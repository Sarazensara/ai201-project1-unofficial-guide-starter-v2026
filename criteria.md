# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

# Acceptance Criteria: The Unofficial Guide

1. **Retrieval Answer Accuracy**: For at least 4 of my 5 test questions, the retrieved chunks include one that contains the answer.
   * *Rationale*: 4 out of 5 allows for edge cases where document terminology differs slightly from natural language queries while ensuring 80% baseline retrieval success.

2. **Source Citation**: Every answer the system produces names at least one source document.
   * *Rationale*: Strict compliance ensures full transparency so users can verify statements against original documents.

3. **Out-of-Scope Relevance Gate**: When I ask a question my documents clearly don't cover, the relevance gate stops it and the system returns "I don't have enough information about that" in at least 4 of 5 tries.
   * *Rationale*: Prevents hallucinations by gating ungrounded queries before reaching the generation phase.

4. **Chunk Integrity**: At least 4 of 5 randomly selected chunks from the index contain complete sentences without cutting key nouns or facts in half.
   * *Rationale*: Ensures the chunking strategy preserves context necessary for the embedding model to represent complete thoughts.

5. **Grounded Answer Fidelity**: For all 5 test questions that pass the relevance gate, 100% of facts in the generated response must originate exclusively from the retrieved context.
   * *Rationale*: Eliminates reliance on parametric background knowledge to keep answers strictly rooted in campus truth.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
