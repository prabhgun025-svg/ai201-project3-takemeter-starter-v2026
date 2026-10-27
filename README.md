# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->
TakeMeter sorts posts from r/television on Reddit into three labels. Some posts
discuss what happens on screen in one specific show, such as a character, an
episode or a season arc (`show_discussion`). Some report news from off screen,
such as a renewal, a release or finale date, casting or an interview
(`industry_news`). The rest ask a general question about TV that people can
answer with any show (`general_question`).


---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `show_discussion`

**Definition:** A post about what happens on screen in one specific show, such as a character, episode, scene or season arc, where the poster gives their own opinion or reading of it.

**Example 1:**
> Could be a case of low expectations but I enjoyed the first two episodes of vampire sitcom Eternally Yours
Seems like the buzz for this hasn't been too positive. I was pleasantly surprised though.

It's going to be compared a lot to What We Do in the Shadows since they both have vampires. Eternally Yours also revolves around a found family as well, I think it's aiming for a different niche.

It feels more wholesome? Definitely comparable to the creator's US adaptation of Ghosts. I say wholesome because they're reformed from killing & two of the couples have their own family.

One has an adopted vampire daughter & the other has half vampire sons with his human wife that doesn't know he's a vampire.

She's learned he's a vampire many times because they aren't particularly careful about it. So they've wiped her mind more times than is probably safe.

One of the half vampire sons is modeled after Edward Cullen type vampires. He's deeply broody & offers up tortured insights that have the surface depth of a spoon. It's my favorite running gag so far.

I think it's got a solid cast with Parker Young, Rose Abdoo, Ed Weeks & Allegra Edwards. I wouldn't be shocked if it gets canceled since it's not your typical CBS show. Ghosts it's still going strong, though. So who knows?


**Example 2:**
I prefer Treme over The Wire
Not to understate how iconic and culturally relevant The Wire is but of the two main David Simon shows out there I’ve always personally preferred Treme (even with its rather rushed five episode fourth episode). The atmosphere was much cozier and ‘slice of life’, the characters were a lot more immersive anr felt like family, and I just loved the emphasis on art, food, music and just generally New Orleans culture

It’s a huge shame to me that Treme never caught on like The Wire did and it’s basically been completely forgotten now (not that it was ever paid much attention to even when it was airing; it’s a miracle to me that we even got three and a half seasons). Although I suppose I do understand why it never did, what with how it basically has like zero plot. It’s solely about the characters and their relationships- complete opposite of The Wire


### `industry_news`

**Definition:** A post reporting something that happened off screen, such as a renewal, cancellation, release or finale date, casting, trailer, ratings or an interview.

**Example 1:**
SNL UK: Meet the Saturday Night Live Weekend Update hosts going viral each week

**Example 2:**
Ryan Coogler’s ‘X-Files’ Update Scores Hulu Series Order

### `general_question`

**Definition:**  A question about TV in general that isn't tied to one show, so people can answer it with examples from any show; if a show is named, it's only an example

**Example 1:**
TV shows with an unaired/unofficial pilot where you’re glad they changed the cast or tone of the show?
I remember a few years ago, I watched the unaired pilot for The Big Bang Theory, which had a different Penny (different actress, different name and I think she was an actual slut?). The guys felt a bit creepier than the sweet awkward nerds we had in the official series and the overall tone felt more mature and sexual.

A few minutes ago, Youtube recommended me the unaired pilot for Big Time Rush. It wasn't my favorite show but honestly I think it was funny for Nickelodeon in those days; and in that pilot you can clearly see how recasting the lead actor (Kendall) might have completely changed the band's dynamic, and why adding a caring, protective mom for a group of boys was so important. -Here's the link in case you're interested: https://youtu.be/HxUYJ0wAcKA

What unaired pilot or original concept have you seen that you think wouldnt have worked? where they made the right call by recasting or changing the tone of the show? Comes to my mind Ren and Stimpy adult version or the Tracey Ullman's version of The Simpsons as well. I think also South Park had an early version before the pilot?

It would be nice if you add the URL to the pilot you mention c: Thanks!



**Example 2:**
Not counting Westerns, what classic TV shows from the 60s do you still enjoy?

### The hardest boundary

**Which two labels:** `industry_news` vs. `show_discussion`. 
**Boundary post:**
>Can't believe Glee (2009) is almost 20 years old. The reboot actually sounds good, with the right people involved, and I have hopes.
 It mentions the reboot announcement, which is news, but nothing new is being reported. The post is the poster's own
