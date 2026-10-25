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

## 1.

Overall accuracy on the held-out test split is at least **0.70** on every one of the three seeds (42, 7, 2024).

**Why this target:** My three labels split by topic (on-screen content, off-screen news, open question), not by tone, and news posts carry strong word signals like "renewed", "premiere date" and "cast as", so the model should beat the 0.33 guessing rate by a lot. I didn't go higher because the test split is only about 30 posts, so each mistake costs about 3 points and one bad seed could drop the score 6 to 9 points below the others.

---

## 2.

Every label (`show_discussion`, `industry_news`, `general_question`) has an F1 of at least **0.60** on every seed.

**Why this target:** One strong label shouldn't be allowed to hide a weak one, so I set a floor for each label. It's looser than the accuracy target because my smallest label will probably have only about 8 test posts, and an F1 on 8 posts can swing 0.15 between seeds. I expect `general_question` to be the small one, because r/television's front page is mostly news.

---

## 3.

In `labels.csv`, no label is more than **50%** of the rows and none is less than **20%**.

**Why this target:** r/television is heavily skewed toward news links. If I labelled what I scrolled past, `industry_news` would probably be 60% or more and the model could score well just by guessing news. Keeping every label at 20% or more (about 40 of 200 posts) means each one has enough examples in training and in the test split.

---

## 4.

When I label the 30 staff posts under `data/staff_taxonomy.md`, I agree with the staff labels on at least **21 of 30 (0.70)**.

**Why this target:** That taxonomy is someone else's, and it sorts by tone (`analysis` / `hot_take` / `reaction`), which is harder to judge than my topic labels, so I don't expect 90%. Still, guessing gets about 10 of 30. If I can't apply written rules at 70%, my own 200 labels are probably inconsistent too, especially on the `industry_news` / `show_discussion` boundary.

---

## 5.

On every seed, accuracy on the model's most confident third of test posts is at least **0.15 higher** than on its least confident third (from `results.json` → `confidence`).

**Why this target:** I expect the uncertain posts to be the ones on my hardest boundary, where news links come with the poster's opinion added, and the confident ones to be clear headlines and clear "what show should I watch" questions. With about 10 posts in each third, one post is worth 0.10, so a one-post gap could be chance. 0.15 means at least two posts' difference. If the model is as accurate on its unsure posts as on its sure ones, its confidence score tells me nothing.

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
