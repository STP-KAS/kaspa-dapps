# Rails — native Kaspa, Tether, PoC dollars, Bitcoin

Freeze: **15 Sep 2026**. Recheck sources in [SOURCES.md](SOURCES.md).

This is the money argument for Kaspa dApp developers. It is not a pitch to buy or sell anything.

---

## 1. Satoshi’s test

Bitcoin whitepaper, abstract:

> A purely peer-to-peer version of electronic cash would allow online payments to be sent directly from one party to another without going through a financial institution. Digital signatures provide part of the solution, but the main benefits are lost if a trusted third party is still required to prevent double-spending.

The test that has held since **3 January 2009**: there is no `addBlackList` on a native BTC UTXO. A government can lean on exchanges, custodians, miners, developers, and people. It cannot call a function that zeros a UTXO it does not have the keys to. Seizure requires keys or a custodian. That is the whole point.

Kaspa kept the same model on native KAS:

| Property | Bitcoin | Kaspa native KAS | USDT |
| --- | --- | --- | --- |
| Proof of work | Yes (SHA-256d) | Yes (kHeavyHash) | No. Issuer ledger |
| UTXO | Yes | Yes | Account / contract balance |
| Fair launch | Debatable history; no ICO | No premine, no ICO | Company issuance |
| Issuer freeze | **No** | **No** | **Yes** (`addBlackList`) |
| Issuer destroy | **No** | **No** | **Yes** (`destroyBlackFunds`) |
| Holder override | Keys | Keys | None |
| Programmability | Script, limited | Toccata covenants (live 30 Jun 2026) | Solidity on host chains |
| Speed | ~10 min blocks | 10 BPS (Crescendo, 5 May 2025) | Instant *inside* the issuer’s chain, subject to the key |

Crescendo and Toccata made Kaspa fast and programmable. They did **not** add an issuer key to native KAS.

A covenant can lock *your* coins to a rule you accepted. That is not the same as a company blacklisting *anyone’s* coins.

---

## 2. What Tether actually is

USDT is an IOU from Tether Limited. The Ethereum and Tron contracts give Tether two switches. One key. No holder warning. No second signature.

Bitquery pulled every `addBlackList` / `destroyBlackFunds` call on ETH + Tron from the first freeze (Nov 2017) to **12 Aug 2026**:

| Measure | Figure |
| --- | --- |
| Freeze events | 11,085 |
| Distinct addresses | 11,045 |
| Value at freeze block | **$5.85B** |
| Permanently destroyed | **$1.43B** (2,434 addresses) |
| Paid *into* already-frozen addresses | $918M (cannot be spent without Tether) |
| OFAC-designated addresses frozen | **80/80 ETH, 100/100 Tron** |
| Median wait to release (ETH) | **386 days** |
| Released addresses ever labelled illicit | 4 of 1,303 |

Trackers that count more chains (eaglevirtual, 14 Sep 2026 sample) sit around **11.5k** wallets. Direction does not change: the switch is used, often, and destruction is a Tether practice.

Circle/USDC is the same *class* with a milder record: fewer freezes, higher unfreeze rate, and a 2023 depeg to ~$0.88 when SVB failed. It repegged because **reserves were real cash**. Pause without reserves is a rug. PegLab already teaches that.

Self-custody of USDT removes *exchange* custody risk. It does **not** remove issuer risk.

---

## 3. What “USDT on Kaspa” does not fix

Kasplex (3 Mar 2026) said the stablecoin bridge follows Circle and Tether standards, BEP-20 first. That is useful liquidity. It is also an honest admission: **issuer policy travels with the token.**

If the bridge honours a freeze, the Kaspa-side inventory freezes. If it does not honour a freeze, the bridged token is no longer 1:1 with USDT and will depeg the moment Tether and the bridge disagree.

Either way:

- Kaspa GHOSTDAG orders the guest. It does not become the issuer.
- Bridge operator risk is **extra**, not instead.
- L2 security is the bridge + sequencer. Industry-wide, bridges are the largest loss category. There is no reason to assume Kasplex or Igra are exceptions. They are young.

Kasplex user counts (CoinEx, week through 12 Jul 2026): weekly active accounts **169**, down **97.8%** from a 7,613 peak. That is not “Kaspa has DeFi now.” It is a launch that did not retain users. Igra had more transactions per account and ~$1.65M TVL in that snapshot — still toy scale, and not native L1.

---

## 4. PoC alternatives, ranked by honesty

A PoC alternative matters because **the dApp unit of account is a political surface**. If that unit is Tether, Tether is a single point of failure for the app: freeze the merchant, freeze the AMM pool, freeze the agent’s gas, freeze the 402 endpoint.

### 4.1 Native KAS (use)

No freeze function. Fee asset. Sequencing asset. The only unit that feeds miner security after emission tails off (~27.7B of ~28.7B already out).

Limitation: merchants quote euros. Users think in dollars. That is a **display** problem, not a reason to make USDT the state machine.

### 4.2 Parker receipt (use as the unit)

1 locked sompi = 1 claim. Conservation on transfer/split/merge. Redeem to holder P2PK. Sponsor pays fees so you do not skim principal. Identity = genesis outpoint + covenant ID + template + series. **Not a dollar.**

