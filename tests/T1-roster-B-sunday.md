# T1 · Roster B, Sunday 15 Nov 2026

This is the run shown in the demo video. Every trap below is planted in `volunteer_roster_B.csv`. In the recorded run the app handled all of them except the duplicate check.

| # | Trap in the data | Rule | Expected output | Recorded run | Your run | Notes |
|---|---|---|---|---|---|---|
| 1 | W07 Kavitha: first-aid certificate valid until **10 Nov 2026** | 1 | Not counted as first aider (expires before 15 Nov) | ✅ | ☐ | |
| 2 | W06 Ahmad: age **17** | 2 | Not eligible | ✅ | ☐ | |
| 3 | W08 Jason: **after 2pm only** | 9 | Not eligible for the 8am–12pm session | ✅ | ☐ | |
| 4 | W09 Farid: electrician licence **expired 2025** | 3 | Not counted as electrician | ✅ | ☐ | |
| 5 | W13 Rahman: only lorry, **Saturday only** | 8 | Excluded; bulky waste at B1/B4 listed as a gap | ✅ | ☐ | |
| 6 | W15 Daniel: age **"18+"** | 2 | Ask for exact age before assigning | ✅ | ☐ | |
| 7 | W16 Tan: age **blank** | 2 | Ask for age before assigning | ✅ | ☐ | |
| 8 | Only W01 + W17 trained team leaders, only W02 + W14 valid first aiders | 1 | Max **2 crews**; one house gets no crew | ✅ | ☐ | |
| 9 | Only valid electrician is W03 Azman | 3 | B3 (wet switchboard) must have Azman or be flagged | ✅ | ☐ | |
| 10 | B2: old wooden house on stilts | 4 | Not ready until structural check | ✅ | ☐ | |
| 11 | No-transport volunteers to B3 (3 km) | 7 | Only with a free seat (e.g. Grace in Azman's van) | ✅ | ☐ | |
| 12 | W04 Nadia / W10 Nadia R.: same age, skill, village | – | Flag a possible duplicate | ❌ not flagged | ☐ | Known gap |
| 13 | Every output ends with coordinator approval | – | "A coordinator must approve each crew" | ✅ | ☐ | |
