# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** None are given. You've had two projects of
practice.

An acceptance criterion names a number. *"The model is accurate"* is an
opinion. *"Every label has an F1 of at least 0.60 on the held-out set"* is a
criterion.

Under each, write a sentence or two on **why that number**. A reason that says
something about your data or your taxonomy earns credit — *"I picked 0.60 F1
for `reaction` because it's my smallest label and I only have about 50
examples of it"*. A reason that could be attached to any project does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## Pick numbers you can defend

Not numbers that sound impressive. Three labels means a coin-flip guesser gets
about 33%, so a target of 0.40 is barely a target. Your number should sit
somewhere you'd honestly call useful.

**Cover at least three of these five areas.** They're here as prompts, not as a
form to fill in — a criterion that fits none of them is fine if it names a
number.

| Area | A question it could answer |
|---|---|
| Overall accuracy | How often does it need to be right to be worth using? |
| Per-label performance | Is one label allowed to be much worse than the others? |
| Balance | How lopsided can your label counts get before it's a problem? |
| Consistency | If someone else labelled the same posts, how often should you agree? |
| Confidence | Should a confident prediction be right more often than an unsure one? |

Two things worth knowing before you pick numbers, because both will affect
whether you hit them:

- **Your smallest label will have the jumpiest score.** If a label has 50
  examples, about 8 land in the test split. An F1 computed on 8 examples moves
  a lot between seeds. A target for that label should be looser than one for
  your biggest label, and saying so is a good reason.
- **Unit 6 tests across three seeds, and the target has to hold across all
  three.** A target of 0.65 against results of 0.71, 0.62, 0.68 is a **miss**.
  Pick with that in mind — it is stricter than it first sounds.

---

# Acceptance criteria — TakeMeter

These targets are recorded before training. Model-performance targets must hold across all three seeds in Unit 6: 42, 7, and 2024.

## 1. Overall accuracy

The classifier achieves at least 65% accuracy on the held-out test set.

**Why this target:** The four labels distinguish the purpose of comments about AI and software careers. I want roughly two-thirds of predictions to be correct despite comments that combine personal experiences, advice, opinions, and questions.

## 2. Macro F1

The classifier achieves a macro F1 score of at least 0.60 on the held-out test set.

**Why this target:** Macro F1 gives each label equal weight. This helps check whether performance extends beyond whichever category appears most frequently.

## 3. Minimum per-label performance

Every label achieves an F1 score of at least 0.50 on the held-out test set.

**Why this target:** The classifier should provide useful predictions for all four categories. This minimum allows for difficult boundaries and small test samples while preventing a completely neglected label from being hidden by the overall score.

## 4. Dataset balance

No label represents more than 60% of the final labeled dataset.

**Why this target:** General opinions may be common in discussions about AI and employment. A 60% limit is stricter than the assignment's 70% maximum and leaves more room for the other categories. If necessary, I will collect additional real examples rather than change correct labels.

## 5. Prediction confidence

On the held-out test set, accuracy for the most confident third of predictions exceeds accuracy for the least confident third by at least 10 percentage points.

**Why this target:** Confidence could help prioritize uncertain comments for human review. A measurable accuracy gap would indicate that the model's confidence helps distinguish more reliable predictions from less reliable ones.



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 6 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath, like this:

         ## 2. Every label performs acceptably

         The model performs well on all labels.

         **Why this target:** ...

         > **Revised in unit 6:** Every label has an F1 of at least 0.60 on
         > the held-out set.
         >
         > **Why revised:** "performs well" gave me nothing to check. I
         > couldn't produce a verdict from it at all.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "Overall accuracy of at least 0.65" → "at least 0.55", because
            0.65 turned out to be optimistic for 200 examples.

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
