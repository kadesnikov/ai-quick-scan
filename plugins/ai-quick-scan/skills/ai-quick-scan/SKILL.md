---
name: ai-quick-scan
description: AI & Process Automation Quick Scan for small and mid-size businesses: pre-call company research, CEO call prep, maturity and process audit, prioritized AI use cases and a client report.
---

# AI Quick Scan

AI & Process Automation Quick Scan for small and mid-size companies (1-250 people), mostly in DE/AT/CZ. It turns whatever the user gives (a photo of a sign, a business card, a website, a few lines of notes, a call transcript) into a researched, scored audit with concrete AI use cases.

Work in the user's language (default: Russian). Write client-facing material in the language the user asks for (default: the language of the client, otherwise Russian).

## Detect the stage

Decide from the input which stage to run. Say in one line which stage you are running.

| Input | Stage |
|---|---|
| Company name, sign, card, website, short notes, no call yet | 1. Pre-call research + 2. Call prep |
| Call transcript, call notes, answers to the checklist | 3. Audit (maturity + processes) + 4. Use cases |
| "Make the report / PDF" after stage 3-4 | 5. Client report |

If an earlier stage was done in this conversation or a client doc already exists, continue from it; never redo research that is already there.

## Where the work lives

Create one doc per client (the Docs artifact type if available, otherwise a markdown file), titled `Quick Scan · <Company>`, with sections: Dossier, Hypotheses, Call questions, Audit, Use cases, Report notes. Fill sections as each stage completes. If the user keeps a shared constructor doc (methodology, industry modules, case library), read it first and reuse its modules and cases; after the audit, list new cases or questions worth adding back to it (and to the module library below, via a pull request to this repo).

## Stage 1 - Pre-call research (target: 1-2 h of analyst work, ~30 min for you)

Goal: arrive at the call with hypotheses, not with "what does your company do?".

Research with web search and fetch; open the pages you cite. Cover:

| Field | DE / AT sources | CZ sources |
|---|---|---|
| Legal entity, register no., founding date, capital | Handelsregister, North Data, firmenwissen (Creditreform) | justice.cz, ARES |
| Business purpose | Register entries | justice.cz |
| Management and authority (GF, Prokura) | North Data, Handelsregister | justice.cz |
| Financials | Unternehmensregister / Bundesanzeiger, North Data | Sbirka listin, Merk, Cribis |
| Products, channels | Website, Airbnb/Booking, ImmoScout24, marketplaces | Website, Sreality, Booking, Heureka |
| Reviews and pain signals | Google, Airbnb, Booking, Trustpilot - recurring complaints | Google, Heureka, Firmy.cz |
| Team and hiring | LinkedIn, Indeed, StepStone (mass hiring for one role = manual work) | LinkedIn, jobs.cz |
| Tech stack and marketing | Website stack, Meta Ad Library | same |
| Market context | Local news, city open data, industry press | same |

Rules:
- Company-level data and public register roles only. Do not collect private life details or personal data of employees. Do not look up the private address or family of anyone.
- Every fact gets a link. Unknown = write "not found" and turn it into a call question.
- Distinguish facts from inferences. Flag mismatches (e.g. the contact is a Prokurist, not the Geschaeftsfuehrer -> ask who signs).
- Assign a provisional AI maturity stage (MIT CISR: 1 Experiment & prepare, 2 Pilots & capabilities, 3 Scale, 4 AI-driven) from signals such as website quality, own-domain email, booking/CRM tools, online channels.

Output: a dossier table (field / fact / source), 3-5 "signals for the audit", and a list of open gaps.

## Stage 2 - Call prep

1. Map each business line to industry modules (below). Create a new module ad hoc if none fits.
2. Write 5-10 hypotheses: "In <line>, <manual work> likely costs <rough hours>; AI could <do X>."
3. Build the call script (60-90 min):
   1. Frame and consent to record (5 min)
   2. Dossier check: "Do we understand correctly that..." (10 min)
   3. Goals for 12 months; where money and time leak; what blocks growth without hiring (15 min)
   4. Module questions + personal questions per business line (25-40 min)
   5. Readiness: systems, access/API, prior AI attempts, owner, budget, payback horizon, constraints (GDPR, clients) (10 min)
   6. "Which one task should disappear tomorrow?" + date for the review call (5 min)
4. Add a capture table to fill during the call: business line | share of revenue % | hours/week manual | volume/month | systems | pain 1-5.
5. Pick one demo to show in the call: a 1-page AI output made on the client's real public data (e.g. a review analysis, a summary of a real document). Prepare it if the user agrees.

## Stage 3 - Audit (after the call)

Read the transcript/notes fully. Extract facts into the capture table; mark anything estimated.

