# Loom video script - 8byte Portfolio Dashboard

**Abishek M** · Full Stack assignment (R1)  
**Goal:** 8–12 minutes · Speak slowly · Point at code with your cursor

## Quick story (memorise this)

> Excel → JSON → API → Yahoo (+ Google backup) → math → UI every 15 sec.

---

## Opening (~45 sec)

**Say:**

> Hi, I am Abishek M. Thank you for reviewing my 8byte full stack assignment.
>
> I built a **real-time portfolio dashboard** with Next.js, TypeScript, Tailwind, and a Node API route.
>
> Holdings come from the Excel file saved as JSON. Live **CMP**, **P/E ratio**, and **earnings** are fetched on the **server** from Yahoo Finance, with Google Finance as backup - not from the browser.
>
> The page **refreshes every fifteen seconds** and groups stocks by **sector**.
>
> I will walk through backend first, then frontend, then the **live demo** on Vercel.

---

## 1. Portfolio data (~1 min)

**Open:** `src/data/portfolio.json`

**Say:**

> This is the **static** portfolio - **26 stocks** converted once from Excel.
>
> Each row has: company name, symbol, buy price, quantity, sector, and NSE or BSE.
>
> These numbers do not update on refresh. Only market fields (CMP, P/E, earnings) come from Yahoo later.

**Show:** scroll one full object (e.g. HDFC Bank).

**If asked “what is CMP?”:** current price of one share right now - see `FINANCE_TERMS.md` in the repo.

---

## 2. Types (optional, ~30 sec)

**Open:** `src/types/portfolio.ts`

**Say:**

> TypeScript shapes for the app: **Holding** from JSON, **StockPrices** from Yahoo, **PortfolioRow** after we calculate investment and gain/loss.

---

## 3. API route (~1 min)

**Open:** `src/app/api/portfolio/route.ts`

**Say:**

> This is the **only** backend entry the browser uses: `GET /api/portfolio`.
>
> Flow: check **15-second cache** → if miss, call `buildPortfolioData()` → return JSON.
>
> `?refresh=true` clears cache for a full refetch.
>
> `maxDuration` is **60 seconds** so Vercel has time for all 26 stocks.

**Point at:** `GET` · `getCachedData` / `saveToCache` · `buildPortfolioData` · `maxDuration`

---

## 4. Cache (~20 sec)

**Open:** `src/services/cache.ts`

**Say:**

> Simple in-memory cache - same **15 seconds** as the UI poll - so we do not hit Yahoo on every browser refresh.

---

## 5. Yahoo Finance - core (~1.5 min) ⭐ most important

**Open:** `src/services/yahooBatchCore.ts`

**Say:**

> This file fetches **live data inside the API** - it works on **Vercel** after deploy.
>
> **NSE** symbols → `.NS` (e.g. `HDFCBANK.NS`). **BSE** numbers → `.BO`.
>
> For each stock we try: **quote** → **quoteSummary** (P/E, earnings) → **chart URL** if price still missing.
>
> Small **delay between stocks** to reduce Yahoo rate limits.

**Point at:** `getYahooSymbol` · `fetchOneFromYahoo` · `fetchYahooBatchInProcess`

**Open:** `src/services/yahooFinance.ts` (~45 sec)

**Say:**

> This **orchestrates** fetching: batches of **8 stocks**, then Google backup if P/E or earnings is missing.
>
> Calls `yahooBatchCore` in batches of eight, then Google backup if P/E or earnings is missing.

**Point at:** `fetchAllStocks` · `STOCKS_PER_BATCH` · `addGoogleDataIfMissing`

---

## 6. Google Finance backup (~25 sec)

**Open:** `src/services/googleFinance.ts`

**Say:**

> When Yahoo misses P/E or earnings, we try Google Finance. No official API - best effort. If both fail, the table shows **-** and the app keeps working.

---

## 7. Calculations & portfolio build (~1 min)

**Open:** `src/services/portfolioService.ts`

**Say:**

> Combines static JSON + live prices into table rows, then sector groups and grand totals.

**Point at:** `buildPortfolioData` · `buildStockRow`

**Open:** `src/utils/calculations.ts`

**Say:**

> Pure math, no API:
>
> - **Investment** = buy price × quantity  
> - **Present value** = CMP × quantity  
> - **Gain / loss** = present value − investment  
> - **Portfolio %** = this stock’s investment ÷ total × 100  

**Open:** `src/utils/grouping.ts`

**Say:**

> Groups rows by sector (Financial, Technology, etc.) with sector-level totals.

**Open:** `src/utils/formatters.ts` (~15 sec)

**Say:**

> Indian rupee formatting; **green** profit, **red** loss.

