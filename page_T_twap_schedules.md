# Hyperliquid native TWAPs, reconstructed — schedules, slices, overlap, participation

**What this is.** Every native TWAP order on Hyperliquid's main perp exchange since 2 August 2025, rebuilt from the
public fill archive: one row per schedule and one row per slice. A schedule carries its wallet, coin, side, start and
end, slice count, clock and sizes, whether the same wallet ran another schedule in the same coin and direction at the
same time, and its share of all taker volume in the coin while it ran.

**Coverage.** 905,909 schedules and 97,485,780 slices from 20,122 wallets, 2025-08-02 to 2026-09-30.
35% of schedules overlap another from the same wallet; 97% of those with four slices or more run on the
30-second clock; the median slice is $39.

| Month | Schedules | Wallets | Notional, $M |
|---|---|---|---|
| 2025-08 | 92,579 | 3,839 | 23,567 |
| 2025-09 | 91,869 | 6,326 | 11,669 |
| 2025-10 | 87,762 | 3,981 | 11,790 |
| 2025-11 | 76,675 | 4,043 | 7,026 |
| 2025-12 | 50,554 | 2,348 | 4,028 |
| 2026-01 | 51,946 | 2,283 | 4,735 |
| 2026-02 | 53,875 | 1,941 | 4,028 |
| 2026-03 | 45,848 | 1,883 | 4,043 |
| 2026-04 | 45,859 | 2,098 | 3,997 |
| 2026-05 | 62,920 | 2,915 | 5,590 |
| 2026-06 | 68,074 | 2,736 | 5,190 |
| 2026-07 | 44,779 | 2,037 | 4,580 |
| 2026-08 | 59,583 | 2,823 | 8,546 |
| 2026-09 | 73,586 | 3,121 | 6,765 |

**Shape** (schedules of four slices or more):

| Length | Schedules | Share | Median size | Median slices | Overlapping | Median participation | Participation 5% or more |
|---|---|---|---|---|---|---|---|
| under 10 min | 330,365 | 41% | $3,854 | 11 | 41% | 0.66% | 29% |
| 10 to 60 min | 335,845 | 42% | $8,158 | 59 | 30% | 0.51% | 26% |
| an hour or more | 142,191 | 18% | $18k | 301 | 28% | 0.08% | 12% |

**Participation by depth of book** (schedules of four slices or more):

| Book | Schedules | Median | 90th percentile |
|---|---|---|---|
| Deep (BTC, ETH and the like) | 390,638 | 0.05% | 2.6% |
| Middle | 154,802 | 0.80% | 18.9% |
| Thin | 256,599 | 5.5% | 57.0% |
| Not in the tier map | 6,362 | 3.1% | 76.9% |

**Five schedules** from the last 60 days:

|  | Start (UTC) | Coin | Side | Length | Slices | Size | Median slice | Overlap | Participation | Wallet | twap_id |
|---|---|---|---|---|---|---|---|---|---|---|---|
| largest | 2026-08-08 10:54 | ETH | buy | 36h 00m | 4,321 | $48.0M | $11k | no | 15.0% | 0xde8d…9524 | 2091685 |
| typical BTC | 2026-08-07 09:56 | BTC | sell | 5h 30m | 660 | $10k | $15 | no | under 0.01% | 0xf9f0…4176 | 2089707 |
| longest off the majors | 2026-08-02 22:15 | LIT | buy | 167h 59m | 6,511 | $82k | $12 | yes | 0.09% | 0xd93d…ae3f | 2077532 |
| largest overlapping | 2026-09-10 12:53 | ETH | sell | 15 min | 31 | $19.8M | $638k | yes | 16.1% | 0xea66…61ee | 2203669 |
| thin book, high participation | 2026-09-20 22:31 | AERO | sell | 30 min | 61 | $208k | $3,413 | no | 48.0% | 0xb1e3…b750 | 2235606 |

**Columns.** Schedule: wallet · coin · side · twap_id · start and end (ms) · slices · fills · size and notional ·
median and largest slice · clock statistics · price walk inside slices · makers and top maker's share · overlap flag ·
participation. Slice: wallet · coin · side · twap_id · sequence · time (ms) · fills · size · notional · average, low and
high price · makers.

**Read this before buying.** I ran pre-registered tests on the archive of trading around these schedules: providing
liquidity to slices, riding a schedule's drift, fading its completion, and riding stacked schedules. None met its bar after costs.
This is data for measuring execution and flow, not a signal I can vouch for. No price outcome is included.

**Limits.** Perps on the main exchange only. Order ids exist from 2 August 2025; earlier TWAPs are not included.
Participation is measured on whole minutes. A schedule running across midnight UTC on 30–31 August 2026 can appear in
two parts until the order build.

**Price.** $3,000 one-off, or $500 a month updated.

**Contact.** Nate Givon — nategivon@hotmail.com
