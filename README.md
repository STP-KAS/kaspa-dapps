> **Experimental only. Not a product.** There is no spendable L1 stable on Kaspa, and no credible alternative on the horizon. Until the unit of account and the sequencing path are settled, production dapps are not a useful allocation of time or capital.
>
> Do not use wallet integrations on this GitHub. STP remains a clown. [DISCLAIMER.md](DISCLAIMER.md)

# Kaspa dApps

**One map.** What a Kaspa dApp developer should use, skip, and not lie about.

Not Kaspa core. Not a dollar. Not a token sale. **Not a product.** Desk: [STP-KAS](https://github.com/STP-KAS) / [@StppStp](https://x.com/StppStp). Current pins: [kaspa-master-file Now](https://github.com/STP-KAS/kaspa-master-file#now-read-this-first) (21 Sep 2026). Lines below are dated receipts.

**21 Sep (eve):** KCC-0’s file is **Final** (`c0bb8f3`). The kccs README index still says Draft. That is not KCC-20 Final. DAGKnight still unmerged. No Argent tag. SilverScript still `3ed9733`. vprogs master still `f9b84a8`. LLM forum execution is halted. Encyclopedia is the master file, not this door.

**20 Sep:** rusty-kaspa master → `eb0a856` (#1136 IBD chunks + #1137 RejectCoinbase merged). DK still unmerged. Encyclopedia: [kaspa-master-file](https://github.com/STP-KAS/kaspa-master-file).

**20 Sep (eve):** kccs#24 head → `7159d48`; #27 approved (still Draft). Pins hold. Encyclopedia: [kaspa-master-file ec73dea](https://github.com/STP-KAS/kaspa-master-file/commit/ec73dea).

This replaces hunting the previous **42** overlapping GitHubs. The encyclopedia stays at [kaspa-master-file](https://github.com/STP-KAS/kaspa-master-file). **This is the front door.**

**18 Sep 2026:** encyclopedia catch-up on DAGKnight / Argent / SilverScript / KCC ([commit abd66dc](https://github.com/STP-KAS/kaspa-master-file/commit/abd66dc)). **Pins hold** — no DK merge, no Argent tag, SilverScript tip still `3ed9733`, no KCC Final.

**Read this first:** [NOT-A-PRODUCT.md](NOT-A-PRODUCT.md).

There is no spendable L1 stable, and no credible alternative on the horizon. KIP-21 is a consensus primitive, not a settled app-sequencing product. Until those two are settled, building real working dapps on Kaspa is not a useful spend of time or capital. Wallet integrations were withdrawn from this desk so a clone cannot be used as a wallet kit.

| File | What |
| --- | --- |
| [NOT-A-PRODUCT.md](NOT-A-PRODUCT.md) | The filter. Compiler ≠ product. No L1 stable. Sequencing unsettled. |
| [RAILS.md](RAILS.md) | Native KAS vs Tether vs PoC dollars vs Bitcoin / Satoshi |
| [REPOS.md](REPOS.md) | STP-KAS repos: keep, one-of, archive, withdrawn |
| [PLAN.md](PLAN.md) | What to do, in order |
| [BREAK.md](BREAK.md) | Things that already break, or will |
| [SOURCES.md](SOURCES.md) | Dated sources. Recheck before quoting |

---

## 1. If you are building a Kaspa dApp

Pick a layer. They are not interchangeable. **Do not call this a product path.**

| Route | When | Honest limit |
| --- | --- | --- |
| **L1 covenants** | Receipts, escrow, vaults, native assets, anything that must survive an issuer | Toccata is live. Tooling is months old. Failure modes are not catalogued. SilverScript **v1.0.0** is a compiler tag, not an audit of your app. |
| **L2 EVM** (Kasplex / Igra) | You already have Solidity and want to ship | Security is the **bridge + sequencer**, not Kaspa PoW. Kasplex weekly active accounts fell **97.8%** from peak by July 2026. Young infrastructure. |
| **Read-only** | Balances, bots, dashboards | Public REST or your own node. No contracts. |

Do **not** wait for DAGKnight, vProgs, Argent, or a Kaspa dollar. Those are research or untagged. Mainnet today is GHOSTDAG, 10 BPS, Toccata spend rules.

Do **not** spend a product team on “real working dapps” while the L1 dollar is missing and app sequencing is unsettled. Honest work: receipts, a till that quotes fiat and settles native KAS, freeze labs. That is not DeFi.

Referee: [kaspaexplained.com/status](https://kaspaexplained.com/status) (checked 14 Sep 2026; L1 snapshot below rechecked **15 Sep 2026**).

---

## 2. The money question (this is why the map exists)

Satoshi’s claim, 2008: *payments sent directly from one party to another without going through a financial institution.* Bitcoin has held the no-issuer-blacklist test since 3 Jan 2009. Kaspa kept the same security model on native KAS: proof of work, UTXO, fair launch, no premine, no company key.

**USDT is a company with two contract functions no holder can override:**

- `addBlackList` — the address can no longer send
- `destroyBlackFunds` — a frozen balance can be deleted

Bitquery (ETH + Tron, cutoff **12 Aug 2026**): **11,085** freeze events, **11,045** addresses, **$5.85B** held at the freeze block, **$1.43B** permanently destroyed, **100%** of OFAC-designated addresses frozen. Median Ethereum unfreeze wait: **386 days**. Released addresses were almost never labelled criminal. That is a financial institution with a kill switch.

Bridging USDT onto Kaspa (Kasplex-class, announced 3 Mar 2026) does **not** remove that key. Kaspa sequences the guest. Tether remains the issuer. If the dApp unit can be frozen, **the dApp can be frozen.** If USDT is gas, a freeze stops the till and starves miners.

Circle/USDC has the same class of risk (smaller blacklist, SVB 2023 depeg to ~$0.88 for days — survived because cash existed). The class is **issuer money**.

Full argument: [RAILS.md](RAILS.md).

---

## 3. PoC alternatives — why they matter, what they are not

A Kaspa dApp that only speaks Tether has outsourced its survival. Alternatives exist. None of them is “a dollar you can list tomorrow.”

| Object | What it actually is | Status 17 Sep 2026 | Use it as |
| --- | --- | --- | --- |
| **Native KAS** | PoW cash. No freeze function. | Live mainnet | Dapp unit, miner fee, x402, anything that must survive |
| **Parker receipt** | 1 unit = 1 locked sompi. Sponsor pays fees. Name ≠ authenticity. | TN10 evidence in [kaspa-explained](https://github.com/parker2017code/kaspa-explained). 1 sompi outputs fail KIP-9 storage mass; live floors are larger. | The unit. Not USD. |
| **PegLab tPEG** | Admin oracle + 2 tKAS pool | Designed to depeg. SCRIPT_ENFORCED genesis is the *toy*. | Classroom. **Never money.** |
| **BitCoffee KUSD** | KAS-overcollateral, oracle-free (module price is a constructor constant), Frankencoin-inspired covenants on TN10 | Six published lifecycle txs **still accepted**. Peg **unproven**. 0.035 KUSD/KAS is a fixture. | The only L1 covenant dollar *candidate* this desk has verified on-chain. **Not** ready for shops. Independent review: [kusdt-bitcoffee](https://github.com/STP-KAS/kusdt-bitcoffee). Upstream: [bitcoffee0/kusd](https://github.com/bitcoffee0/kusd). |
| **1kUSD** | Collateralized PSM research. EVM reference; Kaspa-primary ADR. | Mock oracle, stub governance, no external audit, no mainnet. Their README says so. | Study. Do not race it with a thinner copy. [NeaBouli/1kUSD](https://github.com/NeaBouli/1kUSD) |
| **USDT/USDC guest** | Bridged issuer IOU | Useful liquidity. Freeze switch intact. | Labelled guest. Never gas. Never dapp unit. |
| **Ishum kUSD chair** | A till *seat* this desk reserved | Empty. BitCoffee filled a nearby name with a protocol. Do not weld them. | Quote EUR. Settle KAS. |

**Dual rail is the only honest merchant path today:** keypad in EUR/USD, settlement in native KAS (or a future PoC that actually holds), USDT offered as a labelled guest.

Executable lesson (10/10 tests, 15 Sep 2026): [grok-heavy-showcase](https://github.com/STP-KAS/grok-heavy-showcase). Native redeem still works after the issuer freeze. Guest transfer fails. `useAsGas()` throws `NEVER_GAS`. PegLab’s three prices disagree after a 0.2 tKAS trade.

---

## 4. Best of this desk (why these, not the other 30)

Picked because a stranger can *do something* or *learn a law*. Everything else is a pass log, a fork, or a duplicate. **Wallet-integration is withdrawn** — not in this table.

| Repo | Job | Why it survived this cut |
| --- | --- | --- |
| **This repo** | Front door | One map. |
| [grok-heavy-showcase](https://github.com/STP-KAS/grok-heavy-showcase) | Freeze lab + dual-rail router | Tests the constitution. Pages: [stp-kas.github.io/grok-heavy-showcase](https://stp-kas.github.io/grok-heavy-showcase/) |
| [peglab-stp](https://github.com/STP-KAS/peglab-stp) | WILL DEPEG classroom | The warning. Capital ladder in STABLES-GUIDE. |
| [peglab-poc](https://github.com/STP-KAS/peglab-poc) | Parker unit + PegLab honesty | Receipt spec. Timeout journal still a gap. |
| [ishum](https://github.com/STP-KAS/ishum) | Self-hosted till | Quote fiat, settle KAS, desk holds 0 keys. Live TN10 payment `a7a04250…28e7` still accepted. |
| [kusdt-bitcoffee](https://github.com/STP-KAS/kusdt-bitcoffee) | Independent BitCoffee review | On-chain txids, not a vibe. Not an audit. |
| [sixpack.wtf](https://github.com/STP-KAS/sixpack.wtf) | x402 verdict | Bind [elldeeone/kaspa-x402](https://github.com/elldeeone/kaspa-x402) `v1.0.0-rc.1`. TN10 only. Public: [sixpack.wtf](https://sixpack.wtf) |
| [kns-spec](https://github.com/STP-KAS/kns-spec) | KNS implementer kit | Proven mainnet txs. Overlay is not official KNS. |
| [kaspa-master-file](https://github.com/STP-KAS/kaspa-master-file) | Pin encyclopedia | Compiler tag, KIPs, forum. Desk prompt lives here. Too long to be a front door. |

Full cut: [REPOS.md](REPOS.md).

---

## 5. Constitution (desk law, short)

1. Dapp unit, miner fee, and x402 stay **native KAS**.
2. USDT is a **guest**. Label the freeze. Never gas.
3. tPEG is a **classroom**. WILL DEPEG. No raise against it.
4. This desk **does not issue a dollar**. Review of BitCoffee is allowed. Absorbing it is not.
5. One till: **Ishum**. Do not grow a fourth.
6. One 402 envelope: **elldeeone/kaspa-x402**. HTTP 402 ≠ x402.
7. Compiler pin: SilverScript **v1.0.0** (`3ed9733`). Node: rusty-kaspa **v2.0.1**. Testnet: **TN10**.
8. **No wallet integrations.** Inject kit withdrawn 17 Sep 2026. QR / `kaspa:` URI / paste txid only. Never ask for a seed.
9. Merged Active KIP is law. A tweet, a Draft KCC, and an open PR are not.
10. Cite Parker as **GitHub only**. Do not clone kaspaexplained.com.
11. **Not a product.** Production dapps wait on a spendable L1 stable *and* a settled sequencing path. Unclear stable sequencing is research.

---

## 6. Live this pass (15 Sep 2026 numbers; stance 17 Sep 2026)

Probed with a normal User-Agent (bare Python urllib gets **403** from api.kaspa.org).

| What | Value | Source |
| --- | --- | --- |
| Mainnet DAA | **540,389,037** | `api.kaspa.org/info/blockdag` |
| Circulating | **27,701,371,838.337** KAS | `info/coinsupply` (sompi / 1e8) |
| Block reward | **2.18267645** KAS | `info/blockreward` |
| TN10 DAA | **571,008,588** | `api-tn10.kaspa.org/info/blockdag` |
| Ishum till tx | accepted, mass 2049 | `a7a042501c32cfede58d8672b12a86deaaa2f538606d82002d2e286e689028e7` |
| BitCoffee module / savings / repay | accepted | txids in [kusdt-bitcoffee](https://github.com/STP-KAS/kusdt-bitcoffee) |
| Dual-rail tests | **10 pass, 0 fail** | `grok-heavy-showcase` `npm test` |

Consensus is still **GHOSTDAG**. DAGKnight is KIP-2 Proposed. Toccata is live. Native DeFi is **roadmap**, not a product layer.

---

## 7. Plan and breakpoints

Do this, in order: [PLAN.md](PLAN.md).

Stop the line if any of these fire: [BREAK.md](BREAK.md). Short list:

- Calling a compiler, KCC, or node release a **product**
- Spending a product team on L1 dapps while the dollar and sequencing path are unsettled
- USDT as gas or as the dapp unit
- tPEG listed as money
- 1 sompi sold as a constructible mainnet output (KIP-9 storage mass rejects it)
- Foreign `readInputState` (`silverscript#234` closed unmerged)
- Fourth 402 envelope, or calling k402 “adopted KCC-0402”
- Shipping Argent / vProgs / DAGKnight as live
- A core freeze multisig on a “Kaspa dollar” (that recreates Tether)
- Shipping in-page wallet inject from this desk

---

## 8. Think bigger (same pins)

The 10-year product is not a wrapped dollar and not an L2 clone of Ethereum.

It is **programmable proof-of-work cash that keeps a promise**: escrow that released, a 402 that charged, a receipt that matched locked sompi, a till someone else can host. After the last ~1B KAS is emitted, miners eat **fees**. Dapps whose unit is native KAS feed that. Dapps whose unit is Tether feed Tether, and die on freeze day.

That product does not exist yet. A missing L1 stable plus unsettled app sequencing is research. Year 1 on this pin: one WorkCredit UTXO, receipts with live TN10 txids, one 402 endpoint that actually charges, Ishum hosted on a second machine, USDT labelled at the till. Covenant counts may stay small. Locked KAS in *our* UTXOs should be inventory, not TVL cosplay.

Bitcoin proved electronic cash without a trusted third party. Kaspa made that cash fast and (as of Toccata) programmable. Putting Tether back in as the only language the app speaks un-does the point. Pretending the app layer is a product before the dollar and the sequencing path exist un-does the point the other way.

---

MIT. No warranty. Recheck live endpoints before quoting numbers as current.

---

> **Standard disclaimer.** This GitHub, not the topic above.
>
> Intentions are good; thought process is questionable. STP remains delusional. Si vis pacem, para bellum.
>
> Intern at https://sixpack.wtf/  
> X: https://x.com/StppStp · GitHub: https://github.com/STP-KAS