---

## 8. Frontend data hook (~45 sec)

**Open:** `src/hooks/usePortfolio.ts`

**Say:**

> On load: fetch `/api/portfolio`. Then **setInterval** every **15 seconds**.
>
> First visit → `loading` true (loader). Later polls → `isRefreshing`. **retryLoad** uses `?refresh=true`.

**Point at:** `REFRESH_EVERY_MS` · `loadData` · `setInterval`

---

## 9. UI components (~2 min)

Open each file briefly while speaking.

| File | What to say |
|------|-------------|
| `PortfolioLoader.tsx` | First load - spinner, “Building your dashboard”, while server fetches 26 stocks |
| `page.tsx` | Page title and layout shell |
| `Dashboard.tsx` | Loader → error + retry → main dashboard |
| `DashboardHeader.tsx` | Four cards: invested, current value, P/L, last updated |
| `PortfolioTable.tsx` | TanStack table; all assignment columns; **even rows** light grey; green/red P/L |
| `PortfolioChart.tsx` | Sector bar chart - invested vs current; chart mounts client-side (Recharts fix) |
| `SectorSummary.tsx` | Same table under each sector header with sector totals |

**Say (while on table):**

> Columns match the assignment: buy price, qty, investment, weight, live CMP, value now, gain/loss, P/E, earnings.

**Tip:** Hard refresh once on demo so reviewers see the **loader** for a few seconds.

---

## 10. Live demo (~2 min)

**Open:** **https://8byte-abishek.vercel.app** (or localhost)

**Say:**

> Here is the **deployed** dashboard on Vercel.
>
> First load - loading screen, then data appears (can take up to a minute on cold start).
>
> Top: **summary cards**. Middle: **sector chart**. Main **table** with live CMP and coloured gain/loss.
>
> Bottom: holdings **grouped by sector**.
>
> Watch **last updated** - changes about every **15 seconds**.

**Do:**

1. Show loader (refresh with `?refresh=true` on API if needed)  
2. Scroll table - point one green and one red row  
3. Scroll sector section  
4. Optional: open `/api/portfolio?refresh=true` - “raw JSON for debugging”

---

## 11. Challenges (~30 sec)

**Say (no need to open file):**

> Main challenges: unofficial Yahoo/Google APIs, **rate limits**, Yahoo **not bundling** cleanly in Next (fixed with `yahooBatchCore` + Vercel in-process), first load **slow**, some symbols like **LTIM** missing data.
>
> I documented fixes in **CHALLENGES.md** - caching, batching, fallbacks, error handling.

---

## Closing (~20 sec)

**Say:**

> To summarise: **JSON holdings** → **API with cache** → **Yahoo on the server** → **calculations and sectors** → **React UI with auto-refresh**, deployed on **Vercel**.
>
> Thank you for your time. I am happy to go deeper in the next interview round.

---

## If something goes wrong while recording

| Problem | What to do / say |
|---------|------------------|
| Stuck on loader long | Normal first time - “server is fetching 26 stocks from Yahoo” |
| All P/E empty on Vercel | Mention `yahooBatchCore` fix; ensure latest deploy |
| P/E empty locally | “Need Node 22” - `nvm use 22` |
| LTIM shows - | “Yahoo has no price for that symbol - dash instead of crash” |
| Wrong JSON error in logs | Was `console.log` in batch script - now fixed, stderr only |

---

## Pre-submit checklist

- [ ] Loom link added to README + reply email  
- [ ] CHALLENGES.md exported to PDF (if HR asked)  
- [ ] Vercel `/api/portfolio?refresh=true` - CMP + some P/E populated  
- [ ] Delete this file from public repo if you want (optional)

---

## File order (one screen cheat sheet)

1. `portfolio.json`  
2. `types/portfolio.ts` *(skip if short on time)*  
3. `api/portfolio/route.ts`  
4. `cache.ts`  
5. `yahooBatchCore.ts` ⭐  
6. `yahooFinance.ts` (batching + Google backup)  
7. `googleFinance.ts`  
8. `portfolioService.ts` → `calculations.ts` → `grouping.ts` → `formatters.ts`  
9. `usePortfolio.ts`  
10. `PortfolioLoader` → `Dashboard` → header → table → chart → sectors  
11. **Live demo** (Vercel)  
12. Challenges *(verbal)*  

---

## Timing guide

| Section | Minutes |
|---------|---------|
| Opening + data + API | ~3 |
| Yahoo + Google + math | ~4 |
| Frontend + UI | ~2.5 |
| Demo + close | ~2.5 |
| **Total** | **~10–12** |

Cut optional parts (types, formatters) to stay under **8 minutes**.
