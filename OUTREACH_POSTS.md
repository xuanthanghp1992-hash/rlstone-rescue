# Outreach drafts — rlSTONE Rescue

Use these for Reddit / StakeStone TG / Manta Discord / Twitter. Adjust tone per
platform. **Never DM victims about money first** — drop the free tool, let them
come to you.

---

## 1) Reddit comment — r/Metamask (existing thread)

> URL: https://www.reddit.com/r/Metamask/comments/1boqjxg/how_to_convert_stone_back_to_eth_manta/

If you supplied STONE to LayerBank under the **Renew Paradigm** wrap (so you got
"rlSTONE" / "RNP LayerBank STONE" tokens), the Renew Paradigm frontend is now
dead — but the contracts still work. I just recovered mine.

I put together a free open-source tool that walks you through the 3 steps:
**approve → unstake (rlSTONE→lSTONE) → withdraw via LayerBank**. No seed phrase,
no key, everything is signed in your own wallet. Source is on GitHub.

[Link to tool] · [Link to GitHub] · Tx proof from my own wallet: `<tx hash>`

There are still ~134 wallets holding rlSTONE (about $66k worth at current STONE
price). Happy to help anyone get unstuck — DM if you hit any snag.

---

## 2) Reddit post — r/ReNewParadigmManta (new post)

**Title:** "How I rescued my rlSTONE after the Renew Paradigm UI went down (free tool)"

**Body:**

I was sitting on a rlSTONE position from the original campaign with no UI to
withdraw it. The Renew Paradigm frontend (`renewparadigm.manta.network`) is
down. After some reverse-engineering on the proxy contract, I found that:

- The rlSTONE contract is paused for direct user calls
- But the linked **StakeRouter** at `0x5AD8f91CBb19eaF3dFe520b17F632c6F44B9C0AF`
  still accepts `unstakeERC20(lSTONE, amount)` from any holder
- 50+ users have successfully used this path in the last weeks
  (e.g. tx `0x0cf8104d909d3d39ed46d8173e28e32a921b5e6aaed1c765426a78eeefc769c2`)

So I wrote a static HTML page that builds the calldata for you. Steps:

1. Connect Rabby / MetaMask / OKX on Manta Pacific
2. Approve rlSTONE → StakeRouter (one tx)
3. Unstake → you'll have lSTONE
4. Withdraw lSTONE → STONE on the still-live LayerBank UI

Total gas: ~$0.003. Final result: native STONE in your wallet, which you can
swap to ETH on izumi.finance / Quickswap V3 and bridge out.

Tool: [link]
Source code: [link]

Happy to answer questions or help debug if anything goes wrong.

---

## 3) StakeStone Telegram — t.me/stakestoneofficialhq

Short message, focused on people asking for support:

> If anyone here is stuck with **rlSTONE** ("RNP LayerBank STONE") from the
> Renew Paradigm campaign — the frontend is dead but the contracts still work.
> I put together a free tool that walks through the on-chain steps to unstake
> and withdraw. Open source, no seed/key needed. [link]
>
> Helped me recover mine — sharing in case it helps others too. Happy to DM
> if you get stuck.

---

## 4) Twitter post

> Renew Paradigm on @MantaNetwork is offline but ~$66k of rlSTONE is still
> sitting in user wallets with no UI to withdraw.
>
> I wrote a tiny open-source tool to call the contracts directly.
>
> Free. Open source. No seed phrase. You sign every tx yourself.
>
> 🔗 [link]
> 🐙 GitHub: [link]
>
> If this helped, RT so other holders find it.

---

## 5) Direct outreach to a whale (last resort, after testimonials exist)

**Only after** there are 2-3 public testimonials / Reddit comments confirming
the tool works. Then for top 2 whales:

Channel options (in order of "least creepy"):
1. Their Twitter via ENS lookup (e.g. `0x1083.eth` may be claimed on Twitter)
2. ENS text records (some ENS names have `email`/`com.twitter`/`com.discord`)
3. On-chain message (zero-value tx with calldata containing a short note)

**Template:**

> Hi — I noticed you're holding [X] rlSTONE on Manta from the Renew Paradigm
> campaign. The frontend is down but I built a tool that lets you unstake it
> directly. Free, open source, signed in your own wallet, no key needed.
>
> Multiple users have already recovered with it (Reddit testimonials: [link]).
>
> If you'd like help running it, happy to walk you through. I'd ask for 10-15%
> of the recovered amount as a tip — only payable **after** you see STONE in
> your wallet. Zero up-front, zero risk to you.
>
> Tool: [link] · Source: [link] · My tx proof: [link]
>
> If you'd rather do it yourself, the tool is free either way.

Key rules:
- Never ask for seed/key
- Never receive funds before they do
- Always reference public testimonials
- Always include "free either way"

---

## Posting order

1. Day 1: launch GitHub repo + GitHub Pages
2. Day 1-2: post on r/Metamask, r/ReNewParadigmManta
3. Day 2-3: post on StakeStone TG, Manta Discord
4. Day 3-7: Twitter post + collect 2-3 testimonials
5. Day 7+: direct whale outreach (only after testimonials)
