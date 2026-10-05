# Hyperliquid builder codes — whose users stay

**What this is.** For each builder code: how many of its wallets come back the next month, how long they stay, how
much of their trading goes through that code and how much elsewhere, and whether the code brought them to the venue in
the first place. The public tables show what a code earns. These cuts are not on them.

**Population.** Taker prints of $500 and up on the main perp exchange, 2025-07-28 to 2026-08-30. Smaller prints are
not counted, so an app whose users trade small looks smaller here than it is. The product is rebuilt on every fill.

| # | Builder code | Fee, bps | Wallets | Share of its users' volume it carries | Wallets using it almost only | First trade came through it | Back next month | Median days active | Active 3 months or more | Volume, first half to second half |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | `0xb84168cf…f80b` | 5.0 | 83,942 | 86% | 97% | 99% | 43% | 7 | 23% | -49% |
| 2 | `0xe95a5e31…53aa` | 10.0 | 22,545 | 32% | 77% | 95% | 37% | 2 | 16% | -22% |
| 3 | `0x1924b856…80e5` | 2.5 | 20,632 | 42% | 64% | 95% | 48% | 12 | 27% | -91% |
| 4 | `0x2868fc0d…8a39` | 1.0 | 2,401 | 43% | 40% | 94% | 59% | 18 | 34% | -64% |
| 5 | `0xcf56dd84…fc1a` | 5.0 | 5,336 | 94% | 98% | 99% | 29% | 1 | 11% | -91% |
| 6 | `0x1cc34f6a…da1f` | 1.0 | 14,457 | 98% | 97% | 100% | 44% | 8 | 26% | -67% |
| 7 | `0x557edb25…3c81` | 3.5 | 40,587 | 100% | 100% | 100% | 37% | 4 | 5% | new in the second half |
| 8 | `0xf944069b…7009` | 5.5 | 837 | 100% | 97% | 99% | 65% | 48 | 48% | -71% |
| 9 | `0xad9be64f…f045` | 2.0 | 11,345 | 12% | 26% | 89% | 43% | 4 | 20% | +381% |
| 10 | `0x49509948…9395` | 4.5 | 5,563 | 36% | 77% | 91% | 43% | 6 | 23% | -27% |

**One figure across all codes.** On 20 sampled days, a taker routed through a builder paid a median 7.8 bps in fees all-in; a taker not routed through one paid 2.4 (same population).

**Definitions.** *Share of its users' volume it carries:* of everything this code's wallets traded, the part routed
through this code. *Almost only:* 95% or more of the wallet's volume through this code. *First trade came through it:*
the wallet's first print in the population carried this code. *Back next month:* month-over-month retention of active
wallets. *First half to second half:* routed notional before and after 2026-02-12, the middle of the span.

**Limits.** Ten largest codes by routed fees in this population; any code can be run. Codes are shown by address.
Main exchange only; no HIP-3 markets.

**Price.** $1,500 one-off, or $300 a month updated.

**Contact.** Nate Givon — nategivon@hotmail.com
