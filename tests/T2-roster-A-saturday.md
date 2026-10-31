# T2 · Roster A, Saturday 14 Nov 2026

**This test has not been run yet.** The "Expected output" column is what the rules require, worked out by hand from `volunteer_roster_A.csv`, not something the app has produced. Use this run to show the app gives consistent results with a different NGO's list.

| # | Trap in the data | Rule | Expected output | Your run | Notes |
|---|---|---|---|---|---|
| 1 | V08 Nurul: first-aid certificate **expired 2023** | 1 | Not counted as first aider | ☐ | |
| 2 | V11 Wei Jie: age **17** | 2 | Not eligible | ☐ | |
| 3 | V07 Hafiz: electrical TVET **student, not qualified** | 3 | Not counted as electrician | ☐ | |
| 4 | V03 Ravi: "listed as qualified by NGO", no licence stated | 3 | Should ask for licence proof, or not count him | ☐ | Borderline on purpose |
| 5 | V14 Amir: availability **not stated** | 2/9 | Ask before assigning | ☐ | |
| 6 | V06 Farah: team leader, **Sunday only** | 9 | Not available Saturday | ☐ | |
| 7 | Saturday team leaders = V01 Aiman + V15 Lim only | 1 | Max 2 crews | ☐ | |
| 8 | Valid first aiders = V02 Mei Ling + V16 Hana only | 1 | Max 2 crews | ☐ | |
| 9 | V09 Kumar: own 1-tonne lorry, Saturday | 8 | Lorry available this time (unlike Roster B) | ☐ | |
| 10 | No `free_seats` column | 7 | Should not invent seat numbers; ask the driver | ☐ | |
| 11 | B2 old wooden house on stilts | 4 | Not ready until structural check | ☐ | |
| 12 | B3 wet switchboard, no current licensed electrician | 3 | B3 flagged: needs an electrician | ☐ | |
