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

### Name and purpose

**Startup Offer Sorter** is a tiny classifier that sorts a fictional startup job offer into one of four playful types: **Steady Paycheck**, **Lottery Ticket**, **Jackpot**, or **Bust**. Its purpose is to show that a classifier can weigh several inputs at once (salary, equity, and company size) and that its answers come from the labeled examples it has seen. It is a toy, not financial advice.

### How to open and use it

1. Open `startup-offer.html` in a web browser (double-click the file). No build step, server, or API key is needed.
2. Move the three sliders: salary (30K to 120K EUR), equity (0 to 1.00%), and number of employees (1 to 200). Or click one of the four example buttons.
3. Read the result and the "Why" list, which shows the 3 example offers that were closest to yours.
4. To teach it, set the sliders to an offer, then click the label you think fits. It adds your offer as a new example. "Reset examples" goes back to the original 16.

### How it makes a prediction

The page holds 16 example offers that already have a type. When you enter an offer, it finds the 3 examples most similar to yours (close in salary, equity, and company size) and lets them vote. The type with the most votes wins, and if the vote is split, the single most similar example wins. If even the most similar example is far away, it says "Not sure" and shows its best guess instead. It has no built-in rule like "salary over 70K is high," so different examples give different answers.

### A limitation I discovered

The classifier only knows its examples. When I tested a 1-person company with a 120K salary and 0% equity, it confidently answered "Jackpot" because that offer was far from everything it had seen. I added the "Not sure" answer for offers like this, but the deeper limit remains: my 16 starting examples are made up, so its answers reflect my choices rather than real job offers.

### Development log

Moments where I directed the work on this page:

1. **Chose a different idea.** I first proposed classifying universities into tiers by ranking. Codex pointed out that this is just One Pixel ML again (one number, one cutoff) and may feel high-stakes, so I switched to a startup job offer with several inputs (salary, equity, number of employees) and playful labels (Steady Paycheck, Lottery Ticket, Jackpot) instead of "good" or "bad."
2. **Set the rules myself.** I decided the three inputs (employees instead of funding stage) and defined the low/mid/high cutoffs for each: salary under 60K / 60-70K / over 70K, equity under 0.2% / 0.2-0.4% / over 0.4%, and under 20 / 20-50 / over 50 employees. The first version used these as a lookup table.
3. **Closed a gap in the labels.** Codex noticed that a low-salary, low-equity offer fit none of my three labels, so I asked for a fourth label, "Bust."
4. **Asked for a design element.** I wanted a unicorn on the page. Codex tied it to the Jackpot result (a "unicorn" is startup slang for a huge success) and added it to the header and the browser tab icon.
5. **Changed the wording.** I did not like the word "vibe" in the title and headline, so it was replaced with "Sorter" and "type."
6. **Questioned whether it was a classifier.** I asked if the page was actually a classifier. Codex explained that a hand-written lookup table is rule-based, not learned, so I chose to switch to a nearest-example method that learns from labeled examples.
7. **Improved the strange case.** When I tested a 1-person company with 120K salary and 0% equity, the page confidently said "Jackpot." I asked to improve it, so offers far from every example now get "Not sure" with a best guess, and teaching the page a similar example makes it confident again.
