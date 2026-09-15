# Breaking points

Things that already break, or that must stop the line if someone ships past them. Freeze: **15 Sep 2026**.

---

## Already broken / proven

| Break | Evidence | Consequence |
| --- | --- | --- |
| **1 sompi receipt is unconstructible** | TN10 reject: `Storage mass exceeds maximum` (KIP-9). Hard-test catalog. | Teaching unit stays 1:1 in ENGINE_SPEC. Live outputs need a larger floor. Do not demo “1 sompi on-chain” as if it landed. |
| **PegLab depegs on a tiny trade** | grok-heavy-showcase `runDepegLab`: three prices disagree, depeg **319 bps** after a 0.2 tKAS-class swap. Tests 15 Sep 2026. | tPEG is the classroom. Mainnet does not add depth. |
| **USDT freeze blocks the guest; native still redeems** | grok-heavy-showcase freeze lab, 10/10 tests. | Dual rail is not a slogan. Host USDT labelled. Never as gas. |
| **Tether destroy is real, not theoretical** | Bitquery, ETH+Tron to 12 Aug 2026: $1.43B destroyed, $5.85B at freeze. | If the dApp unit is USDT, the dApp has a kill switch. |
| **Kasplex did not retain users** | CoinEx, week to 12 Jul 2026: 169 weekly active, **−97.8%** from 7,613 peak. | “Solidity on Kaspa” shipped. Product-market fit did not. Size L2 as young. |
| **Foreign `readInputState` is a hole** | silverscript#234 closed **unmerged**. | Own-UTXO `validateOutputState` only. |
| **`State[].split()` tuples broken on v1.0.0** | #249; fix #250 still **open** at last master-file freeze. | Use `.0` / `.1`. Skip tuple syntax. |
| **Amount is not locked by `validateOutputState`** | Compiler pin. Parker and PegLab both encode `require(value)`. | Forgetting this is how an escrow leaks. |
| **Hardcoded miner fees in example escrows** | Toccata-era examples. | Fee market moves. Sponsor input, or you brick the continuation. |
| **TN10 explorer / faucet flaky** | explorer-tn10.kaspa.org **402 DEPLOYMENT_DISABLED**; faucet-tn10 **403** (14 Sep hard-test). | Use api-tn10 + kaspa.stream. Do not block a demo on the official explorer UI. |
| **api.kaspa.org 403 without a browser UA** | This pass, Python urllib default. | Scripts need a User-Agent. The API is public; the WAF is not documented as a pin. |
| **1 sompi / dust vs ~97k–330k UTXOs** | groks-wallet was ~97k UTXOs then ~330k then **1.16M tKAS / balance 116314625488733 sompi** this pass. | Wallet paging is a product problem (kaspa.news 11 Sep). Do not assume MetaMask-like UX. |
| **KCC-20 is Draft** | kaspanet/kccs. PR #25 proposes Final; not accepted. | Not a ratified token standard. Not a gram token. |
| **KCC-0021 / KCC-0402 not adopted** | Unmerged PRs. Bodies claim production use, unconfirmed. | Do not cite as law. |
| **DAGKnight is not consensus** | KIP-2 Proposed. `dagknight` branch unmerged. Mainnet GHOSTDAG. | Do not ship DK as live. |
| **Argent not release-ready** | No tag as of 14 Sep status page. README says audit/hardening still required. Two compiler rules unimplemented. | Demos ≠ production. |
| **vProgs not product** | kaspanet/vprogs: early development, no release, private TN10 fork example. | Roadmap. |
| **BitCoffee peg unproven** | Design is oracle-free via a **fixed** module price. No DEX. No wallet Asset ID pay path. | Candidate. Not shops. |
| **1kUSD not production** | Their README: mock oracle, stub governance, no audit, no mainnet. | Study. |
| **Chainge-class wrap already taught Kaspa a depeg** | PegLab STABLES-GUIDE / doctrine. | Wrapped IOU. Label it. |

---

## Kill-if (stop the line)

