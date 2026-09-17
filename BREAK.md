# Breaking points

Things that already break, or that must stop the line if someone ships past them. Freeze: **17 Sep 2026**.

Why the new kill-ifs exist: [KASPAglobal](https://x.com/kaspaglobal/status/2100536064683176270). A GitHub link is not a product. A node release is not wallet support. This desk does not ship wallet integrations.

---

## Already broken / proven

| Break | Evidence | Consequence |
| --- | --- | --- |
| **1 sompi receipt is unconstructible** | TN10 reject: `Storage mass exceeds maximum` (KIP-9). | Teaching unit stays 1:1 in ENGINE_SPEC. Live outputs need a larger floor. |
| **PegLab depegs on a tiny trade** | grok-heavy-showcase `runDepegLab`: depeg **319 bps** after a 0.2 tKAS-class swap. | tPEG is the classroom. Mainnet does not add depth. |
| **USDT freeze blocks the guest; native still redeems** | grok-heavy-showcase freeze lab, 10/10 tests. | Dual rail is not a slogan. Never as gas. |
| **Tether destroy is real, not theoretical** | Bitquery, ETH+Tron to 12 Aug 2026: $1.43B destroyed, $5.85B at freeze. | If the dApp unit is USDT, the dApp has a kill switch. |
| **Kasplex did not retain users** | CoinEx, week to 12 Jul 2026: 169 weekly active, **−97.8%** from 7,613 peak. | “Solidity on Kaspa” shipped. Product-market fit did not. |
| **Foreign `readInputState` is a hole** | silverscript#234 closed **unmerged**. | Own-UTXO `validateOutputState` only. |
| **`State[].split()` tuples broken on v1.0.0** | #249; fix #250 still **open** at last freeze. | Use `.0` / `.1`. Skip tuple syntax. |
| **Amount is not locked by `validateOutputState`** | Compiler pin. | Forgetting this is how an escrow leaks. |
| **Hardcoded miner fees in example escrows** | Toccata-era examples. | Sponsor input, or you brick the continuation. |
| **TN10 explorer / faucet flaky** | explorer-tn10 **402 DEPLOYMENT_DISABLED**; faucet-tn10 **403**. | Use api-tn10 + kaspa.stream. |
| **api.kaspa.org 403 without a browser UA** | Python urllib default. | Scripts need a User-Agent. |
| **KCC-20 is Draft** | kaspanet/kccs. PR #25 proposes Final; not accepted. | Not a ratified token standard. |
| **DAGKnight is not consensus** | KIP-2 Proposed. Mainnet GHOSTDAG. | Do not ship DK as live. |
| **Argent not release-ready** | No tag. README: audit/hardening still required. | Demos ≠ production. |
| **vProgs not product** | kaspanet/vprogs: early development, no release. | Roadmap. |
| **BitCoffee peg unproven** | Fixed module price. No DEX. | Candidate. Not shops. |
| **1kUSD not production** | Mock oracle, stub governance, no audit, no mainnet. | Study. |
| **No spendable L1 stable** | iziodev pass, 17 Sep 2026. Native L1 USD issuer: none tracked. | Production dapps are not a useful spend. |
| **App sequencing unsettled as a product** | KIP-21 Active as *commitments*. vProgs unreleased. | A primitive is not a sequencer product. |

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
14. **Shipping in-page wallet inject.** Kit withdrawn 17 Sep 2026. Restore is a revert.
15. **Calling a proposal, branch, compiler, or node release a product.**
16. **Staffing production L1 dapps** while the L1 stable and the sequencing path are both unsettled.

---

## L2 / bridge (size these; don’t pretend)

- L2 inherits L1 security **only** through the bridge and proof.
- Bridges are the industry’s largest loss category.
- KRC-20 (indexer overlay) is **not** consensus.

---

## BitCoffee-specific (if you try to execute)

From [kusdt-bitcoffee L1-EXECUTE](https://github.com/STP-KAS/kusdt-bitcoffee/blob/main/L1-EXECUTE.md):

1. Independent covenant + replay + **reorg** audit.
2. Recalibrate every number in their ECONOMICS.md. 0.035 is a fixture.
3. Write down the oracle decision.
4. Third-party indexer that survives reorgs.
5. DEX/RFQ so 1 KUSD has an arbitrage loop against KAS.
6. kaspa-x402 stays native KAS until a new binding exists.
7. Counsel before mainnet issuance.
8. **No inject kit** from this desk as the “wallet pay path.”

---

## Wallet / node (this machine)

- This desk **does not ship wallet integrations.** [wallet-integration](https://github.com/STP-KAS/wallet-integration) is a tombstone.
- Local `127.0.0.1` URLs on GitHub are **this PC**, not a hosted dApp.
- Do not paste keys or seeds into git.

---

## What would change the map

| Event | Then |
| --- | --- |
| Independent audit + peg holds under a sell for BitCoffee or 1kUSD-on-Toccata | Revisit a third rail. Still not USDT-as-gas. Still not a product by itself. |
| vProgs release + public testnet that is not a private fork | Sequencing path becomes *checkable*. Not automatically a product. |
| silverscript#250 merge + #243 budget specified | Relax the tuple / budget kill-ifs. Recheck. |
| KCC-20 Final | Other people list tokens. We still do not list GRAM. |
| Argent tag + README drop + unimplemented rules compile | Other people compose. Till still one UTXO. |
| DAGKnight Active + rusty tag | Consensus pin changes. Product path does not wait for it. |
