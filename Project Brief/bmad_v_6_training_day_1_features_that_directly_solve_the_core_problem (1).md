# BMAD v6 Training – Day‑1 Features That Directly Solve the Core Problem (Refined)

This document defines the **minimum concrete product surface** required for BMAD v6 Training to solve its core problem on Day 1.

It exists to close a critical gap identified in the commercial viability review:

> **“Judgement philosophy is not a product unless it has something a learner can actually do on login.”**

This refinement tightens the feature set, clarifies behavioural intent, and removes residual ambiguity between *teaching judgement* and *creating a judgement environment*.

---

## What Was Slightly Overstated

### 1. “Exactly five things” risked false rigidity

**Original risk**: Over‑literal interpretation of the five screens as sacred UI objects.

**Refinement**:
- The five elements are **functional constraints**, not fixed pages
- They may collapse or expand in UI so long as the constraint is preserved

**Design implication**: Preserve *behavioural enforcement*, not screen count.

---

### 2. Eligibility as a full session terminator needed nuance

**Original risk**: Ending the session could feel punitive or broken.

**Refinement**:
- Eligibility failure should feel like **successfully stopping**, not rejection
- The system should explicitly reinforce:
  > “Stopping here is correct.”

**Design implication**: Termination copy matters as much as the gate itself.

---

### 3. Artefact generation risked feeling automatic

**Original risk**: Auto‑generated artefacts could imply judgement outsourcing.

**Refinement**:
- The artefact must be **assembled from learner input**, not inferred
- Any generation is formatting, not reasoning

**Design implication**: No summarisation that replaces thinking.

---

## What Was Missing

### 1. Psychological orientation on entry

**Missing element**: A brief but explicit posture‑setting moment.

**Refinement**:
Day 1 requires **one short orientation sentence** before any interaction:

> “This is not training content. This is a decision environment.”

Nothing more.

---

### 2. A clear exit state

**Missing element**: What *done* feels like.

**Refinement**:
- Day 1 must end decisively
- No implied continuation
- No “next step” temptation

The learner should leave thinking:
> “That decision is finished.”

---

### 3. Explicit irreversibility signal

**Missing element**: A marker that something has changed.

**Refinement**:
- The Stop/Go action should visually and linguistically signal finality
- Re‑opening should be possible, but framed as *reconsideration*, not continuation

---

## Refined Day‑1 Feature Set (Behaviour‑First)

Below is the **irreducible functional set**, independent of UI layout.

---

## 0. Orientation (Single Sentence)

**Learner sees**:

> “You are not here to learn BMAD. You are here to decide.”

Then the system immediately asks for a real decision.

---

## 1. Eligibility Constraint (Stop Is Success)

**Function**:
Force an explicit choice about whether to proceed.

**Learner must**:
- State why the decision deserves structure
- Acknowledge at least one decision that does *not*

If they stop:
- The system confirms correctness
- No further prompts appear

---

## 2. Declaration Constraint (Ownership Lock)

**Function**:
Prevent proxy authority.

**Learner must**:
- Declare the decision in first‑person terms
- Acknowledge they own the outcome

Disallowed language is blocked.

No examples shown.

---

## 3. Sufficiency Constraint (Central Move)

**Function**:
Train stopping confidence.

**Learner must**:
- Name what is enough
- Name what is excluded
- Name the accepted risk

All fields are mandatory and short.

This is the core learning event.

---

## 4. Artefact Assembly (Two‑Minute Defence Test)

**Function**:
Make judgement legible without expansion.

**Learner sees**:
- A minimal artefact composed entirely of their inputs
- One prompt only:
  > “Could you defend this in under two minutes?”

Optional: time‑boxed defence recording.

---

## 5. Stop / Go Commitment (Irreversibility Marker)

**Function**:
Convert clarity into action.

**Learner must choose**:
- Commit
- Or explicitly not proceed

If commit:
- One downside is named
- One reconsideration trigger is named

The decision is then marked **complete**.

---

## The Exit State (Critical)

When finished, the learner sees:

> “This decision is complete. You may now act on it.”

No next module.
No upsell.
No progress indicator.

Silence is intentional.

---

## What Is Still Absent (Reaffirmed)

- Content libraries
- Video instruction
- Metrics dashboards
- Social features
- Achievement indicators

Their absence is not an MVP gap.
It is the product.

---

## Why This Still Solves the Core Problem

In a single session, the learner:

- Stops unnecessary work
- Owns a decision
- Names sufficiency explicitly
- Produces a defensible artefact
- Commits with eyes open

Judgement is restored through action, not explanation.

---

## Final Product Test (Refined)

If a learner completes Day 1 and says:

> “I didn’t realise how much I was over‑working decisions until this forced me to stop.”

Then the product works.

If they ask:
> “What should I do next?”

Then the design has failed.

---

*This document should be treated as the definitive Day‑1 product specification for the BMAD v6 Training Programme. Anything added must prove it strengthens constraint, irreversibility, or ownership — not comfort, clarity, or continuation.*

