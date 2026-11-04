# Self-assessment — IA#3 (Three answers to one brief)

Submitted by: 24120037 — Nguyễn Đức Đạt

Total I claim: 96 / 100

| Criterion | Max | I claim | Evidence |
|---|---|---|---|
| 1. Verdicts and evidence | 30 | 28 | `VERDICTS.md`: predictions in §1–8, committed in `f05b449` before any run. §9 holds all 27 lines (9 rows × 3 versions) with PASS/FAIL and the measured values. It also gives the responsible lines (A: a.js:51–56; B: b.js:16), the verdicts with deciding row (A fix / row 2, B fix / row 6, C keep), and one sentence per version naming row, evidence and constraint. Every FAIL has a page + DevTools/VS Code screenshot: `evidence/a-row2.png`, `evidence/b-row6.png`, `evidence/b-row8.png`. No version is failed on a row it passes. Minus 2: most passing rows were measured by a script rather than by hand. |
| 2. Every version passes every row | 25 | 25 | `VERDICTS.md` §10: after fixes `b0b7f0e` (A) and `e83e623` (B), all three versions pass rows 1–8, empty and the parallel check. The 8 stock requests start within 1 ms of each other. Row 6 aborts at about 5.04 s. Row 8: `tsc` exit 0 for all three. |
| 3. Assistant's review, checked | 15 | 15 | `ASSISTANT-REVIEW.md`: tool/model, prompt, and the answer pasted unedited. A table checks all 22 claims against a row or a run, each marked Confirmed / Not real / Outside the rows. "Failing rows the assistant missed": none. "Where the assistant was wrong" says plainly that "forever" for B was overstated (row 6 shows the error at 30 s) and that the type-error and `slow` > 5 s claims were not real (rows 8 and 4). |
| 4. CSR vs SSR | 10 | 9 | `CSR-SSR.md`: all five questions answered from observation. It quotes the page source of `/?v=c` and `/ssr`, explains why the scarf reads `&lt;i&gt;` (escaping in `renderSsrPage`, the same idea as `textContent`), says what is left with JavaScript off, and counts the requests before the stock value appears. Minus 1: the observations were collected mostly with a browser script. |
| 5. AI-LOG.md | 10 | 9 | `AI-LOG.md`: one entry per use of an assistant — prediction drafting, the test run, the review, fix A, fix B, CSR-SSR. Each names the tool, the request and the result. Changed/Rejected record real errors caught by rows: the review's "forever" claim (row 6), its invented type errors (row 8), and the script's DevTools-less screenshots, rejected and retaken. Minus 1: the first entry still carries its handoff-time "pending" wording. |
| 6. Scope and commit history | 10 | 10 | `git log`: `c1f62e8 starter` comes first, then predictions `f05b449`, then results `715b0a6`. Each fix is its own commit touching only its version file: `b0b7f0e` → `public/versions/a.js`, `e83e623` → `public/versions/b.js`. `git diff c1f62e8 HEAD -- server.mjs public/panel.js public/index.html public/style.css jsconfig.json` is empty. |

## What I did not manage

- I did not run all 27 rows by hand in the browser. A script (Codex, then Claude Code) ran the full matrix. I reproduced the three failing rows myself, with DevTools and VS Code. The screenshots of passing rows are the script's page-only captures.
- My first `b-row6.png` was taken about 4 s after reload, which proves nothing; the server log showed it, and I retook it at about 22 s. My first `a-row2.png` had an empty Network panel because my keyboard typed into the filter box.
- The CSR vs SSR answers rely more on a script's observations than on my own clicking.

## What I would do differently

Run the whole table by hand once before asking a script to repeat it, so every observation in `VERDICTS.md` is mine and not only the failing rows. Start earlier, so there is time to do the CSR vs SSR part myself with JavaScript disabled in DevTools.
