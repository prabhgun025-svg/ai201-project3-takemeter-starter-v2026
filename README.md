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

**Definition:** A question about TV in general that isn't tied to one show, so people can answer it with examples from any show but also contains general tv questions

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
| Overall accuracy |  |  |  |
| Macro F1 |  |  |  |
| F1 — `label_one` |  |  |  |
| F1 — `label_two` |  |  |  |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->



---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted |  |  |  |
|---|---|---|---|
| **** |  |  |  |
| **** |  |  |  |
| **** |  |  |  |

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->



---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** ___ / 30 = ___%

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

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



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



