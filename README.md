# The Unofficial Guide

**Author:** Sara  
**Corpus:** `campus_life`

---

# Unit 1

## What This Does

This system indexes unofficial student guidance, housing reviews, dining tips, and campus survival advice from the `campus_life` corpus to create a searchable, grounded Q&A search system. It allows incoming students to ask conversational questions about daily life on campus—such as dining hall wait times, dorm conditions, and course grading policies. Every generated response is strictly backed by retrieved source documents and explicitly cites the source file.

## Chunking Strategy

**Chunk size:** 500 characters  
**Overlap:** 100 characters  

The `campus_life` corpus consists of short to medium-length forum posts and student reviews. The default starter chunker used an 800-character fixed window, which resulted in entire posts being treated as massive chunks or splitting distinct multi-topic recommendations right through the middle of a sentence. A 500-character window with a 100-character overlap preserves individual student tips as complete, self-contained thoughts while preserving cross-boundary context between adjacent paragraphs.

## Sample Chunks

**Chunk 1** — source: `dorm_reviews/miller_hall.txt` — produced by: `custom_chunker`

"Miller Hall has the best location near the quad, but the AC units in the south wing break down every September. Bring a box fan for the first three weeks or you won't sleep."

**Chunk 2** — source: `dining_guides/commons_info.txt` — produced by: `custom_chunker`

"Commons dining hall is worth the walk for Tuesday taco bar, but avoid it between 12:00 PM and 1:15 PM unless you want to wait 20 minutes in line."

**Chunk 3** — source: `course_reviews/cs101_smith.txt` — produced by: `custom_chunker`

"Professor Smith's midterms come straight from the slide decks. He does not curve the final exam, so make sure you hit the TAs' office hours early in the term."

**Chunk 4** — source: `campus_life/library_spots.txt` — produced by: `custom_chunker`

"If you need total quiet on weekends, head to the 3rd floor stacks in the main library. The basement gets surprisingly noisy with study groups."

**Chunk 5** — source: `housing/lottery_faq.txt` — produced by: `custom_chunker`

"The housing lottery numbers are generated randomly, but priority groups still apply based on completed credit hours."

## Sample Answer

**Question:** What do students say about wait times at Commons during lunch?

**Answer:**

According to student guides (dining_guides/commons_info.txt), Commons experiences heavy lunch crowds between 12:00 PM and 1:15 PM, leading to wait times of up to 20 minutes. Students recommend visiting outside these peak hours.

**My relevance cutoff:** `0.55`

The cutoff was determined by testing 5 in-scope corpus questions against the 5 `OUT_OF_SCOPE` test questions. In-scope questions yielded low distance scores between 0.28 and 0.44, whereas out-of-scope questions resulted in high distance scores between 0.69 and 0.85. Setting the cutoff threshold at 0.55 cleanly separates relevant content from irrelevant queries.

| Question | In corpus? | Best distance |
|---|---|---|
| What do students say about wait times at Commons during lunch? | Yes | 0.28 |
| Which dorm has issues with air conditioning in early fall? | Yes | 0.35 |
| Does Professor Smith curve the final exam in CS101? | Yes | 0.38 |
| What is the best quiet spot to study in the library on weekends? | Yes | 0.41 |
| Are housing lottery numbers assigned purely at random? | Yes | 0.44 |
| What is the policy for studying abroad in Tokyo during junior year? | No | 0.69 |
| How do I register a personal vehicle for campus parking permits? | No | 0.72 |
| What are the core graduation requirements for major in Astrophysics? | No | 0.78 |
| Where can I buy tickets for off-campus professional sports games? | No | 0.81 |
| What is the menu at the downtown commercial Italian restaurant? | No | 0.85 |

## How I Used AI

**1.** I asked AI to help draft a custom chunking function that splits text on paragraph breaks first before falling back to character limits with overlap. The initial suggestion used external `langchain` library dependencies, so I modified it into a clean, lightweight Python helper function to fit the project's minimal setup.

**2.** I asked AI to review my five initial acceptance criteria to test if they were objectively measurable. It pointed out that my fourth criterion ("Chunks should look clean") was an unmeasurable opinion, so I revised it to require that "at least 4 of 5 randomly selected chunks contain complete sentences without cutting key nouns or facts in half."

---

# Unit 2

## Run Log — Before

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 |  |  |  |  |
| 2. Every answer names a source | 5 of 5 |  |  |  |  |
| 3. Gate stops out-of-corpus questions | 4 of 5 |  |  |  |  |
| 4. Chunk Integrity | 4 of 5 |  |  |  |  |
| 5. Grounded Answer Fidelity | 5 of 5 |  |  |  |  |

## Verdicts

| # | Criterion | Verdict | How I decided |
|---|---|---|---|
| 1 |  |  |  |
| 2 |  |  |  |
| 3 |  |  |  |
| 4 |  |  |  |
| 5 |  |  |  |

## Diagnoses

## The Improvement

**What I changed:**

**Why I picked it:**

### Run Log — After

| Criterion | Target | Run 1 | Run 2 | Run 3 | Verdict |
|---|---|---|---|---|---|
| 1. Retrieved chunk contains the answer | 4 of 5 |  |  |  |  |
| 2. Every answer names a source | 5 of 5 |  |  |  |  |
| 3. Gate stops out-of-corpus questions | 4 of 5 |  |  |  |  |
| 4. Chunk Integrity | 4 of 5 |  |  |  |  |
| 5. Grounded Answer Fidelity | 5 of 5 |  |  |  |  |

**Did it help?**

## What's Still Broken

## What I'd Do Differently