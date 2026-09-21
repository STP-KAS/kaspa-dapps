# Plan of action

For this desk. Do in order. If a kill-if in [BREAK.md](BREAK.md) fires, stop.

Not Kaspa core. Not a dollar raise. **Not a product.**

Someone posts a Kaspa GitHub link and says it shipped. Open the link. A proposal is not a release. A node release is not wallet support. Do not use wallet integrations on this GitHub. STP remains a clown.

---

## Track split

| Track | What | Not |
| --- | --- | --- |
| **0 — public goods** | This map, kns-spec, honest pins, freeze lab | A token. A product. |
| **1 — BTCPay-shaped software** | Ishum till, anyone hosts, desk keeps 0 | Circle. Fill is not a business. |
| **out of path** | DAGKnight, vProgs, Argent ICC, a fourth 402, tPEG-as-money, a desk-issued dollar, wallet inject | Tagged + Active + audits where a release is claimed. |

---

## Now (this pin)

### 0. Stay on the pin (every clone, every day)

- SilverScript **v1.0.0** (`3ed9733`). Not `master`. Not v1-rc1.
- rusty-kaspa **v2.0.1**.
- Testnet **TN10** only for experiments that spend.
- Referee: [kaspaexplained.com/status](https://kaspaexplained.com/status).
- Law: merged **Active** KIP.
- **No wallet inject** from this desk.

**Done when:** every STP-KAS `.sil` header names v1.0.0, and no public repo ships in-page inject.

### 1. Pick the layer before you write Solidity-on-Kaspa by accident

| Building | Layer | First repo |
| --- | --- | --- |
| Payments, escrow, receipts, 402 | L1 covenants | peglab-poc + ishum + elldeeone/kaspa-x402 |
| Existing Solidity DeFi | L2 (Kasplex/Igra) | Their docs. Size bridge risk. Do not call it L1 PoW security. |
| Dashboard / bot | Read-only REST or own node | api.kaspa.org / rusty-kaspa |

**Done when:** README names the layer, the freeze/bridge assumption, and that this is **not a product** until stables + sequencing are settled.

### 2. Money: dual rail, no exceptions

- Quote EUR/USD on the keypad (Ishum).
- Settle native KAS / Parker receipt whenever the promise must survive.
- Offer USDT as a **labelled guest**. Freeze-check.
- Never USDT as gas, dapp unit, or x402 asset.
- Keep PegLab in the docs so nobody ships a 2 tKAS pool as USD.

**Done when:** `assertHonestPitch` in grok-heavy-showcase would pass on the public copy.

### 3. One covenant that cannot lie about money

Own-UTXO only.

- `validateOutputState` on **our** continuation.
- `require(tx.outputs[i].value == expected)` every time. Amount is **not** locked by the state check.
- Never `readInputState` a foreign UTXO.
- Never `(State[] a, State[] b) = xs.split(n)` until silverscript#250 merges. `.0` / `.1` is allowed.
- Do not invent `compute_budget`. Measure by TN10 rejection.

**Done when:** a TN10 txid spends and recreates the UTXO with the value invariant.

### 4. Fill the receipt journal (Parker unit)

peglab-poc / stillpay-tn10:

- Unit = sompi, not USD.
- Timeout / pay / reclaim txids on **TN10**.
- Live floor > 1 sompi (KIP-9 storage mass). Say so.

**Done when:** README lists txids for create, pay, timeout, refuse-fake-dollar.

### 5. Charge for the call (402)

- Bind **elldeeone/kaspa-x402** `v1.0.0-rc.1`. TN10. Mainnet blocked.
- No fourth envelope.
- First billed surface: local URL → 402 → pay KAS on TN10 → 200 + txid.
- Pay path: QR / `kaspa:` URI / paste txid. **No inject.**

**Done when:** `curl` proves it. No USDC. No Solana. No in-page wallet kit.

### 6. One till, hosted by someone else

Ishum:

- PC hosts. Desk holds **0** keys.
- Pay: QR / `kaspa:` URI / paste txid. **No in-page inject from this desk.**
- BitCoffee KUSD seat stays a **candidate** until audit + peg that holds + a pay path that is not this desk’s inject kit.

**Done when:** a second machine, not this one, takes a TN10 payment without this desk in the loop.

### 7. Names locate, chain settles

kns-spec:

- One name. Publish keys that exist.
- `kns://` opens a page that **never asks for a seed** and **does not inject a wallet**.
- Uniqueness is still indexer FCFS. Say so.

**Done when:** a stranger resolves, runs locally, pays with QR or URI, gets a receipt.

### 8. BitCoffee: review, don’t absorb

- Keep [kusdt-bitcoffee](https://github.com/STP-KAS/kusdt-bitcoffee) as the independent pass.
- Do not put KUSD in kaspa-x402 as `asset` without a new binding.
- Recalibration, indexer, DEX/RFQ, counsel: their L1-EXECUTE list. None of that is this desk issuing a dollar.

**Done when:** the till can *display* the candidate without claiming 1:1 USD.

### 9. Housekeeping

- This repo is the front door. kaspa-master-file is the encyclopedia. Desk prompt: `DESK-PROMPT.md`.
- wallet-integration stays public as a **tombstone**. Do not restore inject.
- Profile README (`STP-KAS/STP-KAS`) points here.

**Done when:** a new contributor lands on kaspa-dapps, reads NOT-A-PRODUCT.md, and cannot clone a wallet kit from this account.

---

## Next (only after the done-checks above)

- Mainnet Ishum, still gated broadcast, still no tPEG, still no inject.
- If KCC-20 becomes more than Draft: *other people* can list assets. We still do not list GRAM.
- If Argent tags **and** README drops “not release-ready” **and** the two unimplemented compiler rules compile: *other people* compose actors.
- If BitCoffee (or 1kUSD-on-Toccata) ever has an independent audit and a peg that holds under a sell: *then* revisit the kUSD chair as a third rail. Not before.
- Production dapps stay **out of path** until the L1 stable *and* the sequencing product are both settled.

---

## Monday tripwire

1. silverc latest SemVer tag
2. rusty-kaspa latest node tag
3. kaspaexplained.com/status vs this freeze
4. silverscript#250, #243, kccs#4 / #14 / #20 / #25
5. Argent tags or not
6. BitCoffee txids still accepted
7. api.kaspa.org DAA / reward / supply
8. Any kill-if in BREAK.md
9. Confirm wallet-integration still throws (no inject restored)
10. Any GitHub claim of “shipped” still classified as proposal / branch / release / activation
