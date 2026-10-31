# CleanUp Crew Matcher

**AWS CendekiAwan 2026 IIUM Generative AI Challenge · GovTech & Social Impact · built in AWS PartyRock**

After a flood, an NGO coordinator has damaged houses, a list of volunteers and their own safety rules. CleanUp Crew Matcher turns **house photos + house notes + a volunteer roster + the NGO's crew rules** into job cards, safety hand-offs, a rule-checked crew plan and ready-to-send briefings. A coordinator approves every crew.

- **App:** https://partyrock.aws/u/imanzafri/8_6Tgd6bg/Cleanup-Crew-Matcher
- **Demo video (3 min):** [`video/CleanUp-Crew-Matcher-demo.mp4`](video/CleanUp-Crew-Matcher-demo.mp4)
- **Screenshots:** [`screenshots/`](screenshots/)

## What's in this repo

```
video/          3-minute demo video (submission)
screenshots/    5 app screenshots (submission)
data/
  photos/       B1–B4 (main demo), H1–H3 (gas/appliance test)
  rosters/      volunteer_roster_A.csv, volunteer_roster_B.csv (made-up test data)
  house-notes/  text to paste into the House Notes box
  crew-rules/   text to paste into the Crew Rules box (Sunday / Saturday)
tests/          step-by-step test checklists + results log
docs/           system analysis, video plan + script, Stage 2 research
```

## How the app works

| Widget | Type | What it does |
|---|---|---|
| House Photos | input | 1–4 photos, one per house |
| House Notes | input | one line per house: place, distance, residents, work needed |
| Volunteer Roster | input | CSV / PDF / Word list of volunteers |
| Crew Rules | input | the NGO's own rules, in plain words |
| Job Cards | AI | per house: what the photo shows, tasks, tools, crew size, priority |
| Safety Hand-Offs | AI | hazards, why they matter, who to hand off to |
| Crew Plan | AI | checks every volunteer against every rule, builds crews, lists gaps |
| Crew Briefing Card | AI image | illustration for the briefing |
| Crew Briefings | AI | short message per crew, ready to copy and send |
| Coordinator Assistant | AI chat | what-if questions ("Jason can come at 10am?") |

## Try it in 2 minutes

1. Open the app link and click **Remix** (or use it directly).
2. Upload `data/photos/B1.jpg` to `B4.jpg` into **House Photos**.
3. Paste `data/house-notes/house-notes_B1-B4.txt` into **House Notes**.
4. Upload `data/rosters/volunteer_roster_B.csv` into **Volunteer Roster**.
5. Paste `data/crew-rules/crew-rules_Sunday-15-Nov_roster-B.txt` into **Crew Rules**.
6. Press **Play**, then check the output against [`tests/T1-roster-B-sunday.md`](tests/T1-roster-B-sunday.md).

More tests (second roster, gas cylinders, chat questions) are in [`tests/`](tests/README.md).

## Known limitations

- The AI can build different crews on different runs with the same inputs. Always check against the rules.
- It did not flag the possible duplicate volunteer (W04 Nadia / W10 Nadia R.).
- It says it can't read photo file names; it matches photos to houses by what's in them.
- The generated briefing image can show a child, which conflicts with the 18+ rule.
- It can't judge structural or electrical safety from a photo. A team leader checks on site.

## Stage 2 (roadmap, not built)

A web app on AWS: **Amplify** (coordinator site + Cognito sign-in), **S3** (photo and roster uploads), **Bedrock** (job cards, matching, chat), **DynamoDB** (rosters, rules, approved crews). Research and sources: [`docs/stage2/stage2-research-notes.md`](docs/stage2/stage2-research-notes.md).

## Data and privacy

All volunteer names in the rosters are made-up test data. Use real photos only with residents' consent, and with no faces, number plates or house numbers.
