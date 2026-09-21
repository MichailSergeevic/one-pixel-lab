# One Pixel Lab

A tiny one-pixel image classifier built for CPSC 1710, Homework 2 (Stop 1: Explore One Pixel ML).

## What it does

`one-pixel.html` shows twelve grayscale pixels. You label each pixel "dark" or "light," then train a simple threshold model that searches for the brightness cutoff with the fewest mistakes.

## How to run it

Open `one-pixel.html` directly in a web browser. No build step or server needed.

## Development log

Moments where I directed the work on `startup-offer.html`:

1. **Chose a different idea.** I first proposed classifying universities into tiers by ranking. Codex pointed out that this is just One Pixel ML again (one number, one cutoff) and may feel high-stakes, so I switched to a startup job offer with several inputs (salary, equity, number of employees) and playful labels (Steady Paycheck, Lottery Ticket, Jackpot) instead of "good" or "bad."
2. **Set the rules myself.** I decided the three inputs (employees instead of funding stage) and defined the low/mid/high cutoffs for each: salary under 60K / 60-70K / over 70K, equity under 0.2% / 0.2-0.4% / over 0.4%, and under 20 / 20-50 / over 50 employees.
3. **Closed a gap in the labels.** Codex noticed that a low-salary, low-equity offer fit none of my three labels, so I asked for a fourth label, "Bust."
4. **Asked for a design element.** I wanted a unicorn on the page. Codex tied it to the Jackpot result (a "unicorn" is startup slang for a huge success) and added it to the header and the browser tab icon.
5. **Changed the wording.** I did not like the word "vibe" in the title and headline, so it was replaced with "Sorter" and "type."