Parker already shipped TN10 evidence (Sprout Harbor, wrap lab). `wTestUSD` cannot buy the town’s crops — that sentence is the whole wrap-honesty lesson.

This desk’s copy is ENGINE_SPEC in PegLab `src/receipt.mjs` and stillpay-*. **Gap:** 1 sompi outputs are unconstructible on TN10 (`Storage mass exceeds maximum`, KIP-9). Teaching unit stays 1:1 in spec. Live floors are larger. Timeout journal in peglab-poc is still the bottleneck.

### 4.3 PegLab tPEG (use as the warning)

Admin oracle + 2 tKAS pool. A 0.2 tKAS swap already moves the pool. Three prices (admin, pool, redeem) disagree. **WILL DEPEG.** That is the product. Mainnet does not add magic. Do not raise money against it. Do not list it.

### 4.4 BitCoffee KUSD (watch, do not ship as money)

The only Kaspa L1 covenant protocol this desk has seen with **accepted TN10 lifecycle transactions** for a dollar-named asset.

What holds:

- Overcollateralized with native KAS (1,000 KAS demo position in their record)
- No Tether-style freeze key in the design
- No live price oracle: liquidation price is a **constructor constant** (0.035 KUSD/KAS in the fixture)
- Six published txs still `is_accepted: true` on 15 Sep 2026
- Their `cargo test --locked --all-targets`: 88 passed (Windows, rustc 1.94.0) — their suite, not an audit

What does **not** hold:

- Peg without a DEX/RFQ is a bet on veto + arbitrage. Unproven.
- 0.035 is a toy parameter. Recalibrate or it is fanfic on mainnet.
- No Kasware/Kastle pay path for the Asset ID → not a till rail
- Unaudited. Frankencoin-inspired. Savings disabled at genesis.
- A fixed Module price can be a **bad** price. PegLab exists so that lesson stays public.

Capital: users lock their own KAS. Treasuries may fund *audits and indexers*, not the peg. A core freeze multisig on KUSD recreates Tether. Do not do that.

This desk reserved a kUSD *chair* in Ishum two weeks earlier. BitCoffee filled a nearby name. **Different objects. Do not weld.**

### 4.5 1kUSD (study)

Serious research: PSM, no CDP, Kaspa-primary ADR, EVM executable reference. Their own README: not production, mock oracle, stub DAO timelock, no external audit, license metadata inconsistent. A Kaspa Toccata port is **not** a Solidity line-by-line translate. Do not scoop it with a 2 tKAS pool and a Discord round.

### 4.6 Licensed fiat stable (company, not this desk)

USDT/USDC/PYUSD hold ~95% of working payment-stable market share because redemption at par under stress is a **banking** product. GENIUS (US) and MiCA (EU) are the floor if you say “dollar.” This desk is not Circle. Host a real issuer when it exists. Do not print a thinner copy.

### 4.7 Failed models (forbidden copies)

| Model | Example | Lesson |
| --- | --- | --- |
| Algorithmic / sister token | Terra UST–LUNA, May 2022. Do Kwon sentenced 2025. | Backing was confidence. Terminal. |
| Thin pool as “peg” | PegLab; farm tokens | Constant-product with shallow depth *is* the depeg. |
| Yield that pays the peg | Anchor ~20% | A run with a date. |
| CEX index as cash | Ethena USDe on Binance, Oct 2025 (~$0.65 print vs DEX near par) | Oracle print ≠ redemption. |
| Chainge-class wrap as native | Kaspa already learned this | Wrapped IOU. Label it. |

---

## 5. Dual rail (the practice)

| Use | Rail | Why |
| --- | --- | --- |
| Dapp unit of account | Native | Freeze = kill switch on the app |
| Miner fee / mass | Native KAS | Security budget must not sit under Tether policy |
| x402 / agents | Native KAS, elldeeone envelope | A future stable needs its own binding |
| Merchant quote | EUR/USD display | People think in fiat. That is a keypad. |
| Merchant inventory | USDT guest, labelled | Liquidity today. Freeze-checked. |
| Classroom | PegLab | So nobody ships a 2 tKAS pool as money |
| Reserved dollar | BitCoffee candidate / empty chair | Not till-ready |

Router is executable in [grok-heavy-showcase](https://github.com/STP-KAS/grok-heavy-showcase) `src/best-practice.mjs`. A pitch that needs PegLab’s UI without the WILL DEPEG banner fails `assertHonestPitch`.

---

## 6. Why this is load-bearing for Kaspa, not a purity contest

Refusing all dollar inventory is how shops stay on Telegram invoices. Hosting only USDT is how a dApp dies on freeze day.

Kaspa’s remaining emission is chromatic, not a cliff. After it, **fees** pay miners. Empty 10 BPS slots are inventory. Filling them with receipts, 402, escrow, and native settlement is how a PoW cash chain survives. Filling them with Tether-as-gas is how it becomes an L2 of Tether Limited.

Bitcoin proved the no-issuer test. Kaspa kept it and added speed and covenants. The PoC alternatives (receipts now; KAS-backed dollars only if they ever hold a peg without a freeze key) are how dApps keep that test while still quoting the unit merchants mean.
