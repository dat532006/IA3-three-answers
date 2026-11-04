AI-assisted predictions — accepted by the student; NOT_TESTED.

# IA#3 — Predictions from static analysis

The student explicitly accepted all **27 predictions** (9 rows × 3 versions) in this AI-assisted draft on **2026-11-04 (Asia/Bangkok, UTC+7)**, including their assumptions and qualifications. Acceptance confirms agreement with the predictions, not observed test results. No execution results are recorded, and all verdicts below remain provisional. This is not the independent review for `ASSISTANT-REVIEW.md`, nor is it a complete submission.

## 1. Status, baseline and sources

### 1.1. How to read the labels

- **VERIFIED_SOURCE**: information read directly from documents, source code or read-only Git output; this does not mean the behavior has been verified by running it.
- **STATIC_INFERENCE**: reasoning based on the source and API/JavaScript behavior; this includes the entire Prediction column, explanations of behavior and provisional verdicts.
- **NOT_TESTED**: no application, server, browser tests, TypeScript checker or Network measurements were run during the drafting session. No diagnostics, runtime screenshots or student observations have been supplied as results.

### 1.2. Baseline checked during the original drafting session — VERIFIED_SOURCE

- Workspace: `D:\Do_AN\WEB\IA#3\session5-starter`.
- At that check, `HEAD` on branch `main` was **`c1f62e8207f7d0f42f3f91d0b106e1bb3cceacad`**, with message `starter` and commit date 2026-11-04 17:13:19 +0700. The commit had no parent; the log contained one commit. The local `origin/main` ref pointed to the same commit; no fetch or direct remote verification was performed.
- Before the draft was written, `git status` was clean, with no working-tree or staged diff. The ten tracked starter files matched that commit. Because the source was unchanged, the analysis used the working-tree files checked against Git, which were also the starter files at this commit.
- Neither `VERDICTS.md` nor `AI-LOG.md` existed before drafting. No `AGENTS.md` was found in the applicable ancestor directories or repository. The repository inventory contained no test reports, screenshots or logs, including ignored/untracked files; the queried history also contained neither report nor an evidence directory.
- The absence of evidence within that scope **does not prove that no earlier runs took place elsewhere**. No tests were run and no predictions were committed during the drafting session. If the student had already run the application, the timing must be disclosed and the earlier results retained; this new draft must not be described as a prediction committed before that run.

### 1.3. Source list and line-reference conventions — VERIFIED_SOURCE

All line numbers below are **1-based references to the original source at the baseline commit**, before adding `// @ts-check`. The notation `A:52–56` means lines 52–56 of source A in this table. Adding a checker directive later will shift the editor's displayed line numbers by one.