### 3.1 Company maturity
- MIT CISR stage 1-4, with the evidence.
- 5 readiness pillars, each 1-5 with one line of evidence: Strategy & use cases, Data, Technology & integrations, People & culture, Governance & risk (GDPR, EU AI Act risk class of planned cases).

### 3.2 Process maturity (Hammer PEMM, adapted)
For each key process (3-6), rate P1-P4 per enabler, each with evidence:
- Design (documented end to end?), Performers (skills), Owner (named, with authority?), Infrastructure (IT supporting it), Metrics (defined and used?)
- plus Agent readiness: share of rules vs judgment, input data quality, system access (API / UI only / email / paper), human-in-the-loop points.

A process cannot sit above the enterprise maturity: if there is no owner or metrics, note "fix first" as a prerequisite. Use behavioral descriptions so two analysts would give the same score; never score without evidence - write "no data" instead.

### 3.3 Process map
For each key process: trigger -> steps -> systems -> handoffs -> exceptions -> workarounds -> time per unit -> volume. Flag copy-paste between systems, waiting on people, rework.

## Stage 4 - Use cases

For each candidate:
- What it does (one sentence), process and module
- Effect per month = manual hours x automatable share x hourly rate (+ extra revenue if any). Show the formula and inputs; label estimates.
- Value 1-5 (volume, time x rate, cost of error, bottleneck impact)
- Feasibility 1-5 (rules vs judgment, data, system access, verifiability of output, reversibility of mistakes - irreversible actions such as payments, prices, access need human approval)
- Autonomy level: assistant / agent with approval / agent with spot checks / autonomous. Start at "agent with approval".
- Complexity: L (days, no-code) / M (2-4 weeks) / H (integrations, 1+ month); tools
- Quadrant: Quick win / Big bet / Template filler / Not now

Rank, pick 1-2 pilots (quick wins with clear KPI), and say plainly what should NOT be automated now and why. Do not bend findings toward what the agency sells.

## Stage 5 - Client report (8-12 pages)

1. One-page summary: maturity stage, top 3 opportunities with EUR and hours, recommended pilot
2. Company and market profile (from the dossier) and what competitors already do with AI
3. Traffic-light view of business functions
4. 5-10 use cases with effect, complexity, timeline
5. Value x feasibility 2x2 matrix
6. Recommended pilot: scope, timeline, price placeholder, KPIs
7. Risks and what the client must prepare (data, access, owner)
8. Offer and next step

Produce it as a document (Docs type, exportable to PDF) unless the user asks for a .pdf or .pptx file directly. Recommend presenting it on a 30-minute call rather than only emailing it.

## Industry modules (starter library)

Each module: typical cases | rough effect for a small business | complexity. Extend it after each audit.

- Real estate brokerage: lead qualification from portals (4-8 h/wk, L-M); expose generation and translation (2-3 h/property, L); viewing scheduling and follow-up (2-4 h/wk, L); document checklist per deal (1-2 h/deal, L).
- Project development: site pre-assessment from Bebauungsplan / listings (3-6 h/site, M); residual-value feasibility template (faster go/no-go, M); site monitoring digest (3-5 h/wk, L-M); letters to authorities and bid comparison (3-5 h/wk, L).
- Foreclosure auctions (Zwangsversteigerung): lot filter from the ZVG portal (2-4 h/wk, L-M); Gutachten summary with red flags (1-2 h/lot, L); max-bid calculator (L).
- Apart-hotel / short-term rental: 24/7 multilingual guest concierge on Airbnb/Booking/WhatsApp (5-10 h/wk + rating, L-M); dynamic pricing around fairs and seasons (L, verify uplift on data); review analysis and replies (1-2 h/wk, L); ops: cleaning schedule, lock codes, invoices, tourist tax (3-6 h/wk, M).
- Social / municipal housing placements: day-rate invoicing per authority from the occupancy log (3-6 h/wk, L-M); payment and Kostenuebernahme expiry tracking (L); letters and occupancy reports (2-3 h/wk, L). Residents' personal data only on EU infrastructure with a DPA.
- Consulting: meeting recording -> minutes, proposal, report in the needed language (3-6 h/wk, L); client research drafts (4-8 h/job, L).
- SMB back office (always include): email triage and drafts (3-5 h/wk, L); receipts and invoices to Lexoffice/DATEV for the tax advisor (2-4 h/wk, L); weekly owner dashboard (1-2 h/wk, L-M).
- New ventures: AI-assisted research of a client's idea (market size, competitors, suppliers, regulation, one-page financial model) - sold as a separate 2-3 day service.

## Quality bar

- Money, not just scores: every case shows hours, FTE share and EUR.
- Evidence for every score; estimates labeled as estimates until the client confirms numbers.
- Honest "not now" list.
- Recorded calls and screen recordings contain personal data: remind the user about consent, a DPA, EU storage and masking.
- End each stage with: what was produced, the 2-3 gaps that matter most, and the next stage.
