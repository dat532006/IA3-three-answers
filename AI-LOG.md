# AI-LOG.md

One entry per task where an assistant did part of the work, in the order the work happened. Entry 1 was written at the original drafting handoff and is kept as it was then. Its "pending" wording describes that moment; I accepted the predictions before commit `f05b449`.

## 2026-11-04 — IA#3: static analysis and prediction drafting

Tool: Codex (desktop application). The session information described the agent as based on GPT-6; no specific backend/model version identifier was verified. Used file-reading/PowerShell tools, read-only Git, and the PDF skill to extract/render/read the rubric; used file-editing tools for exactly the two authorized reports. No sub-agent was used.

Asked for: Read the rubric, AI-log template, brief/README and A/B/C source with execution context; check the baseline; perform static analysis, explain mechanisms, draft 27 predictions and a verification plan, then hand them to the student.

Kept: Not yet reviewed/confirmed by the student; no decision to retain AI content had been recorded.

Changed: Not yet reviewed/confirmed by the student; no student changes or execution results established a need to revise a claim.

Rejected: Not yet reviewed/confirmed by the student; no claim or proposal had been rejected by the student for recording.

By hand: Not yet reviewed/confirmed by the student; no evidence of report content personally written by the student in that session.

Actual outputs: `VERDICTS.md` and `AI-LOG.md` in the workspace. Neither file existed before the session. VERDICTS contained sources/commits/code lines, three tables totaling 27 predictions, separate analyses of A/B/C, concurrency, risks outside the matrix, provisional verdicts, and a runtime section retained as NOT_TESTED. The draft predicted A fix for row 2, B fix for rows 6 and 8, and conditional C keep; these were AI inferences, not student decisions or test results.

Baseline and verification: HEAD was `c1f62e8207f7d0f42f3f91d0b106e1bb3cceacad` (`starter`), with a clean working tree before creating the draft. Documents/source were read and checked against Git; the two reports, row counts and diff were reviewed. No existing test evidence was found in the files/history inspected; this cannot establish that the student had never run the application elsewhere. PDF images were document renders in a temporary directory outside the repository, not runtime evidence.

Completed scope: only source/Git reading and creation/review of the two report files. No application/server, browser tests, TypeScript checker, build or formatter was run; no dependency was installed. No source changes, add/commit/push, or index/ref/history changes; no evidence directory, other reports, ZIP or submission. Reading/rendering the PDF and counting Markdown structure were not application tests.

Handoff status at that time: **pending student review**. The student could accept, revise with reasons, disagree or request explanation. There was no new prediction commit yet. Content acceptance did not itself authorize commit/push; testing was to begin only after the student explicitly confirmed that predictions had been committed before testing and assigned the testing task.

Declared limitation: one entry for the prediction-drafting task, not the formal independent ASSISTANT-REVIEW step. No earlier sessions, observations, assistant mistakes caught by testing, regressions, or Changed/Rejected decisions were recorded without evidence; no self-assessment score was assigned.

## 2026-11-04 — IA#3: running the table on the original A, B and C

Tool: Codex desktop application (session identifies the agent as GPT-6 based; exact model build not exposed). It used Node.js, Playwright 1.62.1 driving Chrome 156, and `tsc` 6.0.3 installed in a temp folder outside the repo.

Asked for: Run rows 1–8, the empty row and the stock parallel check against the three original files, after the predictions had been committed in `f05b449`. Use the unmodified `server.mjs` and `jsconfig.json`, and change no starter file.

Kept: The measured results: DOM state at fixed times (1 s, 5 s, 7 s), the start time of every `/api/stock` request, Console entries and the `tsc` output. They confirmed all 27 predictions: A fails row 2 (`0 đ`), B fails row 6 (still loading at 7 s, error only at 30 s) and row 8 (TS2353 at b.js:16), and C passes. Also kept: its page-only screenshots of passing rows (`evidence/<v>-normal/error/retry/hang/empty.png`) as supporting evidence. Every version file was restored after the temporary `// @ts-check` edit; `git diff` on `public/` was empty afterwards.

Changed: Its screenshots of the failing rows showed only the page, with no DevTools panel or terminal, so they did not prove the failure the way the rubric asks. I re-ran those rows myself in Chrome DevTools and VS Code and replaced them with `evidence/a-row2.png`, `b-row6.png` and `b-row8.png`.

Rejected: The JSON logs and duplicate screenshots it wrote into `evidence/run-2026-11-04/`. They are too long to be readable evidence, so I removed them from the submission and kept the numbers I need in `VERDICTS.md` §9.

By hand: Nothing in this step. The script run was the assistant's work.
