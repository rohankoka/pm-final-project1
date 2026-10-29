# A/B Experiment Brief, StreamLine (B2C)

## Parameters
| Parameter | Decision |
|---|---|
| Feature under test | Spotlight Curated Rail & Personalized Spotlight Queue |
| Persona | The Overwhelmed Viewer |
| Expected outcome | Help Wanderers find and start relevant content faster and return more often, improving Month 1 retention, reducing churn, and increasing subscriber lifetime value and retained revenue. |
| Primary success metric | Homepage-to-play conversion among Wanderers: the percentage of Wanderers who start content after visiting the homepage. A proposed target is a 10% relative improvement versus a control group. This directly signals that fewer users leave without finding something to watch |
| Baseline rate | 10% relative increase in homepage-to-play conversion versus control. |
| Guardrail metric | Month 1 subscriber retention for Casual Browsers and Power Users must not decline. Set a proposed tolerance of no more than a 2-percentage-point decrease versus control to protect the existing base |
| Guardrail boundary | Run a randomized test for 6–8 weeks, allowing at least one full month of retention follow-up. Calculate the required sample size using Wanderers’ baseline conversion before launch. Scale if conversion improves by at least 10% relatively, the improvement is statistically significant at 95% confidence, and the retention guardrail passes |
| Second guardrail | · |
| Minimum Detectable Effect | 2 |
| Sample size per arm | 3,841 |
| Traffic split | 50/50 |
| Test duration | 14 Days |
| Significance threshold | 0.03 |

## Control vs. Variant
- **Control (A):** User ends up watching anything after prolonged search and scrolling. They spend more time on searching. Basically an overload of Choices that confuses the user.
Numbers align where only 29% of homepage visitors start playing, and content searched then played fell from 41% to 34%. Numbers diverge where after playback starts and many do not reach 30 minutes. Average session length also fell from 31 to 24 minutes
- **Variant (B):** Screens to build
Entry Point — Homepage with Spotlight Rail
Show a prominently placed “Spotlight: Hand-picked for you to explore” rail with up to five curated titles, inviting the viewer to explore without endless scrolling.
Feature Core — Selected Title Preview
Show the selected title’s artwork, brief synopsis, runtime, and age rating, with a clear Play button. Allow viewers to return easily to the shortlist.
Success/Confirmation — Playback Started
Show the chosen content playing in the existing player. Playback itself confirms success; no extra confirmation step is needed.

Functional requirements
Homepage visibility: Display one clearly labeled Spotlight Curated Rail on the homepage for viewers assigned to the experiment’s treatment group.
Limited selection: Show one to five eligible titles, in the order manually configured by the content curator, without infinite scrolling within the rail.
Editorial control: Allow the curator to select and reorder titles using existing content tools or configuration, without requiring a code deployment.
Content eligibility: Display only titles available in the viewer’s region, included in their subscription, and permitted by their profile’s maturity settings.
Title selection and playback: Each card must display artwork and a title name, open the existing title preview, and provide a Play action using the existing player.
Accessible interaction: Viewers must be able to navigate the rail, select a title, and activate Play using the launch platform’s supported controls; all interactive elements must have accessible labels and visible focus states.
Failure handling: Hide the rail if it fails to load or contains no eligible titles; the remaining homepage and existing playback paths must continue functioning.
Experiment measurement and rollback: Record experiment assignment, homepage visits, and playback starts to calculate Wanderer conversion and each protected cohort’s Month 1 retention; allow the team to disable the rail without a code deployment.
- **Held constant (isolation check):** Not changed. It is constant

## Hypothesis
> I believe that Spotlight Curated Rail & Personalized Spotlight Queue for The Overwhelmed Viewer will result in Help Wanderers find and start relevant content faster and return more often, improving Month 1 retention, reducing churn, and increasing subscriber lifetime value and retained revenue., as measured by a 2 change in Homepage-to-play conversion among Wanderers: the percentage of Wanderers who start content after visiting the homepage. A proposed target is a 10% relative improvement versus a control group. This directly signals that fewer users leave without finding something to watch within 14 Days. We will protect Month 1 subscriber retention for Casual Browsers and Power Users must not decline. Set a proposed tolerance of no more than a 2-percentage-point decrease versus control to protect the existing base throughout the test.

## Shipping criteria
> We will **ship** if Homepage-to-play conversion among Wanderers: the percentage of Wanderers who start content after visiting the homepage. A proposed target is a 10% relative improvement versus a control group. This directly signals that fewer users leave without finding something to watch improves by ≥ 2 at 0.03 and Month 1 subscriber retention for Casual Browsers and Power Users must not decline. Set a proposed tolerance of no more than a 2-percentage-point decrease versus control to protect the existing base does not reach Run a randomized test for 6–8 weeks, allowing at least one full month of retention follow-up. Calculate the required sample size using Wanderers’ baseline conversion before launch. Scale if conversion improves by at least 10% relatively, the improvement is statistically significant at 95% confidence, and the retention guardrail passes after 14 Days.
> We will **iterate** if direction is positive but lift is below the MDE.
> We will **kill** if the primary metric shows no improvement or moves negatively.
> The read date is fixed at the end of 14 Days, no results reviewed before this date.
