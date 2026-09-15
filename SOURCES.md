# Sources

Sampled **15 Sep 2026** unless a row says otherwise. Recheck live endpoints before quoting as current.

## This pass (what Grok actually ran)

| Check | Result |
| --- | --- |
| `STP-KAS` GitHub | 42 public repos (39 original + 3 forks). `github__search_repositories user:STP-KAS fork:true` |
| grok-heavy-showcase `npm test` + `npm run lab` | **10 pass, 0 fail.** Native redeem after freeze. Guest blocked. NEVER_GAS. Depeg 319 bps. |
| `api.kaspa.org/info/blockdag` | DAA **540,389,037**, network `kaspa-mainnet`. Bare urllib **403**; browser User-Agent **200**. |
| `info/coinsupply` | 2,770,137,183,833,713,622 sompi → **27,701,371,838.337** KAS |
| `info/blockreward` | **2.18267645** |
| `api-tn10.kaspa.org/info/blockdag` | DAA **571,008,588**, `kaspa-testnet-10` |
| TN10 tx `a7a04250…28e7` (Ishum till) | `is_accepted: true`, mass 2049 |
| BitCoffee txs `2d571d6b…`, `472af946…`, `680c6408…` | all `is_accepted: true` |
| groks-wallet balance | `116314625488733` sompi = **1,163,146.25488733** tKAS |

## Kaspa protocol / status

- [kaspaexplained.com/status](https://kaspaexplained.com/status) — live vs roadmap vs wrong. Sources checked 14 Sep 2026; L1 snapshot 14 Sep 09:14:52 UTC (older than this pass’s API pull).
- [kaspaexplained.com/build-on-kaspa](https://kaspaexplained.com/build-on-kaspa) — covenant counts.
- [hellokaspa.com/ecosystem](https://hellokaspa.com/ecosystem) — L1 / L2 / indexer. Honest maturity. Bridge warning.
- [kaspanet/rusty-kaspa](https://github.com/kaspanet/rusty-kaspa) v2.0.0 / [v2.0.1](https://github.com/kaspanet/rusty-kaspa/releases/tag/v2.0.1)
- Toccata KIPs Active: [16](https://github.com/kaspanet/kips/blob/master/kip-0016.md), [17](https://github.com/kaspanet/kips/blob/master/kip-0017.md), [20](https://github.com/kaspanet/kips/blob/master/kip-0020.md), [21](https://github.com/kaspanet/kips/blob/master/kip-0021.md). Activation DAA **474,165,565** (~30 Jun 2026).
- Crescendo: KIP-14, 10 BPS, 5 May 2025.
- SilverScript [v1.0.0](https://github.com/kaspanet/silverscript/releases/tag/v1.0.0) `3ed9733` (9 Sep 2026).
- DAGKnight: [KIP-2](https://github.com/kaspanet/kips/blob/master/kip-0002.md) Proposed. [dagknight branch](https://github.com/kaspanet/rusty-kaspa/tree/dagknight).
- [kaspanet/kccs](https://github.com/kaspanet/kccs) — KCC-20 Draft. KCC ≠ KIP.
- [docs.kaspa.org/toccata](https://docs.kaspa.org/toccata)
- [api.kaspa.org](https://api.kaspa.org/docs)
- CoinEx, 17 Jul 2026: [Kasplex / Igra activity snapshot](https://www.coinex.com/en/insight/report/can-kas-survive-another-crypto-cycle-the-signals-that-matter-now-6a59d8102f8f1bbf5c08b91d) — Kasplex −97.8% weekly active from peak. Dated; recheck.

## Bitcoin / Satoshi

- Nakamoto, 2008: [bitcoin.org/bitcoin.pdf](https://bitcoin.org/bitcoin.pdf) — “without going through a financial institution”; trusted third party loses the main benefits.

## Tether freeze record

- [Bitquery, The Tether Freeze Regime](https://bitquery.io/investigations/tether-blacklist-audit) — 13 Aug 2026 write-up, on-chain pull to **12 Aug 2026**, ETH+Tron. Primary numbers in [RAILS.md](RAILS.md).
- [eaglevirtual USDT blacklist](https://eaglevirtual.com/usdt-blacklist) — wider-chain tracker (14 Sep 2026 sample in grok-heavy-showcase).
- [BlockSec, USDT blacklist 2026](https://blocksec.com/blog/usdt-blacklist-explained-2026)
- [EMM Legal, challenge a freeze](https://www.emmlegal.com/news/recover-frozen-usdt-a-guide-to-tether-wallet-freezes/) — 2025 unfreeze rate cited 3.6%.
- USDT contracts: `addBlackList`, `destroyBlackFunds` (Ethereum + Tron). Holder has no override.

## Tether / stables on Kaspa

- Kasplex, 3 Mar 2026: [x.com/kasplex/status/2028901724279464187](https://x.com/kasplex/status/2028901724279464187) — stablecoin bridge, Circle/Tether standards, BEP-20 first.
- [Kaspa Daily](https://x.com/DailyKaspa/status/2028924498053878134)

## PoC / dollar research

- [parker2017code/kaspa-explained](https://github.com/parker2017code/kaspa-explained) — receipts, Sprout Harbor, wrap lab. `wTestUSD` cannot buy crops.
- [bitcoffee0/kusd](https://github.com/bitcoffee0/kusd) `tn10` — KUSD covenants. Unaudited. Testnet only.
- [Kas-Smiths #143](https://kas-smiths.org/t/kusd-a-decentralized-oracle-free-kas-backed-stablecoin-on-l1/143) — BitCoffee0, 13 Sep 2026.
- [Frankencoin](https://github.com/Frankencoin-ZCHF/Frankencoin) — inspiration, not a port.
- [NeaBouli/1kUSD](https://github.com/NeaBouli/1kUSD) — PSM research. Not production.
- [elldeeone/kaspa-x402](https://github.com/elldeeone/kaspa-x402) `v1.0.0-rc.1`
- [Kali123411/k402](https://github.com/Kali123411/k402) — HTTP 402 + channel lock. [kccs#4](https://github.com/kaspanet/kccs/pull/4) open.

## This desk (prior)

- [STP-KAS/kaspa-master-file](https://github.com/STP-KAS/kaspa-master-file) — pin encyclopedia (the mess this repo replaces as a front door).
- [STP-KAS/peglab-stp](https://github.com/STP-KAS/peglab-stp) — DOCTRINE, STABLES-GUIDE, WILL DEPEG.
- [STP-KAS/ishum](https://github.com/STP-KAS/ishum)
- [STP-KAS/grok-heavy-showcase](https://github.com/STP-KAS/grok-heavy-showcase)
- [STP-KAS/kusdt-bitcoffee](https://github.com/STP-KAS/kusdt-bitcoffee)
- [STP-KAS/tn10-hard-test](https://github.com/STP-KAS/tn10-hard-test)

## Failed / cautionary pegs (context, not Kaspa-native)

- Terra UST–LUNA, May 2022; Do Kwon sentenced 2025.
- USDC/SVB, March 2023, ~$0.88 for days; DAI gapped with the PSM cap.
- Ethena USDe Binance print ~$0.65 vs DEX near par, Oct 2025.

GENIUS (US) and MiCA (EU) are the regulatory floor if a project says payment stable. A receipt is not a payment stable. Do not mix the sentences. Not legal advice.