feelings about the show. Under the rule below I labelled it `show_discussion`.

**The decision rule I used every time:**
If the post's main point is a new event that happened off screen such as announcements, date, interviews, etc, it's `industry_news`, even if the poster adds an opinion. It's `show_discussion` only when the poster's argument is about what happens on screen and the news is just the reason they're bringing it up or if they are talking about a specific show or movie. 

**Secondary rule (`general_question` vs. `show_discussion`):** If the question can only be answered by people who watched one named show, it's `show_discussion`. If the named show is just an example and people could answer from any show, it's `general_question`.



---

## The Dataset


**Where the posts came from:** 150 posts from r/television on Reddit.
I scrolled through the top and recent posts and deciphered form there 

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->

135 posts were labelled cold: I read each post and chose the label myself based on what would fit 
15 posts are marked `pre-labelled` in the `note` column. I asked claude to label the post for me and see what it would say for the criteria 


**Counts per label:**

| Label | Count | Share |
|---|---|---|
| `industry_news` | 85 | 57% |
| `show_discussion` | 39 | 26% |
| `general_question` | 26 | 17% |
| **Total** | 150 | 100% |

This is below the 200 posts the brief asks for, and it's lopsided toward
`industry_news`, because most of what r/television's feed shows is news links.

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:* #73. "Who is watching Major Crimes? The show is number 5 on the
> Nielsen Ratings for acquired TV shows, beating out Gilmore Girls and Greys
> Anatomy. Who is watching this show? What is the target demographic and why is
> it so successful?"
>
> *Could have been:* `industry_news` (it reports ratings) or `show_discussion`.
>
> *I chose `show_discussion`, because:* the ratings are only the reason for
> posting. The question is about why this one show appeals to people, and only
> people who know Major Crimes can answer it.

