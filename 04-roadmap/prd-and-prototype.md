# Spotlight Curated Rail, Simplified PRD (StreamLine)

**Author:** Me · **Status:** Draft · **Target:** High-Fidelity Prototype · **Persona:** The Overwhelmed Viewer

## 1. The Big Picture
- **Vision:** Every Overwhelmed Viewer finds something worth watching within moments of opening StreamLine and spends their time enjoying it
- **Press release:** StreamLine introduces Spotlight Curated Rail, a hand-picked homepage shortlist that helps viewers find something worth watching without endless scrolling. Instead of facing row after row of options, viewers get a small, thoughtfully chosen selection and a clear path to press Play.

Built for the Overwhelmed Viewer, Spotlight tackles a familiar frustration: spending your limited free time searching, finding nothing appealing, and closing the app. By narrowing the choices, Spotlight helps viewers choose with confidence and spend more time enjoying what they came for.
- **Success metric:** Homepage-to-play conversion among Wanderers: The percentage of Wanderers who start watching content after visiting the homepage.  For example, if the control group converts at 40%, Spotlight’s target is 44%—meaning fewer viewers leave without watching.
- **Guardrail:** Month 1 subscriber retention for Casual Browsers and Power Users, measured separately.  Target: No decline versus the control group, with a proposed maximum tolerance of a 2-percentage-point decrease in either cohort.  For example, if control-group retention is 80%, retention with Spotlight should ideally stay at or above 80% and must not fall below 78%. This protects existing subscribers while improving discovery for Wanderers.

## 2. The Details
### User stories
- As an Overwhelmed Viewer, I want to easily find the Spotlight rail on the homepage so that I can discover something appealing without endless scrolling.
- As an Overwhelmed Viewer, I want a shortlist of no more than five hand-picked titles so that I can choose without feeling overwhelmed.
- As an Overwhelmed Viewer, I want to see each title’s artwork, name, and brief description so that I can quickly decide whether it interests me.
- As an Overwhelmed Viewer, I want Spotlight to show titles available to my profile and subscription so that I can watch anything I choose.
- As an Overwhelmed Viewer, I want to start watching directly from a Spotlight title so that I can spend less time navigating and more time enjoying content.
- As a content curator, I want to select and order Spotlight titles using existing content tools so that I can offer viewers a focused editorial shortlist.
### Screens to build
- Entry Point — Homepage with Spotlight Rail
- Show a prominently placed “Spotlight: Hand-picked for you to explore” rail with up to five curated titles, inviting the viewer to explore without endless scrolling.
- Feature Core — Selected Title Preview
- Show the selected title’s artwork, brief synopsis, runtime, and age rating, with a clear Play button. Allow viewers to return easily to the shortlist.
- Success/Confirmation — Playback Started
- Show the chosen content playing in the existing player. Playback itself confirms success; no extra confirmation step is needed.
### Functional requirements
- 1. Homepage visibility: Display one clearly labeled Spotlight Curated Rail on the homepage for viewers assigned to the experiment’s treatment group.
- 2. Limited selection: Show one to five eligible titles, in the order manually configured by the content curator, without infinite scrolling within the rail.
- 3. Editorial control: Allow the curator to select and reorder titles using existing content tools or configuration, without requiring a code deployment.
- 4. Content eligibility: Display only titles available in the viewer’s region, included in their subscription, and permitted by their profile’s maturity settings.
- 5. Title selection and playback: Each card must display artwork and a title name, open the existing title preview, and provide a Play action using the existing player.
- 6. Accessible interaction: Viewers must be able to navigate the rail, select a title, and activate Play using the launch platform’s supported controls; all interactive elements must have accessible labels and visible focus states.
- 7. Failure handling: Hide the rail if it fails to load or contains no eligible titles; the remaining homepage and existing playback paths must continue functioning.
- 8. Experiment measurement and rollback: Record experiment assignment, homepage visits, and playback starts to calculate Wanderer conversion and each protected cohort’s Month 1 retention; allow the team to disable the rail without a code deployment.
### Smart behaviors (Situation → Outcome)
- If a viewer is assigned to the treatment group and eligible picks are available, then show the Spotlight rail on the homepage.
- If a viewer is assigned to the control group, then show the existing homepage without Spotlight.
- If more than five titles are configured, then show only the first five eligible titles in the curator’s chosen order.
- If a title is unavailable in the viewer’s region, subscription, or maturity settings, then exclude it and use the next eligible curated title.
- If fewer than five eligible titles remain, then show the available titles without adding filler recommendations.
- If no eligible titles remain or the rail fails to load, then hide Spotlight and keep the rest of the homepage usable.
- If the viewer selects a title, then open its existing preview with a clear Play action.
- If the viewer activates Play, then launch the existing player and record a playback start only when content actually begins.
- If the viewer returns from the title preview, then restore the homepage and their position in the Spotlight rail.
- If Spotlight is disabled through configuration, then stop showing the rail while preserving existing homepage and playback functionality.
### Technical constraints
- Single-file prototype: Build one self-contained HTML file with embedded CSS and JavaScript.
- No backend, APIs, or database: Use a hardcoded list of up to five curated titles with sample artwork and metadata.
- In-memory state only: Use simple JavaScript variables for the selected title and current screen; no login, cookies, or persistent storage.
- Exactly three screens: Homepage entry point → selected title preview → simulated playback success.
- No real streaming: Clicking Play opens a mock player; clearly label playback as simulated.
- No AI or personalization: Show the same editorial shortlist to every prototype user.
- No editorial admin interface: Define title selection and ordering directly in the code.
- No live experiments or analytics: Simulate eligibility and experiment assignment; production measurement remains outside this prototype.
- No additional features: Exclude search, filters, mood selection, downloads, watch parties, and curator profiles.

## 3. The Logistics
### Features out
- AI personalization and personalized queues: Spotlight uses one manually curated shortlist.
- AI-generated explanations: No “Why You’ll Love This” labels in the first release.
- Mood selection, advanced filters, and preference onboarding: No extra steps before discovering titles.
- Hidden Gem badges and curator profiles: No badges, curator following, or social discovery.
- Digest emails, watch parties, and offline downloads: Excluded from the core homepage-to-play experience.
- New editorial CMS, recommendation backend, or custom player: Reuse existing tools and components.
- Full homepage redesign and simultaneous cross-platform rollout: Add one rail on one launch surface.
### Edge cases & safety guard
- No eligible titles or rail fails to load->Hide Spotlight; keep the rest of the homepage usable.
- Title becomes unavailable after selection->Explain that it is unavailable and offer a return to Spotlight; never leave the viewer stuck.
- Title violates region, subscription, or maturity restrictions->Exclude it; never bypass content restrictions.
- Prototype simulates playback or eligibility->Clearly label the simulation; never imply that real streaming, restriction checks, or analytics are active.
### Decision log
- Use a manually curated shortlist of up to five titles; exclude AI personalization.
- Reuse existing title previews and playback components; exclude a custom player.
### Evals
- Task accuracy / completion
- Time-on-task
- Safety

## MoSCoW scope
- **Must:** Spotlight Curated Rail; Personalized Spotlight Queue
- **Should:** 'Why You'll Love This' Label; Mood-Based Entry Point
- **Could:** Hidden Gem Badge
- **Won't (now):** Spotlight Digest Email; Curator Profiles; Watch Party (Spotlight); Advanced Filter Engine; Offline Download (Spotlight)

---
**Builder hook:** Build a working prototype based on this PRD. Use the User Story as the core flow, Functional Requirements as build constraints, and prioritize speed and clarity over visual complexity.
