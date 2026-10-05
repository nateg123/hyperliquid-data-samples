# Hyperliquid liquidation legs — displacement, 60-second marks, maker count

**What this is.** Every liquidation on Hyperliquid's main perp exchange, one row per leg: one account, one coin, one
liquidation event. Each row says how far the leg printed from the last trade before it, where price stood from 10
seconds to 30 minutes later, and how many makers filled it. Built from the public fill archive; every row is keyed by
its public transaction hash and first trade id.

**What it shows.** Window 2026-08-31 to 2026-09-30 (31 days). Calm days, single-coin liquidations. "Net" is what a maker
already resting at the leg's average price kept at 60 seconds, after 6.0 bps of fees and a per-coin slippage
allowance.

| Distance from the last trade | Legs | Share | Median leg | Gross at 60 s, bps | Net at 60 s, bps |
|---|---|---|---|---|---|
| under 2 bps | 70,375 | 47% | $300 | +0.7 | -7.3 |
| 2 to 10 | 51,275 | 34% | $281 | +4.4 | -4.3 |
| 10 to 30 | 20,496 | 14% | $211 | +20.0 | +9.2 |
| 30 to 100 | 7,606 | 5% | $178 | +76.2 | +62.9 |
| 100 and over | 1,340 | 1% | $95 | +285.6 | +267.5 |

81% of these legs print within 10 bps of the last trade, and they lose money for the maker. The return sits in the legs that print further away.

**The tested set.** Single-coin legs 30 bps or more away, plus legs of multi-coin liquidations 100 bps or more away:
**9,036 legs in 1,342 transactions on 141 coins, net +91.17 bps (gross +105.05), t = 5.87.** The test and its
bar were registered before any price in the window was read. 86% of these legs were filled by one maker each. Gross by
horizon: +71 at 10 s, +105 at 60 s, +128 at 30 min.

**Read this before buying.** Three things. The figure belongs to a maker whose order was already resting when the
liquidation printed; an archive test of a newcomer's ladder of resting orders made money at no size tried. The legs
are small: the median leg in the tested set is $166, and at the test's cap of $1,500 a leg the set carried about
$54.4M of notional a year — worth about $496,000 a year to a maker who took every leg. The legs' full notional is
about $856M a year; the test capped each leg at $1,500 and says nothing about the part above the cap. And one month
of forward data stands behind the tested row. Main exchange only; no HIP-3 markets.

**Columns.** Transaction hash · first trade id · coin · time (UTC, ms) · forced side · notional · fills · makers · top maker's share ·
reference price and its age · displacement in bps · price change to the maker at 10, 30, 60, 120, 300 and 1,800
seconds · single- or multi-coin event · storm-day flag. No account address is included.

**Ten rows** from the tested set, one per transaction, taken in hash order, not by outcome. They illustrate the
rows; they are not the distribution:

| Time (UTC) | Coin | Forced side | Size | From last trade, bps | Makers | 60 s, bps | Transaction hash | First trade id |
|---|---|---|---|---|---|---|---|---|
| 2026-09-09 19:01:06 | USELESS | sell | $9 | +59.9 | 1 | +55.7 | `0x5b4442e9a818ce655cbd04440bad6c0202e500cf431bed37ff0cee3c671ca84f` | 491359350296021 |
| 2026-09-20 07:05:00 | CASHCAT | sell | $10 | +83.5 | 1 | +57.7 | `0xc3075e2b8d33204dc4810444ccd2740203df001128363f1f66d0097e4c36fa38` | 673940819447100 |
| 2026-08-31 14:11:29 | PONS | buy | $38 | +43.0 | 1 | +331.1 | `0x39f76b17a0a772e93b71044361fef202043800fd3baa91bbddc0166a5fab4cd3` | 476282514432001 |
| 2026-09-07 16:30:27 | PONS | sell | $52k | +39.0 | 40 | +221.6 | `0x9401be68c59472e2957b0443e4f197020266004e609791b437ca69bb84984ccd` | 5069379107199 |
| 2026-09-15 18:46:32 | FARTCOIN | sell | $15 | +32.3 | 1 | +55.8 | `0x5069273bbb0ef4ad51e204447983f902096b00215602137ff431d28e7a02ce97` | 827760500177572 |
| 2026-09-22 23:21:09 | FARTCOIN | buy | $22 | +42.9 | 1 | +24.2 | `0xba47f68df581e7a5bbc10444fe33ac0203940073908506775e10a1e0b485c190` | 700446633301317 |
| 2026-09-19 08:11:32 | AR | buy | $109 | +39.9 | 1 | +66.7 | `0x581edab02a7306ee59980444bb40d0010700f295c57625c0fbe78602e976e0d8` | 617629445844622 |
| 2026-09-05 19:17:43 | SUSHI | buy | $14 | +32.7 | 1 | +83.8 | `0x0b9f848b3cd2a9310d190443c221490000da9c70d7d5c803af682fddfbd6831b` | 27916578268974 |
| 2026-09-09 20:31:13 | PUMP | sell | $33k | +110.9 | 1 | +104.4 | `0xa3f48ab6029bab63a56e04440cd7d1020214009b9d9eca3547bd3608c19f854e` | 541156550002663 |
| 2026-09-23 14:11:15 | SUI | sell | $125 | +36.8 | 1 | +67.4 | `0x4c480501ff28838d4dc10445098d6a0108001ce79a2ba25ff010b054be2c5d77` | 216090537868014 |

**Check a row yourself.** Take the hash and the trade id. In the public fill archive, the liquidation fills with that hash and coin can
belong to several accounts; the account whose first fill carries that trade id is the leg. Its size-weighted price
against the last taker print before the transaction is the displacement.

**On disk today.** For 2026-08-31 to 2026-09-30: 169,361 legs, 169,314 with marks. For 2025-07-28 to 2026-08-30: 1,849,727 legs with displacement and maker count, 573,022 of them with marks. The full history with marks is
built on order.

**Price.** $5,000, one-off.

**Contact.** Nate Givon — nategivon@hotmail.com
