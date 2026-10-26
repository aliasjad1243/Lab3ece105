# AI log: Lab 3, fit_zipf

Your name: Ali Asjad Syed

Tool: ChatGPT Edu

## The prompt I gave it

(paste your prompt here, including the docstring)
I attached Lab3_StarterCode.py, check_fit.py, ai_log.md, the three
books, and the Lab 3 slides, and asked: "Here is a starter code. Could you give me its body?". The fit_zipf
def line and docdtring (lines 82-96 of the starter code) were part of
the attached file, unchanged.


## The code it gave me

    k = np.arange(kmin, kmax + 1)        # ranks kmin, ..., kmax (inclusive)
    ck = c[kmin - 1:kmax]                # rank k is c[k - 1]
    m, b = np.polyfit(np.log10(k), np.log10(ck), 1)
    return m, 10**b

## What I checked

- Example 1, `fit_zipf(np.array([600, 300, 200, 150]), 1, 4)`: I got
  -1.0 600.0 (want: -1.0 600.0)
- Example 2, `fit_zipf(np.array([5000, 900, 400, 1]), 2, 3)`: I got
  -2.0 3600.0 (want: -2.0 3600.0)
- Anything else I checked: ran the full program. A Tale of Two Cities
  fit, ranks 1 to 1000: c_k = 25,910 * k^(-1.092), the same as slide 17.
  King James Bible: slope -1.162. Don Quijote: slope -1.046. Checked
  each line against slide 14's list of common mistakes: it uses np.log10
  (not np.log), kmax + 1 so kmax is included, and kmin - 1 because
  rank k is c[k - 1].


## What I changed, and why

Nothing. What each line does:
- Line 1 makes the list of ranks, from kmin up to kmax.
- Line 2 picks out the word counts for those ranks.
- Line 3 draws the best straight kine through the points on a log-log graph.
- Line 4 returns the slope of that line and the number C.
## The third part of submission 
The three slopes:

A Tale of Two Cities: −1.092
King James Bible: −1.162
Don Quijote: −1.046

Closest to Zipf’s −1: Don Quijote, at −1.046, only 0.046 away. Dickens comes next (−1.092), and the King James Bible is farthest (−1.162).

Top-20 words:

The Bible’s alone: be, is, lord, not, shall, them, they, unto
Dickens’s alone: as, at, had, her, it, was, with, you
In both (12): a, and, for, he, him, his, i, in, of, that, the, to