**2.**
> *The post:* #10. "Anyone else remember, 'The Hard Times of RJ Berger' 2010 MTV
> Show"
>
> *Could have been:* `general_question` (it's phrased as a question to everyone)
> or `show_discussion`.
>
> *I chose `show_discussion`, because:* by my secondary rule, only people who
> watched that one named show can answer it. It isn't a question you can answer
> with any show.

**3.**
> *The post:* #86. "Offbeat Thriller Phony Is Something Genuinely New on TV:
> Review"
>
> *Could have been:* `industry_news` (a published article, linked like a news
> headline) or `show_discussion`.
>
> *I chose `show_discussion`, because:* a review is someone's reading of what
> happens on screen, not a report of an off-screen event. Looking back, I
> labelled a similar review, #63 ("'Nobody Wants This' Season 3 Has Already
> Learned From Its Season 2 Mistakes | Review"), as `industry_news`. So I didn't
> apply the rule consistently to reviews, and that's a boundary to check in
> unit 6.

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:** `distilbert-base-uncased`

**Settings:** <!-- epochs, learning rate, batch size, seed -->
3 epochs, learning rate 2e-5, batch size 16, 128 tokens per post, seed 42.

Trained on an Apple Silicon GPU (MPS), torch 2.14.1, Python 3.13. Training took
about 17 seconds. The device is also recorded in `results.json`.

**Anything I changed from the defaults, and why:**
Nothing. All the training settings are the defaults. The only notebook edit is
`LABELS`, set to my three labels.

To get the notebook running I had to fix two setup problems:
- My virtual environment was on Python 3.14, which `requirements.txt` doesn't
  support, and training crashed inside `datasets`. I rebuilt `.venv` on Python
  3.13.
- My first labels file wasn't valid CSV, so I converted it into `labels.csv`.

**Split sizes:** <!-- train / val / test, and per-label counts in the test
split. If a label had fewer than about 8 in test, say so — it explains a lot
of next unit's variance. -->
train 104 · val 23 · test 23 (70/15/15, stratified)

| Label | Train | Val | Test |
|---|---|---|---|
| `show_discussion` | 27 | 6 | 6 |
| `industry_news` | 59 | 13 | 13 |
| `general_question` | 18 | 4 | 4 |

`show_discussion` (6) and `general_question` (4) both have fewer than 8 posts
in the test split. One post there is worth 17–25 points of recall, so expect
those labels' scores to swing a lot between seeds next unit.



---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:* I asked claude to evaluate my criteria and see whether it is good or not and whether the posts can fit into each criteria 
- *What came back:* It found that my criteria (1) was too vague and virtually a lot of posts are able to be fit in each of the criterias 
- *What I changed:* I changed the criteria and made it more strict and only made it into headlines or current events from the industry. 
**Moment 2**

- *What I asked for:* to help me find out why the training crashed.
- *What came back:* the crash happened because my `.venv` was on Python 3.14,
  which `requirements.txt` says isn't supported. It rebuilt the environment on
  Python 3.13 and the training ran.
- *What I changed:* I switched the notebook's kernel in VS Code to the new
  `.venv` and re-ran sections 1–5 myself. I got the same `results.json`.

**Pre-labelling disclosure:**
The 15 posts marked `pre-labelled`. I asked claude to label the post for me and see what it would say for the criteria 

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy | 0.565 | 0.565 | +0.000 |
| Macro F1 | 0.415 | 0.241 | -0.174 |
| F1 — `general_question` | 0.000 | 0.000 | +0.000 |
| F1 — `industry_news` | 0.700 | 0.722 | +0.022 |
| F1 — `show_discussion` | 0.545 | 0.000 | -0.545 |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->
I expect the trained model to beat the baseline, around 0.70–0.80 accuracy and 0.60–0.70 macro F1. The biggest gain should be on general_question, which the baseline got completely wrong (F1 = 0). Fine-tuning sees real examples of question-style posts, so it should learn that "asking for recommendations/help" is its own category. I also expect industry_news recall to go up, because the baseline sent news headlines about shows into show_discussion. My worry is that general_question only has a handful of examples, so its F1 may stay low and swing between seeds. The hardest boundary will still be industry_news vs show_discussion, for headlines that are about a specific show.

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->
Fine-tuning added nothing, and on macro F1 it made things worse (0.415 → 0.241). The matching accuracy is a coincidence: the confusion matrix shows the trained model predicted industry_news for all 23 test posts, and 13/23 = 0.565 is just the majority-class rate. With 104 training posts, 57% of them industry_news, and default settings, the model collapsed to the most common label instead of learning the categories. The zero-shot baseline at least split news from show discussion. My prediction (0.70–0.80 accuracy and a gain on general_question) was wrong: general_question stayed at 0, and show_discussion dropped from 0.55 to 0.


---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1. Overall accuracy (held-out) | ≥ 0.70 on every seed | 0.565 | 0.565 | 0.565 | MISSED |
| 2. Per-label F1 floor (min of the three labels) | ≥ 0.60 for every label, every seed | 0.000 (`show_discussion` 0.00, `industry_news` 0.72, `general_question` 0.00) | 0.000 (same) | 0.000 (same) | MISSED |
| 3. Label balance in `labels.csv` | No label > 50%, none < 20% | 56.7% / 26.0% / 17.3% | same (data, not seed-dependent) | same | MISSED |
| 4. Agreement with staff labels | ≥ 21/30 (0.70) | not yet measured | — | — | PENDING (no `data/staff_labels.csv` yet) |
| 5. Confidence gap (top third − bottom third accuracy) | ≥ +0.15 on every seed | 1.000 − 0.143 = +0.857 | 1.000 − 0.000 = +1.000 | 1.000 − 0.000 = +1.000 | MET (but hollow, see below) |

**Device:** all three seeds ran on `mps` (Apple Silicon GPU), torch 2.14.1, `max_length` 128, as recorded in `results_three_seeds_before.json`. Settings: `distilbert-base-uncased`, 3 epochs, learning rate 2e-5, batch 16. Every seed split the data 104 train / 23 val / 23 test.


### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted | show_discussion | industry_news | general_question |
|---|---|---|---|
| **show_discussion** | 0 | 6 | 0 |
| **industry_news** | 0 | 13 | 0 |
| **general_question** | 0 | 4 | 0 |

(Seed 42. Seeds 7 and 2024 produced the identical matrix.)

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->

The biggest off-diagonal number is 6: all 6 real `show_discussion` posts were called `industry_news`, and 0 went the other way. All 4 `general_question` posts went to `industry_news` too. So the model didn't learn the `show_discussion` / `industry_news` boundary at all. It didn't learn any boundary: the whole `industry_news` column is filled and the other two columns are empty. The model collapsed to the majority label (85 of 150 posts, 56.7%) and predicts it for every post on every seed. The mistakes all run one way, into `industry_news`. That points to class imbalance and too little training data, not to a confusing pair of labels. If the model were stuck on a hard boundary, some errors would go the other way.



---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 | Overall accuracy | ≥ 0.70 on every seed | MISSED | 0.565 on all three seeds, which is below 0.70 every time. It is also exactly 13/23, the share of `industry_news` in the test split. |
| 2 | Per-label F1 floor | ≥ 0.60 for every label, every seed | MISSED | `show_discussion` and `general_question` both have F1 0.00 on all three seeds. Only `industry_news` (0.72) clears the floor. |
| 3 | Label balance in `labels.csv` | No label > 50%, none < 20% | MISSED | Counted `labels.csv`: `industry_news` 85/150 = 56.7% (over 50%), `general_question` 26/150 = 17.3% (under 20%). `show_discussion` 39/150 = 26.0% is fine. Seeds don't affect this one. |
| 4 | Agreement with staff labels | ≥ 21/30 (0.70) | PENDING | Can't score it: I never received `data/staff_labels.csv` from my TF, and my email asking for it got no reply, so `agreement.py` can't run. |
| 5 | Confidence gap | ≥ +0.15 on every seed | MET | Gaps of +0.857, +1.000 and +1.000 all clear +0.15. But the model predicts `industry_news` for every post, so "confident" just means "looks like news". The top third is real news posts (always right) and the bottom third is everything else (always wrong). It meets the number without showing the confidence score is useful. |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->

**Criteria 1 and 2: too few examples, made worse by imbalance.** The confusion matrix is one filled column. All 23 test posts were predicted `industry_news` on all three seeds, with zero spread. That is a model that collapsed to the majority label, not a model that confused two labels. If the cause were a genuinely hard pair, like news posts with an opinion added versus `show_discussion`, I would expect errors in both directions between those two labels, and `general_question` would still mostly come out right, because questions look very different from either. Instead `general_question` got 0 of 4 right too. On every seed the model had 104 training posts: 59 `industry_news` (57%), 27 `show_discussion` and only 18 `general_question`. It also barely trained: 104 posts at batch size 16 is 7 weight updates per epoch, so 21 updates in total over 3 epochs at learning rate 2e-5. That is too little signal for it to learn anything beyond "say the most common label".

**Criterion 3: a labelling choice, not a model problem.** I labelled roughly what r/television's front page shows, which is mostly news. My criterion warned that would push `industry_news` to 60% or more, and I didn't fix it before training. This miss is also a likely cause of the miss on 1 and 2: the imbalance is what makes always guessing news the easiest way to lower the loss.

**Labelling problem or model problem?** I couldn't use the agreement report as evidence here: I never got `data/staff_labels.csv` from my TF, and my email asking for it went unanswered. If I had it, the report would show whether I apply written rules consistently. If I'm at or above 21/30 and few disagreements are pile (a), my labels are probably consistent. Then the misses on 1 and 2 are a data-quantity and balance problem: add `general_question` and `show_discussion` posts instead of relabelling. If I'm well below 21/30, or most disagreements are pile (a), my 150 labels are probably inconsistent too, especially on the `industry_news` / `show_discussion` boundary. Then I should re-check those labels before adding more data. Even before that report arrives, the collapse already points to quantity and balance as the main cause: inconsistent labels would produce mixed errors, not the same prediction for every post.



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** not available. I did not receive `data/staff_labels.csv` from my TF, and my email asking for it got no reply, so `agreement.py` could not be run and there are no disagreements to adjudicate.

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**2.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**What the pattern in my disagreements tells me:**



---

## The Improvement

**What I changed:** `EPOCHS` from 3 to 10. Nothing else changed: same `labels.csv`, same three seeds (so the same splits), same model, learning rate 2e-5, batch 16, `max_length` 128, device `mps`.

**Which diagnosis pointed at it:** The misses on criteria 1 and 2. The before run predicted `industry_news` for all 23 test posts on every seed. With 104 training posts at batch 16, 3 epochs is only 21 weight updates at a small learning rate. That is enough to learn the label prior (57% news) but not the words that separate the labels. If the collapse came from too few updates, training longer on the same data should break it. If it came from the labels themselves, training longer shouldn't help. I picked this over rebalancing `labels.csv` because the only way to rebalance without new posts is to delete `industry_news` rows, and that would make the "too few examples" problem worse.

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1. Overall accuracy (held-out) | ≥ 0.70 on every seed | 0.696 | 0.870 | 0.957 | MISSED (seed 42 is 0.004 short, 16/23) |
| 2. Per-label F1 floor (min of the three labels) | ≥ 0.60 for every label, every seed | 0.364 (`show_discussion` 0.36, `industry_news` 0.82, `general_question` 0.75) | 0.727 (`show_discussion` 0.73, `industry_news` 0.93, `general_question` 0.86) | 0.857 (`show_discussion` 0.92, `industry_news` 1.00, `general_question` 0.86) | MISSED (seed 42 `show_discussion`) |
| 3. Label balance in `labels.csv` | No label > 50%, none < 20% | 56.7% / 26.0% / 17.3% | same | same | MISSED (data unchanged) |
| 4. Agreement with staff labels | ≥ 21/30 (0.70) | not yet measured | — | — | PENDING (no `data/staff_labels.csv` yet) |
| 5. Confidence gap (top third − bottom third accuracy) | ≥ +0.15 on every seed | 1.000 − 0.286 = +0.714 | 1.000 − 0.857 = +0.143 | 1.000 − 0.857 = +0.143 | MISSED (seeds 7 and 2024 are short by one post) |

**Device:** all three seeds ran on `mps` (Apple Silicon GPU), torch 2.14.1, `max_length` 128, as recorded in `results_three_seeds_after.json`.

**Confusion matrix, seed 42 (the weakest seed):**

| true \ predicted | show_discussion | industry_news | general_question |
|---|---|---|---|
| **show_discussion** | 2 | 3 | 1 |
| **industry_news** | 2 | 11 | 0 |
| **general_question** | 1 | 0 | 3 |

**Did it help, and how do I know:** Yes, clearly, but not enough to meet any criterion on all three seeds. Accuracy went from 0.565 / 0.565 / 0.565 to 0.696 / 0.870 / 0.957. Macro F1 went from 0.241 on every seed to 0.643 / 0.838 / 0.927, now well above the zero-shot baseline's 0.415. The collapse is gone: on every seed the model now predicts all three labels. `general_question` went from F1 0.00 to 0.75–0.86, and 3 of its 4 test posts are right on every seed. The before-and-after comparison is fair because the seeds, splits and data are identical and only the epoch count changed.

Two caveats:
- Criterion 5 went from a MET to a  MISS. Before, the confidence gap only separated news from not-news, because news was the only prediction. Now the model makes real predictions, and on seeds 7 and 2024 its least-confident third scores 6/7. That is just one post short of the +0.15 gap. Seed 42's gap is +0.714, so the confidence score does mean something, but with 7 posts per third the measure can't separate a 0.14 gap from a 0.15 one.
- Accuracy now spreads 0.261 across the three seeds (0.696 to 0.957). The before run showed zero spread only because the model gave the same answer for every post. With 23 test posts, one post is worth 0.043. Some of the difference between seeds is the model, and some is which 23 posts each seed happened to put in the test split.

---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->

**Criteria 1 and 2 (seed 42).** Seed 42's errors are almost all on the `show_discussion` / `industry_news` pair: 3 discussion posts were called news and 2 news posts were called discussion. That's an error in both directions, the "genuinely hard pair" pattern, and it's the boundary I flagged as hardest in my taxonomy: news headlines about one specific show. Next I would collect more `show_discussion` posts (only 27 in training) and more examples of opinionated posts about a show's news. Then I would re-check those boundary rows against my decision rule once the agreement report tells me whether I apply rules consistently. I stopped at one change because the brief asks for one, measured cleanly.

**Criterion 3.** Training longer doesn't change the data. The fix is collecting about 15 more `general_question` posts and 10 more `show_discussion` posts, which would bring 150 rows up toward the 200 the brief asks for. I didn't do it in this unit because new posts need careful labelling, and adding them would also change the test splits, which would make before and after no longer comparable.

**Criterion 4.** Still pending. I never received `data/staff_labels.csv` from my TF, and my email asking for it got no reply, so `agreement.py` couldn't be run.

**Criterion 5.** Missed by one post on two seeds. More test posts per third (a bigger dataset) would show whether this is a real miss or noise.

**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->

I meant `show_discussion` vs `industry_news` to depend on whether the post is about what happens on screen or off screen, but the model seems to go by surface cues like a show's name and headline-style wording. That's why seed 42's matrix has errors in both directions between those two labels. `general_question` is the label it learned closest to what I meant, with 3 of 4 posts right on every seed, probably because questions have a clear surface cue (a question about TV in general) that matches my definition.


<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**



