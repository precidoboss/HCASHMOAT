# 💧 hCASH Moat — Liquidity Intelligence

> **Real-time LP intelligence, miner analytics, and complete DeFi tooling for the hCASH / AVAX ecosystem on Avalanche C-Chain.**

Built by [@precidobos](https://x.com/precidobos) for the [@clubhashcash](https://x.com/clubhashcash) community · [moats.app](https://moats.app)

---

## What Is This?

hCASH Moat Intel is a **single-file, zero-install web dashboard** that aggregates everything an hCASH participant needs into one place. Whether you're a liquidity provider trying to maximize Moat Points, a miner deciding which hardware to buy, or a new user just learning the ecosystem — this app gives you live on-chain data, interactive calculators, and direct wallet actions without ever leaving the page.

It pulls live data directly from the HashCash API, Pharaoh Exchange pools on Avalanche, the Moats protocol contract, and the Avalanche C-Chain RPC. No backend, no database, no server costs.

---

## Table of Contents

1. [Getting Started](#getting-started)
2. [Connecting Your Wallet](#connecting-your-wallet)
3. [Dashboard](#1-dashboard)
4. [Liquidity Tab](#2--liquidity)
5. [Stake / Lock View](#3--stake--lock)
6. [Moat Explorer](#4--moat-explorer)
7. [Calculator](#5--calculator)
8. [Miners](#6--miners)
9. [Leaderboard](#7--leaderboard)
10. [Activity Feed](#8--activity-feed)
11. [What If? Scenario Planner](#9--what-if-scenario-planner)
12. [Build — Custom Facility Simulator](#10--build--custom-facility-simulator)
13. [Key Concepts Explained](#key-concepts-explained)
14. [Tech Stack](#tech-stack)
15. [Contract Addresses](#contract-addresses)
16. [Links](#links)

---

## Getting Started

No install or build step required. The entire app lives in a single `index.html` file.

```bash
git clone https://github.com/YOUR_USERNAME/hcash-moat-intel.git
cd hcash-moat-intel
open index.html   # or drag into any modern browser
```

Or serve it locally for full wallet support:

```bash
npx serve .
# Visit http://localhost:3000
```

> **Tip:** For wallet features (Add LP, Stake, Lock, Claim), open in a browser that has **MetaMask** or **Core** installed and switch to **Avalanche C-Chain (Chain ID 43114)** before connecting.

---

## Connecting Your Wallet

Click **Connect Wallet** in the top-right corner. The app will prompt your wallet extension to authorize the connection. Once connected:

- Your wallet address appears in the header (e.g. `0xAbC…1234`)
- Your AVAX, hCASH, and LP token balances load automatically on the Liquidity tab
- Your staked position, Moat Points, and Fort Score populate on the Dashboard and Stake/Lock view
- All transaction buttons (Add LP, Stake, Lock, Claim, etc.) become active

To disconnect, click the **✕** next to your address in the header. The app supports **MetaMask** and **Core Wallet** — any EIP-1193 compatible provider will work.

---

## 1. Dashboard

**The command center. Loads automatically on startup with no interaction required.**

The Dashboard gives you a live snapshot of the entire hCASH ecosystem. Data refreshes on page load; hit **↺ Refresh** to pull the latest at any time.

### Live Stat Cards

| Stat | What It Shows |
|---|---|
| hCASH Price | Current market price in USD with 24h % change |
| Market Cap | Fully diluted valuation of hCASH |
| LP Liquidity | Total USD value locked in the AVAX/hCASH Pharaoh pool |
| Volume 24h | Last 24 hours of swap volume through the Pharaoh pool |
| Moat Stakers | Number of unique wallets currently staking in the hCASH Moat |
| Total Points | Sum of all Moat Points earned across every participant |
| Current Block | Latest Avalanche C-Chain block number with approximate timestamp |
| Network Hash | Total hCASH mining hashrate across all active facilities |
| Emission/Block | How many hCASH are minted per block at the current rate, plus daily total |
| Halving In | Blocks remaining until the next emission halving event |
| Facilities | Number of active mining facilities on hashcash.club |

### My LP Position Card

If your wallet is connected, this card shows your LP tokens staked in the Moat, your share of the total pool (%), your accumulated Moat Points, and your Fort Score. A **Manage →** button links directly to the Liquidity tab. If not connected, a prompt appears to connect.

### Pool Composition Card

A live breakdown of the Pharaoh AVAX/hCASH pool: how many AVAX and hCASH tokens are currently in reserve, the current pool ratio (which is effectively the exchange rate between the two tokens), and the total LP token supply outstanding.

### LP Signals

An auto-generated list of signals based on current pool conditions — warnings if volume is too low to generate meaningful fees, green signals when yield looks healthy, and notes about upcoming halvings that would affect mining returns.

---

## 2. 💧 Liquidity

**Manage your AVAX/hCASH LP position end-to-end — all from one tab, six sub-tabs.**

Your wallet balances (AVAX, hCASH, LP tokens) appear in a strip at the top once connected. Quick links to **Pharaoh**, **LFJ (Trader Joe)**, and **hashcash.club** let you buy hCASH without leaving the app.

---

### Add LP

**How to add liquidity to the AVAX/hCASH pool on Pharaoh Exchange.**

1. Make sure your wallet is connected and holds both AVAX and hCASH.
2. Enter the amount of **AVAX** you want to deposit. The hCASH field auto-fills at the current pool ratio — you don't need to calculate it yourself.
3. Use **MAX** to fill your entire available AVAX balance.
4. Set your preferred **slippage tolerance**:
   - `0.5%` — tight, may fail in volatile markets
   - `1%` — default, recommended for most users
   - `2%` — always fills, but accepts more price impact
5. Click **💧 Add Liquidity**.
6. Approve the hCASH spend in your wallet (one-time per session), then confirm the main transaction.
7. Once confirmed, **Pharaoh LP tokens** appear in your wallet.

> **What are LP tokens?** They're your receipt for depositing into the pool. They represent your proportional ownership of the AVAX/hCASH reserves and entitle you to a share of every swap fee generated by that pool. You must then **stake** them in the Moat to start earning Moat Points on top of fees.

---

### Remove LP

**How to exit the pool and receive your AVAX + hCASH back.**

> If your LP tokens are currently **staked** in the Moat, you must unstake them first. The app shows an **↩ Unstake First** button if this applies to you.

1. Enter the amount of LP tokens to withdraw, or hit **MAX** to remove everything.
2. A preview shows exactly how much AVAX and hCASH you'll receive back at the current pool ratio.
3. Click **💧 Remove LP** and confirm in your wallet.
4. AVAX and hCASH return to your wallet. The LP tokens are burned by the pool contract.

---

### Stake

**Deposit LP tokens into the hCASH Moat to start earning Moat Points.**

Staking is the flexible option — no time commitment, unstake whenever you want (subject to a 0.5% exit fee). You earn points at a **1× base rate**.

1. Enter the LP amount to stake, or hit **MAX**.
2. A preview shows your estimated Moat Points per day at the current rate.
3. Click **🔒 Stake LP in Moat** and confirm the transaction.
4. Points begin accumulating **every second** from the moment the transaction is confirmed.

> **0.5% unstake fee** applies when you withdraw flexible stakes. This fee goes to remaining stakers and the protocol — a small cost for maximum flexibility.

---

### Lock

**Time-lock your LP tokens for a boosted Moat Points multiplier (2.04× up to 5×).**

Locking is the most powerful points strategy. Your LP tokens cannot be withdrawn early without paying an **EEL penalty** (see Key Concepts below), but your points accumulate much faster.

**Lock duration options:**

| Duration | Multiplier |
|---|---|
| 30 days | 2.04× |
| 90 days | 2.50× |
| 180 days | 3.00× |
| 365 days | 4.00× |
| 730 days | 5.00× |

**How to lock:**

1. Select a lock duration from the duration grid.
2. Enter the LP amount you want to lock (or hit MAX).
3. The preview shows your total Moat Points accumulated over the full lock period.
4. Click **⏳ Lock LP Now** and confirm in your wallet.
5. Your active locks appear below with each lock's unlock date, amount, and current EEL penalty if you were to exit early today.

> You can have multiple locks running simultaneously at different durations. Each lock is tracked independently with its own unlock date and multiplier.

---

### Unstake

**Withdraw your flexible (non-locked) LP tokens from the Moat.**

1. Enter the amount to unstake, or leave blank and use **MAX** to unstake everything.
2. Click **↩ Unstake from Moat** and confirm.
3. LP tokens return to your wallet minus the 0.5% exit fee.

> **Locked positions cannot be unstaked here.** Locked LP is only released when the lock matures, or via EEL early-exit with a significant penalty.

---

### Claim Rewards

**Collect your accumulated swap fee income and any special reward distributions.**

The tab loads your pending reward balance from the Moat contract. Click the claim button and confirm in your wallet. Rewards arrive as hCASH (or the token distributed by the Moat at the current epoch).

**Miner NFT Rewards** — also visible here. If you ranked in the **Top 10 on the Moats leaderboard** at snapshot time, you received a Miner NFT airdrop. Two NFTs are tracked:

- **Miner #27** — 100 MH/s, 100W, supply of 10
- **Miner #40 (The Grotto Miner)** — 150 MH/s, 200W, supply of 10

The tab displays each NFT's image (if loaded), full stats, a Snowtrace link, and the current list of holders.

---

## 3. 🔒 Stake / Lock

**A dedicated overview of your staking and locking positions, with the Fort Score Optimizer.**

### Position Summary

Shows your total flexible-staked LP, total locked LP across all active locks, your cumulative Moat Points, and your current Fort Score — all in one clean view.

### Points Estimate

A live projection card that updates as you adjust stake/lock amounts. Shows daily points earned and a running total at the end of your chosen lock period.

### Fort Score Optimizer

Click **↺ Analyze** with your wallet connected. The optimizer reads your positions across all Moats you've joined and tells you:
- Your current Fort Score and what % of the ecosystem total you represent
- Which lock duration would maximize your points given your available LP
- Whether moving flexible stakes into locks would meaningfully improve your ratio

### Lock Multiplier Reference Grid

A visual grid of all lock durations and their multipliers — a quick at-a-glance reference when planning your strategy.

### EEL Early-Exit Penalty Reference

A table showing the penalty rate you'd pay at different stages of lock completion. Penalty starts at **95% on day 0** and drops linearly to **0% on the final day**. Penalized LP is redistributed to remaining stakers and the protocol — this is a direct incentive to stay committed.

---

## 4. ⬡ Moat Explorer

**Inspect the hCASH Moat contract transparently — all participants, all stats, no wallet needed.**

### Hero Banner

Displays the Moat contract address, LP token address, chain (Avalanche C-Chain ID 43114), DEX (Pharaoh Exchange), and confirms that the **burn mechanism is disabled** — this Moat is stake + lock only. Direct links to Snowtrace and moats.app are in the corner.

### On-Chain Stats

Live data pulled directly from the Moat contract including total LP staked, total LP locked, average lock duration across all participants, and the protocol fee rate.

### Top LP Stakers Table

Ranked by Moat Points — all participating wallets, their points, and their % share of total ecosystem points. This determines your relative position in the airdrop distribution.

### hCASH LP Token Holders

All wallets holding AVAX/hCASH LP tokens, ranked by balance. Data is assembled by scanning on-chain Transfer events from the LP contract address. Covers LP in wallets, in the Moat, and in any other protocol.

### How the hCASH LP Moat Works

An inline explainer covering three critical concepts:

**EEL Penalty** — If you exit a lock early, a penalty is deducted from your returned LP tokens. The penalized tokens are redistributed to the protocol and remaining stakers. The penalty makes early exits expensive, especially near the beginning of a lock.

**Fort Score** — Your Moat Points from all moats you participate in are summed into a Fort Score. Your Fort Score as a % of all Fort Scores in the ecosystem = your share of Early User Airdrops and future protocol rewards.

**LP vs Token Moat** — Unlike regular token moats where you deposit raw tokens, hCASH Moat accepts **Pharaoh LP tokens**. This means your capital earns *twice*: swap fees from every AVAX/hCASH trade that routes through the pool, AND Moat Points from the staking protocol simultaneously.

---

## 5. 🎛 Calculator

**Plan your investment and model EEL penalties before committing any capital.**

### Investment Calculator

Answers: *"I have $X — what do I get if I go LP?"*

1. Enter your budget in **USDC**.
2. The calculator automatically splits it 50% AVAX / 50% hCASH using live prices.
3. Select a lock strategy (30 / 90 / 180 / 365 / 730 days).
4. Results instantly show:
   - How much AVAX and hCASH you'd buy
   - Estimated LP tokens received at the current pool ratio
   - Projected Moat Points over the full lock period at that multiplier
   - Estimated daily swap fee income based on current 24h pool volume

No wallet needed — this is a pure planning tool.

### EEL Penalty Calculator

Answers: *"If I exit my lock early right now, how much do I lose?"*

1. Enter your **lock duration** in days (e.g. 180).
2. Enter the **LP amount** you have locked.
3. Enter **days already served** into the lock.
4. Results instantly show:
   - % of the lock period complete
   - Current penalty rate (%)
   - Exact LP tokens you'd lose to the penalty
   - LP tokens you'd actually receive back

Use this before making any early-exit decision to understand the true cost.

### Council Score Calculator

For participants in **multiple Moats** across the ecosystem. Enter your Moat Points from each moat (add rows with **+ Add Another Moat**), and the calculator computes your **Council Score** including the diversity bonus awarded for participating in more than one moat. The more moats you're active in, the higher your Council Score bonus.

---

## 6. ⛏ Miners

**Browse the full hCASH mining hardware catalog with live market data and ROI stats.**

HashCash miners are **ERC-721 NFTs** you place into facilities on hashcash.club to generate hCASH. Miners differ in hashrate (MH/s) and power draw (W). Higher hashrate = more hCASH per block; higher wattage = higher electricity cost. Your net income = gross hCASH earned minus electricity cost.

### Filter & Sort Bar

- **Name search** — filter the grid in real time as you type
- **Sort by**: Name A→Z · Hashrate (highest first) · Power draw (highest first) · Efficiency (MH/W, highest first)
- **Filter by type**: Miners (standard NFT) or Rig Assemblers (composable rigs with multiple slots)
- **Clear button** — reset all filters instantly
- A **count label** shows how many items match your current filter

### Miner Cards

Each card shows the miner name, type badge, hashrate (MH/s), power draw (W), efficiency score (MH per Watt), and all current marketplace listings with prices in both hCASH and USD. Click any card to open the **Miner Detail** view.

### Miner Detail View

A full-page breakdown of a single miner:
- All stats (hashrate, power, efficiency rating)
- All current marketplace listings and their prices
- Estimated daily hCASH yield at the current network difficulty and emission rate
- Break-even timeline at current hCASH price
- A direct button to open that miner in the **🔮 What If?** tool for a full LP comparison

### Rig Assemblers

A separate section below the miners grid. Rigs are multi-slot composable units — you populate them with individual miner NFTs to scale hashrate within a single facility slot.

### Other HashCash Contracts

A reference list of other contracts in the hCASH ecosystem with Snowtrace links for on-chain verification.

---

## 7. 🏆 Leaderboard

**Ranked table of every wallet in the hCASH Moat by accumulated Moat Points.**

The leaderboard shows all Moat participants in descending order of points. Data loads from the Moats API on tab entry and can be refreshed with **↺ Refresh**.

| Column | Description |
|---|---|
| # | Rank (1 = most points in the Moat) |
| Wallet | Shortened address — search by address in the filter box |
| Points | Total Moat Points accumulated to date |
| Share | This wallet's % of all points in the Moat |
| Method | How they accumulated points (flexible stake vs lock, lock duration used) |

Use the **search box** to find a specific wallet address and check your own rank. The leaderboard is the primary reference for airdrop share estimates.

---

## 8. 📡 Activity Feed

**Live on-chain event stream for the hCASH Moat — see what other participants are doing in real time.**

### Event Types

Use the **filter dropdown** to narrow the feed to specific events:

| Filter | Description |
|---|---|
| 🔒 Staked | Someone deposited LP tokens into the Moat (flexible stake) |
| ⏳ Locked | Someone created a new time-locked position |
| 💰 Rewards | Someone claimed their accumulated reward balance |
| ↩ Unstake / Exit | Someone withdrew LP tokens from the Moat |
| ⚡ EEL | Someone triggered an early exit from a lock — penalty was applied |

Each event row shows the wallet address, action type, token amount, and a relative timestamp. The feed is scrollable and loads the most recent on-chain events first.

### Moat Stats Sidebar

Alongside the feed, an aggregate stats panel shows total events in the loaded history, a breakdown by event type, and net flow (LP deposited minus LP withdrawn) for the visible period — useful for reading whether the Moat is growing or shrinking.

---

## 9. 🔮 What If? Scenario Planner

**The most powerful tool in the app. Compare buying a miner vs putting the same capital into LP — with real on-chain math, live prices, and a clear verdict.**

The core question this tool answers: *"You're about to spend X hCASH on a miner from the marketplace. What if you just put that money into LP instead?"*

---

### Step 1 — Browse the Live Marketplace

The top panel loads all currently listed miners from the HashCash marketplace in real time. Listings update automatically.

**Filter and sort the marketplace:**
- **Name search** — filter listings as you type
- **Sort by**: Price low→high · Price high→low · Hashrate highest · Efficiency highest
- **Minimum hashrate filter**: All · ≥100 MH/s · ≥150 MH/s · ≥200 MH/s · ≥500 MH/s
- A count shows how many listings match your filters

Click any listing card to add it to your **facility cart**.

---

### Step 2 — Build Your Facility Cart

After selecting miners, a cart panel appears:

- All selected miners are listed with names and prices
- **Facility Level selector** — choose 1 of 5 facility levels, each with different slot capacity, total power, and electricity cost:

| Level | Grid | Slots | Max Power | Electricity Rate |
|---|---|---|---|---|
| Lv1 | 2×2 | 4 | 400W | 8.87 hCASH/kWh |
| Lv2 | 2×3 | 6 | 1,000W | 7.09 hCASH/kWh |
| Lv3 | 3×3 | 9 | 2,000W | 6.21 hCASH/kWh *(default)* |
| Lv4 | 3×4 | 12 | 6,000W | 7.09 hCASH/kWh |
| Lv5 | 4×4 | 16 | 15,000W | **3.55 hCASH/kWh** *(best)* |

- A **slot grid preview** shows which slots are filled with which miners and a power usage bar indicating how close you are to the facility's power cap
- A slot summary shows current fill (e.g. "5/9 slots · 850W")

Click **⚡ Run Simulation →** when your facility is set up.

---

### Step 3 — Path B Auto-Fills

While you build your miner cart, the **Path B — LP** panel calculates automatically in the background:

- Takes the **exact same USD value** as your total miner spend
- Splits it 50% AVAX / 50% hCASH at live market prices
- Calculates how many LP tokens you'd receive at the current pool ratio
- Shows your resulting pool share percentage
- Lets you choose a **lock duration** (30 / 90 / 180 / 365 / 730 days) to apply the Moat multiplier to the LP path's point projection

All fields update live as you change miners or facility level.

---

### Results — Full Side-by-Side Comparison

After running the simulation, a complete comparison table appears:

| Metric | ⛏ Miner | 💧 LP |
|---|---|---|
| Daily gross income (hCASH) | Mining reward at current hashrate share | Your share of 24h swap fees |
| Electricity cost/day | Facility kWh × facility rate | None |
| Net/day (hCASH) | Gross minus electricity | Full fee amount |
| Net/day (USD) | At live hCASH price | At live prices |
| 30-day net (hCASH) | Projected | Projected |
| 30-day net (USD) | Projected | Projected |
| 1-year net (hCASH) | Projected | Projected |
| 1-year net (USD) | Projected | Projected |
| Break-even | Days to recover total purchase cost | Already liquid — capital preserved |
| Network share | Your % of total hCASH hashrate | — |
| Moat Points | None (miners earn 0 points) | Points at chosen lock multiplier |
| Capital (exit anytime) | Illiquid (spent on NFT) | Liquid (remove LP anytime) |

---

### Winner Banner

A verdict badge at the top of the results section:

- **⛏ MINER EARNS MORE** — miner annual USD income exceeds LP by more than 20%
- **💧 LP WINS** — LP annual income exceeds miner by more than 20%, or miner is unprofitable at the facility electricity rate
- **⚖️ IT DEPENDS** — difference is within 20%; outcome depends on your priorities
- **⛔ Do NOT buy at this price** — electricity costs exceed the miner's gross earnings entirely

---

### Key Signals

Auto-generated flags below the table that highlight important conditions:

| Signal | Meaning |
|---|---|
| 🚀 Fast break-even | Miner recovers cost in under 90 days |
| ⏳ Slow break-even | Break-even over 365 days — significant price-drop risk during payback period |
| 💧 Meaningful LP share | Your pool % is large enough to generate real daily fee income |
| 🔒 Strong lock multiplier | 4× or higher multiplier is active for the LP path |
| ⚡ Zero power cost | Lv5 facility or manually set wattage to 0 — pure hCASH income, no deductions |
| 🏰 LP earns Moat Points | Reminder that the miner path earns 0 Moat Points unless you also run a separate LP position |

---

### 365-Day Earnings Chart

A dual-line chart projecting **cumulative net USD income over one year** for both paths. The miner line is red; the LP line is gold. Where the lines cross (if at all) is the true break-even and crossover point — not just the purchase-cost recovery, but when total lifetime income flips in favor of one path over the other.

---

### Verdict Card

A structured decision guide:

**Buy the miner if…**
- You want direct hCASH income (mining is guaranteed hCASH, not USD-denominated fees)
- You expect hCASH price to rise significantly before break-even
- The break-even timeline feels acceptable given your time horizon
- You don't need your capital to remain liquid

**Choose LP if…**
- You want capital flexibility (LP can be removed anytime, no NFT to resell)
- You want Moat Points and Fort Score growth for airdrop eligibility
- Pool volume is healthy (the app flags this — low volume means low fees)
- You believe in the long-term ecosystem and want dual exposure

**Best of both worlds** — a highlighted note at the bottom: *Buy the miner AND run a smaller LP position simultaneously. You get hCASH income from mining, swap fees from LP, and Moat Points from the LP stake — all at once.*

---

## 10. 🔨 Build — Custom Facility Simulator

**Same power as What If?, but with full manual control — for miners you already own or prices that aren't listed on the marketplace.**

The Build tab is designed for scenarios where you're not looking at a specific marketplace listing. You already have miners, bought them off-market, or want to model hypothetical prices.

### Step 1 — Enter a Price

Type any price in the input field. Toggle between **hCASH** and **AVAX** denomination using the dropdown. A USD equivalent appears below the field in real time using live prices.

### Step 2 — Choose Facility Level

Same five facility options as What If? — select the level that matches the facility you're planning to run your miners in. This determines slot capacity, power ceiling, and electricity cost per kWh.

### Step 3 — Add Miners to Slots

Search for any miner by name in the slot search box. A dropdown populates from the full HashCash miner catalog. Select the miner you want to add, set whether you're buying it (adds to total cost) or already own it (not added to cost), then click **+ Add to Facility**.

Each added miner occupies one slot in the facility. The slot table updates live showing:
- Each slot's miner name
- Hashrate (MH/s)
- Power draw (W)
- Price (if being purchased)

Use **Clear All** to reset the entire facility and start over.

### Step 4 — Run Comparison

Click **Run Comparison**. The results section is identical to What If? — side-by-side table, winner banner, 365-day chart, key signals, and a full verdict card — all computed using your custom configuration and live on-chain data.

---

## Key Concepts Explained

### Moat Points
Points accumulate every second your LP tokens are staked or locked in the hCASH Moat. The rate is proportional to the amount of LP tokens you have in, multiplied by the lock multiplier. Points are non-transferable and represent your sustained commitment to the hCASH liquidity ecosystem.

### Fort Score
Your Fort Score = the sum of Moat Points you've earned across **all Moats** in the Fortifi ecosystem (not just hCASH). Your Fort Score as a percentage of the total ecosystem Fort Score determines your share of Early User Airdrops and protocol distributions.

### Lock Multiplier
Time-locking your LP tokens multiplies your points accumulation rate:

| Lock | Multiplier |
|---|---|
| No lock (flexible stake) | 1× |
| 30 days | 2.04× |
| 90 days | 2.50× |
| 180 days | 3× |
| 365 days | 4× |
| 730 days | 5× |

### EEL (Early Exit Liquidity) Penalty
If you exit a lock before it matures, a sliding penalty is applied to your returned LP tokens. The penalty is **95% at day 0** (you'd recover almost nothing) and decreases linearly to **0% on the final day** of the lock. Penalized tokens are redistributed to remaining stakers and the protocol — they directly reward users who honor their lock commitments.

### LP vs Token Moat
Unlike moats that accept raw ERC-20 tokens, the hCASH Moat accepts **Pharaoh LP tokens** (AVAX/hCASH). Your capital works double: it earns **swap fees** from every trade that routes through the AVAX/hCASH pool *and* earns **Moat Points** simultaneously. Burn is disabled — no token destruction mechanism exists in this Moat.

### Miner NFTs
HashCash miners are ERC-721 NFTs with embedded specs (hashrate in MH/s, power draw in W). When placed in a facility on hashcash.club, they generate hCASH proportional to their share of the total network hashrate. Miners have **no Moat Points benefit** — they generate hCASH income only, making the LP path's points advantage a meaningful differentiator.

---

## Tech Stack

| Layer | Detail |
|---|---|
| Runtime | Vanilla HTML + CSS + JavaScript — no framework, no bundler, no Node.js required |
| Blockchain | [ethers.js v6](https://docs.ethers.org/) via CDN |
| Charts | [Chart.js v4](https://www.chartjs.org/) via CDN |
| Fonts | Chakra Petch · DM Mono · Barlow (Google Fonts) |
| Chain | Avalanche C-Chain (Chain ID 43114) |
| DEX | Pharaoh Exchange — volatile AVAX/hCASH pool |
| Data sources | HashCash API · Moats API (fortifi.network) · DexScreener · Snowtrace · Avalanche RPC |
| Wallet support | MetaMask · Core Wallet (any EIP-1193 provider) |
| Theme | Dark mode (default) / Light mode — toggle in header |
| Responsive | Mobile-first layout, tested from 380px upward |

---

## Contract Addresses (Avalanche C-Chain)

| Contract | Address |
|---|---|
| hCASH Moat | `0x501f6e7bec3db63d8dacbc9fa0ce42d5d2329d53` |
| AVAX/hCASH LP Token | `0x8f961980518bc9ab302948de7948580666dc35d9` |
| hCASH Token | `0x297731eb3cab3834525fc9ea061fd71d8f4645c9` |
| WAVAX | `0xb31f66aa3c1e785363f0875a1b74e27b85fd66c7` |
| USDC | `0xb97ef9ef8734c71904d8002f8b6bc66dd9c48a6e` |
| Pharaoh Router (legacy quotes) | `0x9cee04bdce127da7e448a333f006defb3d5e38cc` |
| Pharaoh V2 Router (execute) | `0x5acc354dEe55a5d75EF6430c1c2eBE3d6765b4E6` |
| Pharaoh Factory | `0x85448bf2f589ab1f56225df5167c63f57758f8c1` |

---

## UI Controls

| Control | Location | Action |
|---|---|---|
| Connect Wallet | Top-right header | Connects MetaMask or Core to Avalanche C-Chain |
| ✕ (after address) | Top-right header | Disconnects wallet |
| 🌙 DARK / ☀️ LIGHT | Top-right header | Toggle between dark and light theme |
| ⛏ BG ON / OFF | Top-right header | Toggle the animated mining canvas background |
| ↺ Refresh | Dashboard, Leaderboard, Activity, Explorer | Re-fetch live data for that section |
| Live ticker | Below header | Scrolling real-time price and liquidity strip |

---

## Disclaimer

> ⚠ Projections in the Calculator, What If?, and Build tabs assume constant price, hashrate, and pool volume. Real returns will vary. This tool is for informational purposes only and is **not financial advice**.

---

## Links

| | |
|---|---|
| 🌐 Protocol | [moats.app](https://moats.app) |
| ⛏ HashCash | [hashcash.club](https://hashcash.club) |
| 🦅 Primary DEX | [phar.gg](https://phar.gg) (Pharaoh Exchange) |
| 🏔️ Also tradeable on | [lfj.gg](https://lfj.gg/avalanche/trade) (LFJ / Trader Joe) |
| 🐦 Builder | [@precidobos](https://x.com/precidobos) |
| 🐦 Community | [@clubhashcash](https://x.com/clubhashcash) |
| 🔍 Moat on Snowtrace | [View contract](https://snowtrace.io/address/0x501f6e7bec3db63d8dacbc9fa0ce42d5d2329d53) |
