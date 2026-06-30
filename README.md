# rlSTONE Rescue Tool

A free, open-source tool to recover stranded **rlSTONE** ("RNP LayerBank STONE")
from Manta Pacific after the Renew Paradigm campaign frontend was discontinued.

> **TL;DR** — if you supplied STONE to LayerBank → wrapped to rlSTONE under
> Renew Paradigm on Manta, the frontend at `renewparadigm.manta.network` is
> dead. But the smart contracts still work. This tool calls them directly so
> you can unstake yourself, in your own wallet, without trusting a custodian.

## Live tool

- **DIY (free, full withdrawal):** https://xuanthanghp1992-hash.github.io/rlstone-rescue/
- **Guided service (partial withdrawal, paid):** https://xuanthanghp1992-hash.github.io/rlstone-rescue/partial.html

## How it works

The recovery is three on-chain steps. All calls are made from **your own
wallet** — the tool never holds funds and never asks for private keys.

| # | Action | Contract | Method |
|---|--------|----------|--------|
| 1 | Approve rlSTONE → StakeRouter | `0x2d391C26b02B97C7cDc3B08B50eDC69fAC92820b` (rlSTONE) | `approve(spender, amount)` |
| 2 | Unstake rlSTONE → lSTONE | `0x5AD8f91CBb19eaF3dFe520b17F632c6F44B9C0AF` (StakeRouter) | `unstakeERC20(lSTONE, amount)` |
| 3 | Redeem lSTONE → STONE | `0xB7A23Fc0b066051dE58B922dC1a08f33DF748bbf` (LayerBank Core) | `redeemToken(lToken, lAmount)` |

After step 3 you hold native **STONE** on Manta. You can:
- Bridge to Ethereum via Stargate / Manta New Paradigm Bridge
- Swap to ETH on izumi.finance / Quickswap V3

Gas: roughly **$0.001 per transaction** on Manta Pacific.

## Safety

- ❌ The tool **NEVER asks for your private key or seed phrase**.
- ✅ Every transaction is signed in your own wallet (Rabby / MetaMask / OKX).
- ✅ All target addresses and function selectors are visible in the HTML source.
- ✅ The StakeRouter has >50 successful `unstakeERC20` transactions from
  independent users (e.g. reference tx
  [`0x0cf8104d...c769c2`](https://pacific-explorer.manta.network/tx/0x0cf8104d909d3d39ed46d8173e28e32a921b5e6aaed1c765426a78eeefc769c2)).
- ✅ Tool is **MIT licensed** — clone it, host it on your own machine, or
  audit the 300 lines of JavaScript before using.

## Guided service (optional, paid)

Most users can use the free DIY tool. If you prefer 1-on-1 guidance through
Telegram (we walk you through each transaction, verify success, and handle
edge cases), there is an optional paid service:

- **Fee:** 7–15% of recovered amount, scaled by size (whales pay lower %)
- **Payment:** AFTER you receive your STONE — never upfront
- **Process:** Split 60/40 — recover 60% first, pay fee, then recover the remaining 40%
- **Contact:** Telegram **@stone_help**

The fee structure exists because guiding each user 1-on-1 takes time. The
DIY tool is and always will be free.

## Running locally

This is a single static HTML file. To use it:

```bash
git clone https://github.com/xuanthanghp1992-hash/rlstone-rescue.git
cd rlstone-rescue
python -m http.server 8765
```

Open `http://127.0.0.1:8765/` in a browser with Rabby / MetaMask / OKX
installed and configured for Manta Pacific (chain ID 169).

## Why this happened

`renewparadigm.manta.network` (the official Renew Paradigm UI) is no longer
served. Users were left holding `rlSTONE` receipts without a clear way to
withdraw. The rlSTONE contract itself is paused for direct user calls, but
the linked **StakeRouter** still accepts `unstakeERC20()` from token holders,
so the recovery path exists.

## Author

Built by a fellow Renew Paradigm survivor after successfully rescuing my own
position (~$152 of stranded STONE). If this helped you and you'd like to
support continued work on recovery tools for other dead-frontend protocols,
tips are appreciated but **not required**:

- Tip wallet: `0x3033a685a400763de76256147bc2a020589755c8` (Manta Pacific)

## License

MIT — see [LICENSE](LICENSE). Fork freely, just keep the safety notes.
