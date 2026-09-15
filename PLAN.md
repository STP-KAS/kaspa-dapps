# Plan of action

For Kaspa dApp developers, and for this desk. Do in order. Skip a step only if its **done check** is already green. If a kill-if in [BREAK.md](BREAK.md) fires, stop.

Not Kaspa core. Not a dollar raise.

---

## Track split

| Track | What | Not |
| --- | --- | --- |
| **0 — public goods** | This map, kns-spec, honest pins, freeze lab | A token |
| **1 — BTCPay-shaped software** | Ishum till, anyone hosts, desk keeps 0 | Circle. Fill is not a business |
| **out of path** | DAGKnight, vProgs, Argent ICC, a fourth 402, tPEG-as-money, a desk-issued dollar | Until tagged + Active + audits |

---

## Now (this pin)

### 0. Stay on the pin (every clone, every day)

- SilverScript **v1.0.0** (`3ed9733`). Not `master`. Not v1-rc1.
- rusty-kaspa **v2.0.1**.
- Testnet **TN10** only for experiments that spend.
- Referee: [kaspaexplained.com/status](https://kaspaexplained.com/status) and [build-on-kaspa](https://kaspaexplained.com/build-on-kaspa).
- Law: merged **Active** KIP.

**Done when:** every STP-KAS `.sil` header names v1.0.0.

### 1. Pick the layer before you write Solidity-on-Kaspa by accident

| Building | Layer | First repo |
| --- | --- | --- |
| Payments, escrow, receipts, 402 | L1 covenants | peglab-poc + ishum + elldeeone/kaspa-x402 |
| Existing Solidity DeFi | L2 (Kasplex/Igra) | Their docs. Size bridge risk. Do not call it L1 PoW security. |
| Dashboard / bot | Read-only REST or own node | api.kaspa.org / rusty-kaspa |

**Done when:** README of the dApp names the layer and the freeze/bridge assumption.

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

**Done when:** a TN10 txid spends and recreates the UTXO with the value invariant. Explorer link in peglab-poc.

### 4. Fill the receipt journal (Parker unit)

peglab-poc / stillpay-tn10:

- Unit = sompi, not USD.
- Timeout / pay / reclaim txids on **TN10**. Empty journal = ENGINE_SPEC fanfic.
- Live floor > 1 sompi (KIP-9 storage mass). Say so.

**Done when:** README lists txids for create, pay, timeout, refuse-fake-dollar.

### 5. Charge for the call (402)

- Bind **elldeeone/kaspa-x402** `v1.0.0-rc.1`. TN10. Mainnet blocked.
- Steal lock/voucher *shape* from Kali123411/k402. Credit them. Do not call it adopted KCC-0402 (kccs#4 still open).
- No fourth envelope.
- First billed surface: local URL → 402 → pay KAS on TN10 → 200 + txid.

**Done when:** `curl` proves it. No USDC. No Solana.

### 6. One till, hosted by someone else

Ishum:

- PC hosts. Desk holds **0** keys.
- Any Kaspa wallet: QR / `kaspa:` URI / paste txid.
- Inject = Kasware or Kastle only.
- BitCoffee KUSD seat stays a **candidate** until wallet pay path + audit + recalibrated economics exist.

**Done when:** a second machine, not this one, takes a TN10 payment without this desk in the loop.

### 7. Names locate, chain settles

kns-spec:

- One name. Publish keys that exist.
- `kns://` opens a page that **never asks for a seed**.
- Uniqueness is still indexer FCFS. Say so.

**Done when:** a stranger with Kasware/Kastle resolves, runs locally, pays, gets a receipt.

### 8. BitCoffee: review, don’t absorb

- Keep [kusdt-bitcoffee](https://github.com/STP-KAS/kusdt-bitcoffee) as the independent pass.
- Do not open a Position from groks-wallet until their Python builder + live Module outpoint + a TN10 key in `.env` are a deliberate test, not a merge.
- Do not put KUSD in kaspa-x402 as `asset` without a new binding.
- Recalibration, indexer, wallet Asset ID, DEX/RFQ, counsel: their [L1-EXECUTE](https://github.com/STP-KAS/kusdt-bitcoffee/blob/main/L1-EXECUTE.md) list. None of that is this desk issuing a dollar.

**Done when:** the till can *display* the candidate without claiming 1:1 USD.

### 9. Housekeeping (the mess)

- This repo is the front door. kaspa-master-file is the encyclopedia.
- Do not open repo 43 for “what this pass did.”
- Optional: GitHub-archive the archive table in [REPOS.md](REPOS.md) once txids are copied here or into kusdt-bitcoffee.
- Profile README (`STP-KAS/STP-KAS`) points here.

**Done when:** a new contributor lands on kaspa-dapps in under one click from the profile.

---

## Next (only after the done-checks above)

- Mainnet Ishum, still gated broadcast, still no tPEG.
- If KCC-20 becomes more than Draft: *other people* can list assets. We still do not list GRAM.
- If Argent tags **and** README drops “not release-ready” **and** the two unimplemented compiler rules compile: *other people* compose actors. A till still does not need ICC.
- If BitCoffee (or 1kUSD-on-Toccata) ever has an independent audit, a wallet path, and a peg that holds under a sell: *then* revisit the kUSD chair as a third rail. Not before.

---

## Monday tripwire

Recheck, or the map rots (it already did once: v1-rc1 after v1.0.0):

1. silverc latest SemVer tag
2. rusty-kaspa latest node tag
3. kaspaexplained.com/status vs this freeze
4. silverscript#250, #243, kccs#4 / #14 / #20 / #25
5. Argent tags or not
6. BitCoffee txids still accepted
7. api.kaspa.org DAA / reward / supply
8. Any kill-if in BREAK.md

If the job cannot see a Moved URL or a new compiler tag, it must not leave a stale pin in the table.
