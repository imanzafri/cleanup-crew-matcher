# CleanUp Crew Matcher: system analysis

Sources: `01_assets/screen-recording/partyrock-flow.mov` (studied through the proxy `proxy-1920-30fps.mp4`, 8:12.8 long), the 7 photos in `01_assets/photos/Disaster Image/`, and both CSVs in `01_assets/data/`.
Timestamps are from the recording, read off contact sheets sampled every 5 s, so treat them as **±5 s**.
Anything marked *(guess)* is not shown directly in the files.

---

## 1. The problem and the users

**Problem.** After a flood, an NGO has several damaged houses and a list of volunteers. It has to decide who goes where, while keeping its own safety rules: a trained team leader and a first aider with a valid certificate in every crew, no minors, only licensed electricians touching wiring, no crew sent into a house that may be structurally unsafe, transport for people without a vehicle, a lorry for bulky waste, and volunteers who are free for the whole session. Doing this by hand from a spreadsheet is slow and easy to get wrong (an expired certificate, a 17-year-old, someone who is only free in the afternoon).

**Users** (as the app describes them):
- **NGO / volunteer coordinator**: enters the inputs, reads the plan, approves each crew. The app says this repeatedly: "Everything here is a suggestion. A coordinator approves every crew."
- **Team leaders and volunteers**: receive the crew briefings.
- **Residents**: the households are described in the notes (a baby, an elderly person living alone, and so on). They don't use the app.

## 2. Inputs and widgets

The PartyRock app is named **"Cleanup Crew Matcher"** (the in-app title reads "CleanUp Crew Matcher"). Its widgets, top to bottom:

| # | Widget | Type | What it holds in the recording |
|---|---|---|---|
| 1 | Title + "How to use" | static text | 3 steps: upload one photo per house and add notes; paste the roster and crew rules; read the outputs and send the briefings once a coordinator approves. |
| 2 | Language | dropdown | English |
| 3 | House Photos | file upload (1–4 images) | `B1.jpg`, `B2.jpg`, `B3.jpg`, `B4.jpg` |
| 4 | House Notes | text input | One line per house: B1–B4, giving location, distance from Surau Contoh Baru, house type, residents and the work needed |
| 5 | Volunteer Roster | file upload | `volunteer_roster_B.csv` |
| 6 | Crew Rules | text input | 10 numbered NGO rules for **Sunday 15 November 2026** (listed below) |
| 7 | Job Cards | AI text | Per house: seen in photo, from notes, tasks, tools, crew size and hours, bulky waste, priority |
| 8 | Safety Hand-Offs | AI text | Per house: hazard table (what was seen, why it matters, who to hand off to) plus structural, electrical and gas lines |
| 9 | Crew Plan | AI text (shows "Thinking") | Step 1: eligibility check for every volunteer. Step 2: house readiness. Then the crew table with rule checks and a transport plan, the unassigned list, gaps, and "Suggested plan. A coordinator must approve each crew." |
| 10 | Crew Briefing Card | AI image | A generated illustration of a volunteer crew outside a house |
| 11 | Crew Briefings | AI text | Short message per crew (the model's reasoning mentions a "90-word limit"), with a copy-to-clipboard button |
| 12 | Coordinator Assistant | chatbot | What-if questions about crews, volunteers and rules |
| 13 | Disclaimer Text | static text | Can't judge safety from a photo; a coordinator approves every crew; photos only with residents' consent and no faces, number plates or house numbers; call 999 in an emergency |

**Crew rules entered (verbatim summary):**
1. Every crew needs 1 team leader and 1 first aider whose certificate is valid on the day of the clean-up, Sunday 15 November 2026.
2. Volunteers must be 18 or older. Anyone whose age isn't stated must be asked before being assigned.
3. Only a volunteer with a current electrician licence may check wiring, switchboards or flooded appliances, or turn the power back on. Expired licences and students don't count.
4. Possible structural damage (cracks, sagging or water-stained ceiling, leaning wall, rotten floorboards) means the house is Not ready until checked. Don't send a crew.
5. Don't move, open or use gas cylinders. Report them to the team leader.
6. Maximum 5 volunteers per crew, including the team leader. Work in pairs.
7. Volunteers without their own transport may go to a house more than 1 km from Surau Contoh Baru only if a crew member's vehicle has a free seat. Free seats are listed in the roster.
8. Houses with bulky waste need a lorry or van. If none is free, list it as a gap.
9. The session runs 8:00am–12:00pm and volunteers must be available for all of it. A 10-minute water break every hour.
10. Priority: households with babies, elderly or disabled residents first.

**House notes entered:**
- **B1**: Kg Contoh Baru, 200 m; double-storey terrace, ground floor flooded; young family with a 6-month-old baby; mud, wet carpet, rattan chairs to remove.
- **B2**: Kg Contoh Baru, 500 m; old wooden house on stilts; retired teacher living alone, walks with a stick; clean the main room and kitchen.
- **B3**: Taman Contoh Permai, 3 km; single-storey link house; couple and teenage son; kitchen and back room muddy; **switchboard got wet; residents want the power back on today**.
- **B4**: Kg Contoh Baru, 800 m; single-storey brick house; family of 4; porch and yard covered with broken furniture, a damaged mattress and rubbish bags.

**Photos** (all 2016×1152). The B photos are the ones used in the recording:
- B1: open living/dining room, muddy standing water, rattan sofa and chairs.
- B2: dark wooden interior, flooded floor.
- B3: kitchen with a mud line on the walls, a wall switchboard and loose wiring, appliances, a water tank.
- B4: brick house porch piled with black rubbish bags and broken wood.
- H1 (living room with mud and a sofa), H2 (kitchen with washing machines and mud), H3 (wooden kitchen with **red gas cylinders** and a stove). The H photos are **not used in the recording**. H3 would test rule 5 (gas).
- *(guess)* The photos look AI-generated or staged, not real disaster photos. There are no faces, number plates or house numbers.

## 3. What the app does, step by step (recording timeline)

| Time | Moment |
|---|---|
| 0:00 | Empty app: title, how-to-use, empty input widgets |
| 0:05–0:30 | macOS file picker; B1–B4.jpg selected and uploaded |
| 0:35–0:45 | File picker; `volunteer_roster_B.csv` uploaded |
| ~0:50–1:05 | House notes and the 10 crew rules entered |
| ~1:12 | **Play** clicked; widgets start "Thinking" |
| ~1:15–2:05 | **Job Cards** stream in (B1 → B4). The card opens with a photo-matching note (see section 6) |
| ~1:40–2:10 | **Safety Hand-Offs** stream in: hazard table per house |
| ~2:10–3:40 | **Crew Plan** reasoning is visible (long "Thinking…" text) |
| ~3:42 | Crew Plan Step 1: **eligibility table** for W01–W18 with ✅ / ⚠️ / ❌ / ❓ |
| ~3:50 | Totals: team leaders W01, W17; first aiders W02, W14; electrician W03 only → "Only 2 compliant crews can be formed" |
| ~3:55 | Step 2: house readiness. B2 is **Not ready** (rule 4); priority B1 → B3 → B4 |
| ~4:00 | **Crew table**: Crew A → B1, Crew B → B3, B2 Not ready, with rule checks 1–10 and a transport plan |
| ~4:05 | Not assigned list and **GAPS** |
| ~4:10–4:20 | **Crew Briefing Card** image appears; **Crew Briefings** generate |
| ~4:45–5:08 | Chat Q1: "V03 cannot come on Saturday. What changes?" (wrong roster ID, see section 6) |
| ~5:15 | Chat cleared |
| ~5:30–5:50 | Chat Q2: "Kavitha has a certificate. Why isn't she a first aider?" |
| ~6:00–6:15 | Chat Q3: "Jason says he can come at 10am. Can he lead a third crew?" |
| ~6:25–6:40 | Chat Q4: "Can Farid check the switchboard at B3 if Azman is busy?" |
| ~7:05–7:30 | Chat Q5: "Tan is 25. Where can he go?" |
| ~7:34 | Scroll to the Disclaimer |
| ~7:40–7:47 | Crew Briefings in full; **Copy to clipboard** clicked |
| ~7:48–8:13 | Browser side panel opens, a Google search for "whatsapp", WhatsApp Web stuck on "Loading your chats" until the recording ends. **Sending is never shown completing.** |

## 4. Outputs (what the app produced in the recording)

**Job Cards** (B1 example): seen in photo; from notes; 7 tasks (remove water, shovel mud, remove carpet, carry out rattan furniture…); tools; "Estimate: 4 volunteers, 3–4 hours"; bulky waste; priority. B2: 3 volunteers, 2–3 h, priority High (elderly resident, fall risk). B3: 3 volunteers, 2–3 h, **"Do not touch switchboard, wiring, or sockets"**, priority High. B4: 4 volunteers, 3 h, bulky waste needs a lorry or van, priority Medium.

**Safety Hand-Offs**: B1 → a licensed electrician to check sockets before power is restored, plus the team leader. B3 → **only a currently licensed electrician** may inspect or restore power, "even at the residents' request". Gas: "No cylinders visible… do not move/open, report to team leader (Rule 5)". Each house ends with "No hazard seen in the photo. This does not mean the house is safe. A team leader checks on arrival."

**Crew Plan** (the main result):
- **Crew A → B1** (Sun 15 Nov): W01 Syafiq (team leader), W14 Siti Aminah (first aider, valid 2028), W05 Rosnah (cleaning), W11 Hakim (cleaning/heavy lifting). Rule 3 ❌: no electrician (gap). Rule 8 ⚠️: no lorry/van (gap). Everyone lives in Kg Contoh Baru, so they walk.
- **Crew B → B3**: W17 Priyanka (team leader), W02 Grace (first aider, valid 2027), W03 Azman (electrician, licence valid 2028). Azman drives his van from Pekan Contoh and picks up Grace (free seat); Priyanka lives in Taman Contoh Permai.
- **B2: Not ready**. Possible structural risk (old wood on stilts plus water exposure). Escalate for inspection.
- **B4: no crew**. No third team leader and first aider pair.
- **Not assigned**: W04, W10, W18 (reserve); W06 (under 18); W07 (certificate expired before the event); W08 (after 2pm only); W09 (licence expired; no spare cleaning slot); W12 (no transport); W13 (Saturday only); W15 and W16 (ask their age).
- **Gaps**: B2 needs inspection; B1 needs a second electrician or a follow-up visit by Azman; B1 needs a lorry or van; B4 needs one more team leader **and** a first aider valid on 15 Nov, plus a lorry; W15/W16 could fill the B4 gap if confirmed 18+.

**Crew Briefings**: one ready-to-send message per crew (team leader, first aider, top 3 tasks, what to bring, DO NOT touch wiring, work in pairs), plus "Not ready" lines for B2 and B4.

**Coordinator Assistant answers**:
- Q1 (V03): "There's no volunteer 'V03' in the roster — IDs are prefixed with W. Did you mean W03 (Azman)?" It then explains Azman is only scheduled for Sunday, so the change has **no effect**.
- Q2 (Kavitha): the certificate is valid only until 10 Nov 2026, 5 days before the clean-up, so under rule 1 she can't count as the first aider. She may help as a cleaner.
- Q3 (Jason at 10am): No. Rule 9 requires the full 8am–12pm session, and there's no spare valid first aider to pair him with anyway.
- Q4 (Farid at B3): No. His licence expired in 2025 (rule 3). If Azman is unavailable it becomes a gap to escalate, not a swap.
- Q5 (Tan is 25): now eligible. Crew A has 1 slot and Crew B has 2. He has his own car. Not B4, because that's still missing a team leader and first aider pair.

Every answer ends with "Coordinator to confirm."

## 5. Planted edge cases: checked against the CSVs, and whether the app handled them

I checked every item below against the CSV rows myself.

### Roster B (clean-up Sunday 15 Nov, 8am–12pm), the roster used in the recording

| Edge case | CSV confirms | Handled in recording? |
|---|---|---|
| W07 Kavitha: certificate valid only until 10 Nov 2026 | ✅ "valid until 10 Nov 2026" | **Yes**: "Cannot count as first aider"; also explained in chat Q2 |
| W06 Ahmad is 17 (with his mother W05) | ✅ age 17 | **Yes**: "Not eligible — age 17" |
| W08 Jason: after 2pm only | ✅ "Sun after 2pm only" | **Yes**: not eligible (rule 9); chat Q3 |
| W09 Farid: licence expired 2025 | ✅ "licence expired in 2025" | **Yes**: "Cannot count as electrician"; chat Q4 |
| W04 Nadia / W10 Nadia R.: possible duplicate | ✅ same age 22, cleaning, no transport, Kg Contoh Baru | **No**: both listed as separate eligible reserves; no duplicate warning |
| W13 Rahman: Saturday only (the only lorry) | ✅ "Sat only", own 1-tonne lorry | **Yes**: excluded, and the lorry gap is raised for B1 and B4 |
| W15 Daniel: age "18+" | ✅ "18+" | **Yes**: "Needs a question: What is Daniel's exact age?" |
| W16 Tan: age blank | ✅ empty age field | **Yes**: "Needs a question"; chat Q5 shows him being placed once his age is given |
| free_seats column | ✅ e.g. W03 van 2, W17 car 3, motorbikes 0 | **Yes**: Grace (no transport) gets a seat in Azman's van for the 3 km trip; Hakim's motorbike is noted as "no passenger seats"; Mei Xin is held back for lack of a seat |
| Only 2 valid team leaders (W01, W17), 2 valid first aiders (W02, W14), 1 valid electrician (W03) | ✅ derived from the CSV | **Yes**: the app states exactly this and concludes only 2 crews are possible |

### Roster A (clean-up on Saturday)

| Edge case | CSV confirms | Handled in recording? |
|---|---|---|
| V08 Nurul: first-aid certificate expired 2023 | ✅ "expired in 2023" | **Not shown** |
| V11 Wei Jie is 17 | ✅ age 17 | **Not shown** |
| V07 Hafiz: electrical TVET student, not qualified | ✅ | **Not shown** |
| V14 Amir: availability "not stated" | ✅ | **Not shown** |
| V06 Farah: Sunday only | ✅ "Sun only" | **Not shown** |
| Only V01 and V15 are trained team leaders free on Saturday | ✅ (V06 is the other team leader, Sunday only) | **Not shown** |
| Only V02 and V16 are valid first aiders | ✅ (V08 expired) | **Not shown** |
| V03 Ravi: "listed as qualified by NGO" (no licence stated) | ✅. Looks planted to test rule 3's "current licence" wording | **Not shown** |
| Roster A has **no free_seats column** | ✅ | **Not shown** |

**Roster A is never loaded in this recording.** The only trace is chat Q1, which uses a Roster A–style ID ("V03"), and the app correctly says no such volunteer exists in the loaded roster.

## 6. Things I'm unsure about, and possible weaknesses

1. **Photo matching by filename.** The files were named B1–B4.jpg, yet the Job Cards say "No file names (H1, H2, H3…) were provided with the photos… matching by visual content." The matching came out right, but the app apparently can't see filenames. Also, the how-to-use text says to name photos H1, H2, H3, while this demo used B-names.
2. **Rule 6 "work in pairs" with a crew of 3.** Crew B has 3 members and still gets ✅ for rule 6 ("working as a trio"). This is debatable, so it's better not to highlight it.
3. **B2 marked Not ready** on "old wood on stilts + water exposure", not on a visible crack or sag. That's cautious and arguably correct under rule 4, but it's inferred *(guess: from the notes as much as the photo)*.
4. **Distances to volunteers' homes** aren't in the data. The app assumes people living in Kg Contoh Baru are within 1 km of B1, B2 and B4 *(reasonable guess by the app)*.
5. **The Crew Briefing Card image shows a child-sized figure in the crew**, which clashes with the 18+ rule. Use it briefly or not at all in the video.
6. **Sending briefings**: the recording ends on WhatsApp Web loading. The send itself isn't shown.
7. Which AI model PartyRock used isn't visible. The "Thinking…" panels suggest a reasoning-capable model *(guess)*.
8. Whether the recording was a first run or a re-run *(unknown)*. The chat was cleared once, at about 5:15.

## 7. Privacy items to hide in the video

- The URL bar shows the PartyRock username (`partyrock.aws/u/imanzafri/…`). Crop or blur it.
- The macOS menu bar (date and time, status icons) and the PartyRock "PR" account badge in the sidebar.
- **7:48–8:13**: the browser side panel with tabs, a Google search and WhatsApp Web. **Cut entirely.**
- Volunteer names are made-up test data (per the brief in `02_plan/claude-code-prompt.md`), so they can stay on screen.
- Photos have no faces, number plates or house numbers.

## 8. Decisions from the Q&A (31 Oct 2026)

- **Roster A**: the video shows Roster B only. Reliability is proven with Roster B's edge cases and the chat what-ifs. Roster A is not mentioned.
- **Brief**: follow `02_plan/claude-code-prompt.md` (the longer brief).
- **Music**: the HeyGen catalog (free sign-in).
- **H1–H3 photos**: left out. Only the B photos the app actually processed are used.