If any of these appear in a STP-KAS README, till, or pitch, revert.

1. **USDT as gas, as dapp unit, or as the x402 asset.**
2. **tPEG listed as money**, or a raise against the 2 tKAS pool.
3. **“Kaspa has no freeze because we bridged USDT.”** Bridging imports the key.
4. **A core / desk freeze multisig on a Kaspa dollar.** That recreates Tether.
5. **Foreign `readInputState` in our scripts.**
6. **silverc `master` (or v1-rc1) replacing v1.0.0 in a release.**
7. **Fourth 402 envelope**, or calling k402 “x402 v2” / “adopted KCC-0402.”
8. **GRAM as a KCC-20.** Grams are mass + WorkCredit, not a ticker.
9. **Seed-paste UX.**
10. **TN12 as evidence of mainnet covenants.** Toccata activated on mainnet at DAA 474,165,565.
11. **Shipping Argent / vProgs / DAGKnight / 100 BPS as live.**
12. **Compiler tag sold as an audit of the dApp.**
13. **Welding Ishum’s empty kUSD chair onto BitCoffee** as if they were one asset.
14. **In-page inject of unknown wallets.** Kasware / Kastle only.

---

## L2 / bridge (size these; don’t pretend)

- L2 inherits L1 security **only** through the bridge and proof. hellokaspa states this clearly. Believe it.
- Bridges are the industry’s largest loss category. Kasplex and Igra have months of history, not years.
- Igra’s “no single sequencer” claim, if true, trades tooling for a different liveness/censorship surface. Verify, don’t slogan.
- KRC-20 (indexer overlay) is **not** consensus. Native assets exist because the indexer was the weak point. Migration risk is load-bearing.

---

## BitCoffee-specific (if you try to execute)

From [kusdt-bitcoffee L1-EXECUTE](https://github.com/STP-KAS/kusdt-bitcoffee/blob/main/L1-EXECUTE.md):

1. Independent covenant + replay + **reorg** audit. Public RPC cannot fake forks; a hostile indexer can lie.
2. Recalibrate every number in their ECONOMICS.md. 0.035 is a fixture.
3. Write down the oracle decision: competitive Modules, or a fail-closed oracle later. “Oracle-free” is a bet, not a miracle.
4. Partial challenges or an ADR that they will not exist.
5. Third-party indexer that survives reorgs.
6. Wallet pay/sign for the Asset ID.
7. DEX/RFQ so 1 KUSD has an arbitrage loop against KAS.
8. kaspa-x402 stays native KAS until a new binding exists.
9. Counsel before mainnet issuance. Saying “dollar” pulls GENIUS/MiCA into the room.

Did **not** open a new BitCoffee Position from groks-wallet this pass. That needs their builder, the live Module outpoint, and a key in `.env`. Published auctions already used distinct owner / challenger / bidder keys.

---

## Wallet / node (this machine)

- groks-wallet cannot log in to KaChat (inject only).
- KasWare is a desktop extension. It does not exist on a phone. KaChat is the phone. Do not mix the demo paths.
- Local `127.0.0.1` URLs on GitHub are **this PC**, not a hosted dApp. Keep saying it.
- Mainnet kaspad listen `0.0.0.0:16111` was documented on this box. Do not paste keys or seeds into git. PegLab sponsor seed is gitignored on purpose.

---

## What would change the map

| Event | Then |
| --- | --- |
| Independent audit + wallet Asset ID + peg holds under a sell for BitCoffee or 1kUSD-on-Toccata | Revisit a third rail. Still not USDT-as-gas. |
| Tether contract without blacklist (will not happen) | Guest rail gets safer. Native still required for fees. |
| silverscript#250 merge + #243 budget specified | Relax the tuple / budget kill-ifs. Recheck. |
| KCC-20 Final | Other people list tokens. We still do not list GRAM. |
| Argent tag + README drop + unimplemented rules compile | Other people compose. Till still one UTXO. |
| DAGKnight Active + rusty tag | Consensus pin changes. Product path does not wait for it. |
