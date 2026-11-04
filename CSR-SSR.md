# CSR vs SSR — the same catalogue, built in two places

Observed on 2026-11-04 at about 21:22 (UTC+7) with a Playwright 1.64.1 script driving headless Chromium 153, from a folder outside the repo. The server was the running `node server.mjs` at `http://localhost:5050`, in mode `normal` before and after. CSR page: `/?v=c`. SSR page: `/ssr`.

## 1. On `/?v=` any version and on `/ssr`, right-click → View page source (`Ctrl+U`). Where are the product names in each? Where is the stock value?

- **`/?v=c` source** (HTTP 200, 2293 bytes): no product name appears in it (0 matches for each of the 8 names). The list and the card template are empty: `<ul class="catalogue" id="catalogue"></ul>` and `<h2 class="name"></h2>`. The stock value is only a placeholder: `<output id="stock-value">—</output>`. The names arrive later as JSON from `GET /api/products`, and `c.js` puts them into the page.
- **`/ssr` source** (HTTP 200, 1939 bytes): all 8 names are in the HTML, one per card, e.g. `<h2 class="name">T-shirt</h2>`. The finished total is in the markup too: `<output id="stock-value">12.360.000 đ</output>`. The source contains no `<script>` tag at all.

## 2. In `/ssr`'s source, find the scarf. Why does it read `&lt;i&gt;` there, and what does that have in common with `textContent` in the browser?

- The scarf line in `/ssr`'s source: `<h2 class="name">Scarf &lt;i&gt;limited&lt;/i&gt;</h2>`.
- The server writes `${escapeHtml(p.name)}` (`server.mjs:81`), and `escapeHtml` replaces the special characters with entities: `.replaceAll('&', '&amp;').replaceAll('<', '&lt;').replaceAll('>', '&gt;')` (lines 67–71). The browser displays the entities as the characters `<` and `>`, so the page shows `Scarf <i>limited</i>`, not italics.
- `textContent` does the same job in the browser. On `/?v=c`, the scarf's `.name` has `textContent` `Scarf <i>limited</i>`, `innerHTML` `Scarf &lt;i&gt;limited&lt;/i&gt;` and **0 child elements**.
- What they have in common: both treat the name as text, not markup. Server-side escaping and `textContent` keep `<i>` (or a `<script>`) in a product name from becoming HTML.

## 3. Disable JavaScript (DevTools settings, above) and reload both pages. What is left of each?

With `javaScriptEnabled: false`:

| | Status line | Cards | Stock value | Requests made |
|---|---|---|---|---|
| `/?v=c` | empty (`""`) | **0** | **`—`** | `/`, `/style.css` |
| `/ssr` | empty (`""`) | **8** | **`12.360.000 đ`** | `/ssr`, `/style.css` |

On `/?v=c` only the static shell is left: header, an inactive "Test conditions" panel showing `Server mode: unknown`, `Stock value: —` and an empty list. `/ssr` looks exactly as it does with JavaScript on.

## 4. In the Network tab, count the requests each page makes before the stock value appears. Which page would a search engine, or a user on a slow phone, see first?

JavaScript was on, the cache was disabled and there was no throttling. A request was counted if it started before `#stock-value` first held a real value.

- **`/?v=c`: 14 requests, value at 680 ms.** In order: document `/?v=c`, `style.css`, `panel.js`, `GET /__mode`, `versions/c.js`, `/api/products` (at 43 ms), then 8 × `/api/stock/…`, all started at 56.1–56.8 ms. The cards appeared at 57 ms; the total appeared at 680 ms, just after the slowest stock response (677 ms).
- **`/ssr`: 2 requests, value at 12 ms.** Document `/ssr` and `style.css`. The value was already in the HTML while it was being parsed (12.3 ms), and was on screen at the first paint (52 ms).
- **SSR is seen first.** The products and the total come in the first response, so a crawler that does not run JavaScript, or a slow phone, gets them without waiting on a chain of five dependent steps (HTML → `panel.js` → `c.js` → `/api/products` → `/api/stock/…`). On a slow network, every step in that chain costs another full round-trip.

## 5. One sentence: when would you want the server to render, and when the browser?

Render on the server when the content has to be visible and indexable from the first response (public catalogue pages, articles, slow devices or networks). Render in the browser when the page is an interactive app that changes after load without a full reload (filters, a cart, a dashboard, or this page's mode switch and Retry button), where SEO and the first paint matter less.
