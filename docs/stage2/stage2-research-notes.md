# Stage 2 reference notes

Researched 31 Oct 2026. These notes feed the Stage 2 roadmap scene. **Nothing here is built. The Stage 2 scene must say "Roadmap".**

## 1. How past CendekiAwan / PartyRock entries were framed

- **CendekiAwan Malaysia, 2026 phase (AWS + Elitery + Asia Pacific University).** Teams built PartyRock prototypes across five themes, including **GovTech & Social Impact**. Judges scored finalists on innovation, prompt-development quality, relevance to the theme, and potential impact. Of the 60 teams, 20 were picked on the quality of their PartyRock prototype to develop further with **Amazon Bedrock and Kiro**. The GovTech & Social Impact winner was "City Mind MY", pitched as a tool that helps *authorities* plan (traffic, walkability, accessibility) through data-driven insights and policy simulation.
  - What this tells us: the winning framing names **who it helps decide** (an authority or a coordinator) and **what decision gets better**, and treats the prototype as the step before a Bedrock build.
  - Sources: [Elitery investor release](https://ir.elitery.com/press-release/aws-and-elitery-expand-cendekiawan-malaysia-program-with-asia-pacific-university-to-advance-student-ai-application-development/), [Digital News Asia](https://www.digitalnewsasia.com/digital-economy/aws-elitery-expand-cendekiawan-malaysia-programme-asia-pacific-university-advance), [techent.tv](https://techent.tv/2026/05/26/aws-and-elitery-turn-malaysian-students-into-ai-developers-with-expanded-cendekiawan-program/), [CendekiAwan Malaysia site](https://cendekiawan-malaysia.elitery.com/about/)
- **AWS CendekiAwan 2.0 national showcase (20 Oct 2026, Universiti Malaya).** A Multimedia University team won overall with an AI solution that turns parliamentary Hansard into plain language. The framing is a public-interest problem, a clear before and after, and AI as the translator.
  - Source: [MMU news](https://www.mmu.edu.my/2026/10/mmu-team-wins-overall-title-at-aws-cendekiawan-2-0-national-showcase/)
- **PartyRock Generative AI Hackathon (2024, global).** About 7,650 registrants and 1,200+ projects. The winners were framed around one clear experience per app. Apps are remixable, and PartyRock runs on Amazon Bedrock models.
  - Source: [AWS News Blog](https://aws.amazon.com/blogs/aws/congratulations-to-the-partyrock-generative-ai-hackathon-winners)
- No IIUM-specific past entries were found online. The competition facts in the brief (Stage 1 due 6 Nov, Stage 2 "Bedrock Scale-Up" due 13 Nov, Stage 3 hackathon in KL) come from the user's own check of the official page.

**Takeaways for our video:**
1. Lead with the decision-maker (the NGO coordinator) and the decision (who goes where, safely).
2. Show impact as *safer, rule-checked decisions*. No invented numbers.
3. Present PartyRock as the validated prototype and Stage 2 as the "Bedrock scale-up" path, using AWS's own reference patterns.

## 2. AWS reference architectures to borrow from

- **Guidance for Generative AI Assistant on AWS**: a React web app served by **AWS Amplify**, **Amazon Cognito** sign-in, **AWS Lambda** calling **Amazon Bedrock**, and **Amazon DynamoDB** for stored state. ([guidance page](https://aws.amazon.com/solutions/guidance/generative-ai-assistant-on-aws), [docs](https://docs.aws.amazon.com/solutions/generative-ai-assistant-on-aws/))
- **Amplify AI kit**: AppSync as the serverless API layer, plus Lambda, DynamoDB and Bedrock; conversation history is stored in DynamoDB. ([Amplify AI architecture](https://docs.amplify.aws/react-native/ai/concepts/architecture))
- **Guidance for Agentic Workflow Assistants**: **Amazon S3** for stored documents, with Amplify hosting the front end. ([guidance page](https://aws.amazon.com/solutions/guidance/agentic-workflow-assistants-on-aws))

## 3. Proposed Stage 2 roadmap (for the video, labelled ROADMAP)

```
PartyRock prototype (built, Stage 1)
        ↓
Web app on AWS (roadmap)
  Amplify      → coordinator web app (+ Cognito sign-in per NGO)
  S3           → house photo and roster uploads
  Bedrock      → job cards, safety hand-offs, crew matching, chat
  DynamoDB     → rosters, crew rules, approved crews
```

Each item maps to something the PartyRock app already does (the uploads, the rules text box, the AI widgets, the approval step), so the roadmap reads as a port, not a new product. Keep the on-screen version to four labelled blocks.
