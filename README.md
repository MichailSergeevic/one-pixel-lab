# One Pixel Lab

Two small in-browser classifiers built for CPSC 1710, Homework 2.

| Task | File | What it is |
|---|---|---|
| 1 | `one-pixel.html` | Label grayscale pixels and watch a model learn a cutoff |
| 2 | `startup-offer.html` | Sort a fictional startup job offer into a risk/reward type |

Both are single HTML files. Open them directly in a web browser; no build step, server, or API key is needed.

## Task 1: One Pixel ML

**File:** `one-pixel.html`

The page shows twelve grayscale pixels. You label each one "dark" or "light," then train a simple threshold model that searches for the brightness cutoff with the fewest mistakes.

**How to use it:** label the pixels yourself, or load one of the three guided examples (clean split, one odd label, reversed labels), then train the model and test new brightness values.

## Task 2: Startup Offer Sorter

**File:** `startup-offer.html`

The page takes three numbers about a fictional startup job offer and sorts it into one of four playful types. It is a toy classifier, not financial advice.

**Inputs**

- Salary (EUR/year), 30K to 120K
- Equity (%), 0 to 1.00
- Number of employees, 1 to 200

**Labels:** Steady Paycheck, Lottery Ticket, Jackpot, Bust.

**How it decides (nearest example):** the page holds 16 labeled example offers. Each offer becomes three numbers on a 0-1 scale (company size is on a log scale). The classifier finds the 3 examples closest to your offer and they vote; if the vote is split, the single closest example wins. There is no "salary over 70K is high" rule, so different examples give different answers.

**Teaching it:** set the sliders to an offer and click one of the four label buttons to add it as a new example. "Reset examples" returns to the original 16.

**Known limits:** the 16 starting examples are my own made-up offers. If an offer is far from every example (for instance a 1-person company paying 120K with 0% equity), the page says "Not sure" and shows its best guess instead of confidently picking a type. Teaching it a similar example fixes that.

**How to use it:** move the three sliders, or click one of the four example buttons, and read the "Why" list under the result to see which examples voted.

### Development log

Moments where I directed the work on this page:

1. **Chose a different idea.** I first proposed classifying universities into tiers by ranking. Codex pointed out that this is just One Pixel ML again (one number, one cutoff) and may feel high-stakes, so I switched to a startup job offer with several inputs (salary, equity, number of employees) and playful labels (Steady Paycheck, Lottery Ticket, Jackpot) instead of "good" or "bad."
2. **Set the rules myself.** I decided the three inputs (employees instead of funding stage) and defined the low/mid/high cutoffs for each: salary under 60K / 60-70K / over 70K, equity under 0.2% / 0.2-0.4% / over 0.4%, and under 20 / 20-50 / over 50 employees.
3. **Closed a gap in the labels.** Codex noticed that a low-salary, low-equity offer fit none of my three labels, so I asked for a fourth label, "Bust."
4. **Asked for a design element.** I wanted a unicorn on the page. Codex tied it to the Jackpot result (a "unicorn" is startup slang for a huge success) and added it to the header and the browser tab icon.
5. **Changed the wording.** I did not like the word "vibe" in the title and headline, so it was replaced with "Sorter" and "type."
6. **Questioned whether it was a classifier.** I asked if the page was actually a classifier. Codex explained that a hand-written lookup table is rule-based, not learned, so I chose to switch to a nearest-example method that learns from labeled examples.
7. **Improved the strange case.** When I tested a 1-person company with 120K salary and 0% equity, the page confidently said "Jackpot." I asked to improve it, so offers far from every example now get "Not sure" with a best guess, and teaching the page a similar example makes it confident again.