| Label | Source read | Relevant material |
|---|---|---|
| Rubric | [IA3-rubric-three-answers.pdf](<D:/Do_AN/WEB/IA#3/IA3-rubric-three-answers.pdf>) | All 5 pages: workflow, predictions, evidence, concurrency, AI log and scope |
| Log template | [AI-LOG template](<D:/Do_AN/WEB/IA#3/AI-LOG.md-—-template-(CSC13008).txt:24>) | Lines 8–13, 24–37: one honest entry, retaining the template fields |
| Brief | [brief.md](<D:/Do_AN/WEB/IA#3/session5-starter/brief.md:32>) | 13–30: DOM/API; 34–58: behavior and constraints |
| README | [README.md](<D:/Do_AN/WEB/IA#3/session5-starter/README.md:69>) | 19–67: setup/DevTools; 71–90: rows 1–8 and empty; 92–114: verdicts |
| A | [a.js](<D:/Do_AN/WEB/IA#3/session5-starter/public/versions/a.js:1>) | All lines 1–67 |
| B | [b.js](<D:/Do_AN/WEB/IA#3/session5-starter/public/versions/b.js:1>) | All lines 1–63 |
| C | [c.js](<D:/Do_AN/WEB/IA#3/session5-starter/public/versions/c.js:1>) | All lines 1–68 |
| Server | [server.mjs](<D:/Do_AN/WEB/IA#3/session5-starter/server.mjs:19>) | All lines 1–204; data at 19–31, modes at 166–183 |
| Panel | [panel.js](<D:/Do_AN/WEB/IA#3/session5-starter/public/panel.js:24>) | All lines 1–50; mode changes at 24–36, version import at 41–49 |
| HTML | [index.html](<D:/Do_AN/WEB/IA#3/session5-starter/public/index.html:39>) | All lines 1–59; output/status/retry/list at 39–44, template/module at 50–57 |
| CSS | [style.css](<D:/Do_AN/WEB/IA#3/session5-starter/public/style.css:13>) | All lines 1–75; `[hidden]` at line 14, catalogue/grid at 50–59 and 74–75 |
| Config | [jsconfig.json](<D:/Do_AN/WEB/IA#3/session5-starter/jsconfig.json:1>) | All lines 1–17; DOM/ES2022, `strict: false`, `checkJs: false`, scope `public/**/*.js` |

### 1.4. Source precedence and limitations

**VERIFIED_SOURCE:** Rubric page 1 supersedes “Nothing to hand in, not graded.” at README:4. IA#3 is a graded individual assignment; the remaining README instructions still apply. Rubric pages 1–2 require predictions to be committed before results; page 2 checks concurrency separately from the 27 rows; page 3 requires an independent review and CSR/SSR work in other steps. Those steps were not performed during the prediction-drafting session.

README:83,87–90 describes row 8 using VS Code and `// @ts-check`; rubric page 2 describes grading with `tsc` and Config. These are two ways to check the same typing requirement. No TypeScript version, grading command or grading script was available to establish the exact diagnostics. No other conflict was identified between the behavioral requirements in Brief and the README matrix.

Rubric page 3 describes an AI-log scoring band in which Changed/Rejected entries relate to actual mistakes. There was no evidence for such decisions during the drafting session; mistakes or feedback must not be invented to satisfy the rubric. No self-assessment score was assigned.

## 2. Shared conditions and basis for comparison

**VERIFIED_SOURCE:** Panel:41–49 imports the corresponding version only when the URL contains `?v=a`, `?v=b` or `?v=c`. Changing the mode updates the server for subsequent requests; wait for the panel to confirm the change before reloading or pressing Retry (Panel:24–36; README:33–43). Use the correct version's CSR page, not `/ssr`, to assess A/B/C.

**VERIFIED_SOURCE:** Server:19–31 specifies this order: `tshirt`, `hoodie`, `somi`, `cap`, `tote`, `socks`, `jacket`, `scarf`. The final name is `Scarf <i>limited</i>`. Static arithmetic using the constants gives `180000×12 + 420000×5 + 350000×3 + 95000×20 + 120000×0 + 75000×30 + 890000×2 + 160000×7 = 12360000`, matching the expected `12.360.000 đ` at README:71–72; this is not a measurement from the application.

**Assumptions for STATIC_INFERENCE:** the browser supports ES modules, `fetch`, `replaceChildren` and `vi-VN` formatting; A/C also require `AbortSignal.timeout`. The DOM/template remains as defined in HTML. The server uses the starter data; valid stock requests return 200 after a scheduled delay of 100–600 ms (Server:176–183). The tab is active and operating normally, and the local network introduces no failures beyond the selected mode. If these assumptions do not hold, record the actual conditions and reconsider the predictions.

The “wait a second” timing in row 2 and “about 5 seconds” timing in row 6 must be measured later. A delay specified in source does not guarantee the completion time on the student's machine: connections, queuing, scheduling and overhead also matter. If the total becomes correct only after the check's time point, record both the timing and value rather than changing the condition to mark it as passing.

**Row 7:** following README:59–63, distinguish unhandled JavaScript errors (`Uncaught …`, including Promise rejections) or errors printed by the version itself from HTTP messages generated by the browser. A `throw` in an `await` chain handled by `catch` does not automatically produce a Console error. The browser's own `GET … 500` line does not by itself fail row 7. Other HTTP messages, if any appear, must also be recorded verbatim and classified rather than mislabeled as JavaScript exceptions. No Console output has been collected.

**Row 8:** adding `// @ts-check` enables checking for the file under the README procedure; Config currently has `checkJs: false`. `strict: false` does not itself enable strict null checking or prohibit implicitly typed `any` parameters. DOM type assertions and the broad type returned by `res.json()` can allow logic errors to escape the checker. Do not infer a type error in A merely from `forEach(async …)`, or treat a predicted clean checker result as proof of program correctness. All checker claims below remain STATIC_INFERENCE; there are no actual diagnostic codes or messages.

## 3. Version A

### 3.1. Implementation and execution flow

**VERIFIED_SOURCE:** A:4–10 obtains the DOM elements and defines the currency formatter. `load()` is called on import (66–67), guards against overlapping loads with `busy`, hides Retry, sets the total to `—` and sets the status to `Loading products…` (39–44). `getProducts()` uses `AbortSignal.timeout(5000)`, checks `res.ok` and reads JSON (12–16). `renderCards()` clones the template in array order and sets `data-id`, using `textContent` for names/prices (26–34). It then updates the status (48), invokes an async callback for each stock request (51–55) and writes the total (56). The `catch` branch clears the cards, displays the error and shows Retry; `finally` releases the guard (57–63).

**STATIC_INFERENCE:** product loading has an error chain managed by `await`/`catch`, but the Promise returned by each stock callback is not connected to that chain. The total is written to the DOM before the stock requests complete.

### 3.2. Prediction table A — STATIC_INFERENCE, not run

Condition and Expected behavior map respectively to README:76–83; empty follows README:85 and Brief:39–49. Row 3 checks the final card after a `normal` load; row 7 monitors Console throughout rows 1–6.

| Row | Condition | Expected behavior | Prediction | Source reasoning | How to verify later |
|---|---|---|---|---|---|
| 1 | Mode `normal`, reload | 8 cards in API order, prices such as `180.000 đ`; status empty | Predicted pass | A:26–34 preserves `map` order and sets names/prices and `data-id`; 46–48 renders and then clears the status. The total-value error does not change the cards. | Open `?v=a`, compare the 8 cards/data-id values with the products response, and inspect prices and status. |
| 2 | Mode `normal`, reload, wait a second | Stock value: `12.360.000 đ` | Predicted fail | A:51–56 does not wait for the async callbacks; the DOM is expected to receive `0 đ` and is not updated when `total` changes. | Record the total at about 1 s and after the last stock response; remaining at `0 đ` despite all 8 responses would confirm the prediction. |
| 3 | Look at the last card | The name reads `Scarf <i>limited</i>`, with visible angle brackets and no italics | Predicted pass | A:30 uses `textContent`; Server:27 contains the tag-like string as data. | Read the name and inspect `.name`: no `<i>` element should be created from the name. |
| 4 | Mode `slow`, reload | `Loading products…` for about 3 s, then 8 cards; status clears | Predicted pass | A:44 runs before `await`; 47–48 renders/clears the status after products arrive. Server:169 delays by 3 s, less than the 5 s timeout at A:14. | Follow the status from request initiation until the cards appear; compare with Timing. |
| 5 | Mode `error`, reload; then switch to `normal` and press Retry | Initially `Could not load products.`, Retry visible, no cards; after Retry, 8 cards with the message and button gone | Predicted pass | A:15 turns an HTTP error into a rejection caught at 57–60; 42,46–48 and 66 handle Retry. An incorrect total is not a separate criterion for this row. | Observe both stages; wait for mode `normal` to be confirmed before Retry, then inspect the status/button/cards. |
| 6 | Mode `hang`, reload, count to 7 | After about 5 s, `Could not load products.` and Retry; not half a minute spent Loading | Predicted pass | A:14 supplies a real timeout signal; rejection reaches 57–60 before the 504 response at 30 s in Server:171–172. | Measure from the products request to the error/Retry state and request cancellation; record the actual seconds. |
| 7 | Watch Console during rows 1–6 | No `Uncaught …` errors, nothing red except the browser's own `GET … 500` line | Predicted pass | The products request is handled with `await` within `try/catch` (46,57–60), with no explicit `console.error`. Valid stock requests in the matrix are expected to return 200; the stock-rejection risk is treated separately in §3.3. | Keep Console open throughout the rows; record exact messages and stacks if errors occur, distinguishing HTTP from JavaScript errors. |
| 8 | Open the folder in VS Code; add `// @ts-check` as the version file's first line, inspect red underlines, then remove the line | No red underlines | Predicted pass | A:4–8,28 uses DOM type assertions; Config:3–12 provides DOM/ES2022 without strict checking. Ignoring an async callback's return value does not necessarily violate a type rule. This depends on the DOM library recognizing `AbortSignal.timeout`. | Only in a later authorized checker task: use the correct Config and record the TS version/diagnostics; do not infer a type error from the incorrect total. |
| empty | Mode `empty`, reload | `No products yet.` and `0 đ` | Predicted pass | A:34,48 produces the empty list/status; `forEach` has no iterations, so `total=0` makes line 56 correct in this case. | Check the status, output, 0 cards and absence of stock requests. |

### 3.3. Potential issues and scope of impact

**A-1 — Predicted violation of a formal requirement, row 2; Brief:45–49.** Location: [A:51–56](<D:/Do_AN/WEB/IA#3/session5-starter/public/versions/a.js:51>). Condition: a nonempty products array, as in `normal`. `forEach` invokes each callback; the callback returns a Promise when it reaches `await getStock(...)`, but `forEach` neither collects nor waits for these Promises. Line 56 therefore runs while `total` is still 0. Later, line 54 changes only the numeric variable; `textContent` has already received a string and is not bound to update when the variable changes. This is a DOM-update timing error, not an addition error caused by multiple threads writing the variable. Even after every response completes, there is no second instruction to render the total.

Future confirmation: all 8 stock responses succeed, but the output remains `0 đ`. A result that would contradict the prediction under the stated conditions: the output updates itself to `12.360.000 đ` with the exact baseline source; in that case, recheck the version actually imported, the cache and the reasoning. Do not extend this failure to rows 1/3/4/5 or empty, which have their own expected behavior.

**A-2 — Error-handling risk outside the matrix conditions.** Location: A:19–23,52–55. If a stock request encounters a network error, returns a non-2xx HTTP response or produces invalid JSON, the async callback rejects without a handler. The `catch` in `load()` cannot catch the discarded Promise; `Uncaught (in promise)` may appear, with no Retry offered for the stock failure. This warrants verification if testing is extended to stock failures; the Server's five modes change only `/api/products`, and every catalogue id has a STOCK entry. Therefore, do not automatically fail row 7 in the standard matrix. An unhandled rejection with a stack pointing to the callback would confirm the risk; if the rejection is handled, identify the actual handler or conditions that differ from the baseline. This failure was not induced during the drafting session.

### 3.4. Stock concurrency in A

**STATIC_INFERENCE:** A:52–53 calls `getStock` for every product without waiting for the previous stock result; each function reaches `fetch` at A:20 before its first suspension. Request calls are therefore expected to be initiated in parallel at the application level. However, their completion is not awaited, so this does not ensure a correct DOM result. Later measurements must distinguish three moments: each request's start, completion/JSON receipt, and the output update. The expected pattern is requests being created close together, but `0 đ` appearing before stock loading completes. The actual waterfall and DOM timing both remain NOT_TESTED; see §6.

### 3.5. Provisional verdict, assumptions and verification

**STATIC_INFERENCE — provisional `fix`, deciding row: 2.** There is a basis for a focused fix that collects/waits for stock results before writing the total while retaining parallel initiation; there is no basis for requiring a complete rewrite. No source was changed, and no final verdict has been made on the student's behalf.

Draft instruction for the assistant **after verification**: “If row 2 confirms that the output remains `0 đ` after 8 successful stock requests, wait for all stock results before calculating/writing the total, keep the requests parallel, and leave the starter unchanged outside version A.” This is currently a conditional instruction based on a prediction, not a quotation of an observation.

Uncertainties: browser/DOM-library support for the timeout API, actual timing and the effect of stock failures. Prioritize verification of rows 2, 6, 7, 8 and concurrency, while still running every remaining row once testing has been assigned.

## 4. Version B

### 4.1. Implementation and execution flow

**VERIFIED_SOURCE:** B:4–12 obtains the DOM elements and formats currency. `showCatalogue()` runs on import (62–63), guards against overlapping loads with `loading`, hides Retry, clears the list and sets `—` and `Loading products…` (38–44). `loadProducts()` passes `{ timeout: 5000 }`, checks HTTP status and reads JSON (14–18). Cards are created using `textContent` and `map` order (28–33,47–48). `Promise.all` waits for stock results, and `reduce` pairs prices and stock by index before the total is written (51–53). `catch` displays the error/shows Retry; `finally` releases the guard (54–59).

**STATIC_INFERENCE:** the stock-loading path waits for all results. The questionable part is the products request's `timeout`: standard browser `fetch` does not use this member to cancel requests.

### 4.2. Prediction table B — STATIC_INFERENCE, not run

Condition/Expected follow the same mapping to README:76–85 and Brief:39–49 as A; the timeout error is not a reason to fail modes that respond promptly.

| Row | Condition | Expected behavior | Prediction | Source reasoning | How to verify later |
|---|---|---|---|---|---|
| 1 | Mode `normal`, reload | 8 cards in API order, prices such as `180.000 đ`; status empty | Predicted pass | B:28–33,47–48 renders in array order, formats prices and clears the status. The extra `timeout` member does not itself cause a JavaScript exception in a standard browser. | Open `?v=b` and compare order/data-id/prices/status with the products response. |
| 2 | Mode `normal`, reload, wait a second | Stock value: `12.360.000 đ` | Predicted pass | B:51 waits for all Promises; results preserve input order, and 52–53 calculates/writes the correct total for the data in Server:19–31. Actual timing must be measured. | Record the value and timing at about 1 s and after the last response; distinguish a correct total from a missed timing target. |
| 3 | Look at the last card | The name reads `Scarf <i>limited</i>`, with visible angle brackets and no italics | Predicted pass | B:31 uses `textContent` rather than parsing the name as HTML. | Read the name and inspect `.name`, confirming that no `<i>` element is created. |
| 4 | Mode `slow`, reload | `Loading products…` for about 3 s, then 8 cards; status clears | Predicted pass | B:44,46–48 keeps the status until products arrive after 3 s (Server:169). The lack of a real timeout does not prevent this mode from succeeding. | Measure the request and observe Loading → cards/empty status. |
| 5 | Mode `error`, reload; then switch to `normal` and press Retry | Initially `Could not load products.`, Retry visible, no cards; after Retry, 8 cards with the message and button gone | Predicted pass | B:17 throws on HTTP 500, and 54–56 catches the error; 42 has already cleared the list before the request; 41,47–48,62 handles Retry normally. | Check both the initial error and recovery, pressing Retry only after the new mode is confirmed. |
| 6 | Mode `hang`, reload, count to 7 | After about 5 s, `Could not load products.` and Retry; not half a minute spent Loading | Predicted fail | B:16 uses `timeout`, which is not part of `RequestInit`, with no cancellation signal/timer. Loading is expected to remain at 7 s; Server:172 returns 504 only after 30 s. | Record the status/Retry state and Pending request at 5–7 s; if observing through 30 s, distinguish the 504 response from a client-side timeout. |
| 7 | Watch Console during rows 1–6 | No `Uncaught …` errors, nothing red except the browser's own `GET … 500` line | Predicted pass | The calls at B:46,51 are both inside `try/catch`; there is no `console.error`. A Pending request in row 6 is not an exception; 500 is handled. | Monitor Console and stacks throughout rows 1–6; do not count the browser's HTTP 500 line as an error in the version's code. |
| 8 | Open the folder in VS Code; add `// @ts-check` as the version file's first line, inspect red underlines, then remove the line | No red underlines | Predicted fail | B:16 passes an object literal containing `timeout`; the DOM type `RequestInit` used by `fetch` does not declare that property. TypeScript's strict option is not required for excess-property checking here. | When checker work is assigned, record the actual diagnostics at the fetch call with the correct Config/TS version; there is currently no diagnostic to quote. |
| empty | Mode `empty`, reload | `No products yet.` and `0 đ` | Predicted pass | B:42,47–48 produces the empty list/status; `Promise.all([])` completes, and `reduce(...,0)` at 52 yields 0, which is then formatted. | Check for 0 cards, the status/output and no stock requests. |

### 4.3. Potential issues and scope of impact

**B-1 — Predicted violation of the timeout requirement, row 6; Brief:41–44.** Location: [B:16](<D:/Do_AN/WEB/IA#3/session5-starter/public/versions/b.js:16>). The `hang` condition exposes the difference between the comment “Stop waiting after 5 seconds” and the actual API. The `timeout` field does not set a waiting limit for browser `fetch`; the extra property is ignored rather than causing a JavaScript exception. Without a `signal` or another cancellation mechanism, `await loadProducts()` keeps waiting. The server returns 504 after about 30 s; only then does B:17 throw and B:54–56 display the error. Displaying an error after 30 s still does not meet the approximately 5 s deadline.

Future confirmation: at 7 s, the request is still Pending, the status is still `Loading products…` and Retry has not appeared. A result that would contradict the prediction under standard conditions: the request is actually canceled and the UI changes to the error state near 5 s; determine whether code, a polyfill, the harness or a network factor differs from the baseline. The `normal`, `slow`, `error` and `empty` modes respond before this deadline, so their predictions are assessed separately.

**B-2 — Predicted violation of the checker requirement, row 8.** This concerns the same B:16 call, but it is an API type-contract error, separate from the runtime timing error. With `// @ts-check` and standard DOM types, an object literal containing a property outside `RequestInit` is expected to be reported. `strict: false` does not permit arbitrary excess properties on an object passed to a typed API. The checker has not been run, so no observed diagnostic code, wording or underline location is recorded. Confirm this using an actual diagnostic at the call; if none appears, check the directive, folder/config, DOM library and checker version before concluding that the inference is wrong. Rows 6 and 8 share a source-level cause but need different verification methods.

**B-3 — Risk outside the matrix, without a sufficiently clear expected outcome to classify it as a separate formal failure.** B:47 appends cards before awaiting stock; B:54–56 does not clear them if stock loading fails. The page could then show both cards and `Could not load products.`, while the total remains `—`. Matrix row 5 fails the products request before cards are appended, and B:42 has already cleared the list, so a stock-failure scenario must not be used to fail row 5. Brief does not specify detailed UI behavior for stock failure; clarify it if the scope is extended. Blocking a stock request and then observing cards/status/output would verify this mechanism later; it has not been done.

### 4.4. Stock concurrency in B

**STATIC_INFERENCE:** B:51 evaluates `products.map(...)` before `Promise.all` receives the array of Promises. Each `loadStock` initiates fetch at 22 and then suspends, so there is no sequential per-product `await`. `await Promise.all(...)` waits for all requests to succeed and preserves input-array order even if responses arrive in another order. Only then does B:52–53 calculate the total and write it to the DOM. Initiation happens in the `loadStock` calls inside `map`; `Promise.all` aggregates the Promises already created. Both request start times and the output update must be measured as described in §6; no waterfall evidence is available yet.

### 4.5. Provisional verdict, assumptions and verification

**STATIC_INFERENCE — provisional `fix`, deciding rows: 6 and 8.** Both issues are concentrated at B:16; there is a basis for retaining the rendering and total-calculation flow. No source was changed, and no final verdict has been made.

Draft instruction for the assistant **after verification**: “If row 6 confirms Loading is still shown at 7 s and row 8 reports the invalid `timeout` property at fetch, use a valid browser cancellation mechanism within 5 s, preserve Retry and parallel stock requests, and change only version B.” There are currently no observations that would make this an empirical bug report.

Uncertainties: the exact diagnostics, when the total appears on the student's machine and the UI behavior if stock loading fails. Prioritize measuring row 6, checking row 8 and verifying row 2/concurrency, then run the complete matrix when assigned.

## 5. Version C

### 5.1. Implementation and execution flow

**VERIFIED_SOURCE:** C:4–12 groups the DOM elements in `ui` and formats currency. `start()` runs on import (67–68), guards against overlapping loads with `inFlight` and sets the initial state (42–47). `fetchProducts()` uses a timeout signal and checks HTTP status (14–18). `render()` clones the template, uses `textContent`, collects cards in order in a `DocumentFragment` and replaces the list (28–37); line 51 sets the status according to the product count. Line 54 waits for stock via `Promise.all`, and 55–57 sums by index and writes the total. The error branch clears the list, displays the error and shows Retry; `finally` releases the guard (58–64).

**STATIC_INFERENCE:** no violation of the formal requirements has been identified for the stated starter data and conditions. Do not infer that C has a bug merely because A/B do.

### 5.2. Prediction table C — STATIC_INFERENCE, not run

Condition/Expected again come from README:76–85 and Brief:39–49; the conditions have not been adjusted to favor this version.

| Row | Condition | Expected behavior | Prediction | Source reasoning | How to verify later |
|---|---|---|---|---|---|
| 1 | Mode `normal`, reload | 8 cards in API order, prices such as `180.000 đ`; status empty | Predicted pass | C:28–37 preserves `for...of` order, sets `data-id` and uses `textContent` for names/prices; 50–51 renders and then clears the status. | Open `?v=c` and compare cards/data-id/prices/status with the products response. |
| 2 | Mode `normal`, reload, wait a second | Stock value: `12.360.000 đ` | Predicted pass | C:54 waits for all stock results, and 55–57 sums by index and then formats the total. Actual timing on the student's machine is unknown. | Record the total at about 1 s and after the last response, along with the actual update time. |
| 3 | Look at the last card | The name reads `Scarf <i>limited</i>`, with visible angle brackets and no italics | Predicted pass | C:33 uses `textContent` for the name from Server:27. | Read the full string; inspect `.name` to check that no `<i>` element is created from the product name. |
| 4 | Mode `slow`, reload | `Loading products…` for about 3 s, then 8 cards; status clears | Predicted pass | C:47 runs before await; 50–51 runs after the response. Server:169 responds after 3 s, within the timeout at C:16. | Measure from the request to rendering and confirm that the status changes after about 3 s. |
| 5 | Mode `error`, reload; then switch to `normal` and press Retry | Initially `Could not load products.`, Retry visible, no cards; after Retry, 8 cards with the message and button gone | Predicted pass | C:17 throws on an HTTP error; 58–61 clears the list/displays the error and Retry; 45,49–51,67 handles the next attempt. | Observe the error, change mode, wait for confirmation, press Retry and check the complete recovery state. |
| 6 | Mode `hang`, reload, count to 7 | After about 5 s, `Could not load products.` and Retry; not half a minute spent Loading | Predicted pass | C:16 uses `AbortSignal.timeout(5000)`; 49 and 58–61 route rejection to the error UI. | Measure request cancellation and the UI change near 5 s, rather than waiting 30 s for the server. |
| 7 | Watch Console during rows 1–6 | No `Uncaught …` errors, nothing red except the browser's own `GET … 500` line | Predicted pass | The calls at C:49,54 use `await` within `try/catch`; there is no explicit `console.error`. HTTP 500/products timeout reaches catch. | Keep Console open throughout the rows and classify each message by its source/stack. |
| 8 | Open the folder in VS Code; add `// @ts-check` as the version file's first line, inspect red underlines, then remove the line | No red underlines | Predicted pass | C:5–9,31 uses DOM type assertions; signal is a valid fetch option. Config is not strict; the DOM library must support `AbortSignal.timeout`. | When checker work is assigned, record the TS version and actual result with Config; no diagnostics are available yet. |
| empty | Mode `empty`, reload | `No products yet.` and `0 đ` | Predicted pass | C:37 replaces the list with an empty fragment; 51 sets the status; `Promise.all([])` completes, and the total initialized to 0 is written at 57. | Check for 0 cards, the status/output and no stock requests. |

### 5.3. Potential issues and limits of the conclusions

**No formal violation has been inferred within the matrix under the stated assumptions.** This is not a claim that every row has passed. Each prediction still needs to be checked through the corresponding run or checker result.

**C-1 — Environmental dependency to verify.** C:16 uses `AbortSignal.timeout`. If the browser lacks this API, the call may throw before fetch, enter `catch` and prevent success modes from rendering as predicted. If an older checker DOM library does not declare the API, row 8 may report a type error even though the browser can execute the code. Conversely, checker recognition does not establish browser support. No browser/TS versions have been collected; the two environments need separate checks. A:14 has the same dependency; this is not a problem unique to C.

**C-2 — Risk in an extended scenario, not a failure within the matrix.** C:21–25 sets no stock timeout. If a stock request never completes, `Promise.all` at 54 keeps waiting, the total may remain `—` and `inFlight` has not returned to false. If stock loading rejects, C:58–61 catches the error and clears the entire catalogue. Brief associates the 5 s limit with loading products and describes valid stock responses as arriving after 100–600 ms; do not extend that into a requirement for every stock request to time out after 5 s. A separate stock-timeout policy/error UI would need clarification if the application were extended; it does not automatically create a “FAIL row 6” conclusion for C. The extended verification condition would involve delaying or failing stock requests, not the `hang` mode, which affects only products.

### 5.4. Stock concurrency in C

**STATIC_INFERENCE:** C:54 calls all `fetchStock` functions through `map`; each call reaches fetch at 22 before suspending. After `await Promise.all`, C:56 uses `forEach` **synchronously over results already available**, unlike A's discarded async callbacks. Stock results remain in input-index order; response arrival order does not mismatch prices and stock. C:57 writes to the DOM after the calculation is complete. Parallel initiation and waiting for all results are expected to meet the requirement, but request/DOM timing still needs measurement; a Promise expression in source is not runtime evidence.

### 5.5. Provisional verdict, assumptions and verification

**STATIC_INFERENCE — provisional `keep`, conditional on verification.** All rows 1–8, empty and concurrency need confirmation. Rows 2, 6, 8 and the parallel-request measurement deserve particular attention; no failed row has been confirmed as the basis for a final verdict. The current source alone gives no basis to fix or reject this version.

Draft discussion statement: “Provisionally keep version C because its rendering, timeout and stock-waiting flow matches the source/brief; finalize keep only after all 9 rows and the parallel-request measurement have been confirmed, leaving the starter unchanged.” The main uncertainties concern the environment, timing and stock-failure behavior outside the matrix; the plan is to verify those assumptions before finalizing the verdict.

## 6. Plan for measuring stock concurrency later — currently NOT_TESTED

Rubric page 2 separately grades the start times of `/api/stock/…` requests; Brief:45–49 requires parallel requests. Keep these three questions distinct:

| Question | A — inference from source | B — inference from source | C — inference from source |
|---|---|---|---|
| How does the code initiate stock loading? | `forEach` calls the async functions immediately, without waiting for the previous stock result | `map` calls every `loadStock` before awaiting the combined result | `map` calls every `fetchStock` before awaiting the combined result |
| Does the code wait for the Promises to complete? | Does not collect/await the callback Promises | Uses `await Promise.all` | Uses `await Promise.all` |
| When is the total written to the DOM? | After invoking the callbacks, before stock results are available | After all results arrive and reduce completes | After all results arrive and the synchronous summation completes |

Once the student has confirmed that predictions were committed before testing and has assigned the testing task, the plan is to:

1. Use the correct version in mode `normal`, enable Disable cache and record network/browser conditions. Filter for `/api/stock/`, distinguishing the products request and the panel's `/__mode` requests. Do not infer the stock-request count from the total number of Network entries.
2. Record each stock request's start time, overlap in the waterfall and completion time. Concurrent JavaScript fetch calls do not guarantee that every byte is sent over the network at the same instant: browsers have connection pools, queued/stalled phases and connection limits. If a staircase appears, compare queue/initiator information and the grading script's criteria; neither automatically accept it nor automatically attribute it entirely to a sequential loop.
3. Record when `#stock-value` changes relative to the final stock response using Performance/DOM breakpoints or timestamped observations. Debugger pauses can distort timing, so do not use a paused run to establish deadline compliance. A is predicted to write `0 đ` early and never update it; B/C are predicted to write the total after all data is available.
4. Use the terminal to cross-check requests, modes and durations, but do not treat log order as request-start order: Server:141–147 logs on response finish/close. A waterfall or a tool recording request starts directly addresses the concurrency requirement.

No timestamps, waterfall or measurements are available. Do not conclude that parallel execution has been demonstrated solely from source comments, `async`, `forEach` or `Promise.all`. Fixing A by awaiting each stock request in a sequential loop could produce the correct number while violating the parallel-request requirement; this is a constraint on a future proposal, not a regression that has occurred.

## 7. Runtime observations — NOT_TESTED

| Version | Rows 1–8 and empty | Network / Console / terminal | TypeScript checker | Concurrency | Final verdict |
|---|---|---|---|---|---|
| A | NOT_TESTED | NOT_TESTED | NOT_TESTED | NOT_TESTED | None yet; pending runtime verification |
| B | NOT_TESTED | NOT_TESTED | NOT_TESTED | NOT_TESTED | None yet; pending runtime verification |
| C | NOT_TESTED | NOT_TESTED | NOT_TESTED | NOT_TESTED | None yet; pending runtime verification |

Do not record empirical PASS/FAIL results, “What I saw”, screenshots or diagnostics on the student's behalf. If later results contradict a prediction, retain the committed prediction and add the results/timing in a separate section; do not rewrite prediction history to match the results.

## 8. Student acceptance and handoff

Read **§3.3–3.4** carefully (A: parallel initiation without waiting; row 7 does not automatically fail), **§4.3** (B: the timeout logic error is separate from the type error), **§5.3–5.5** (C: keep remains conditional), and **§2 and §6** (timing, environment and concurrency measurements). The tables in §3.2/4.2/5.2 contain all 27 predictions, not 27 results.

**Student acceptance — 2026-11-04 (Asia/Bangkok, UTC+7):** the student accepted the current 27 predictions and explicitly authorized updating this acceptance status, committing the two existing reports and pushing to `origin/main`. The predictions and qualifications remain unchanged: A provisionally requires a fix for row 2; B for rows 6 and 8; C is a conditional keep. No final runtime verdict or student-authored test observation is implied.

At the original drafting handoff, the two draft files had been created in the working tree, **without a commit/push**, starter changes or testing. The student's subsequent instruction separately authorizes committing and pushing these reports. `AI-LOG.md` is retained unchanged at the student's request as the record of that original drafting session; its pending-review wording describes the earlier handoff. The current acceptance is recorded here. Git history and the publication handoff identify the resulting commit and remote verification. Testing remains **NOT_TESTED** and is not authorized by this publication instruction; it requires a separate testing task after the prediction commit has been confirmed.
