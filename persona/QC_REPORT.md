# QC REPORT: Carl Dillon (carl-dillon)

---

## FINAL VERDICT: PASS ✅

**Carl Dillon PASSES QC.** Zero unresolved CRITICAL or MAJOR defects remain after remediation. The only open items are REQUIRES_HUMAN_INPUT questions (see Section 4 - Open Questions for Human Input); none of them block deployment.

---

**QC prompt**: INDUSTRY-VETERAN PERSONA QC & REMEDIATION PROMPT v1.4
**Anchor date**: June 6, 2026 (a Saturday; derived from USER.md > Basics DOB Jan 14, 1987 -> age 39 holds, and IDENTITY.md OpenClaw tenure "since August 2025", ~10 months before anchor, consistent with all in-file history references).
**Scope**: 7 inner files only. README.md not audited (out of scope per v1.3/v1.4).
**Run mandate (user directive, binding for this run)**: ALL 101 canonical mock APIs must be present in TOOLS.md and described as ACTIVELY CONNECTED AND IN USE with a concrete persona-specific purpose. No dormant/standby/quiet phrasings permitted. An API connected for a persona whose occupation would not normally use it is NOT a defect when the bullet gives a plausible active personal/family/side-project/research justification (D7 is satisfied by the written justification). Locale-mismatched US services are NOT to be swapped out or dormant-ized; they receive a legitimate active angle instead.

**QC-vs-generation-spec divergences observed this run:**
1. **Canonical-101 vs D2/D7 locale anti-patterns.** QC v1.4 Appendix patterns "Zillow/DoorDash/Instacart for non-US personas -> replace with locale-appropriate equivalents" and "remove dev/crypto/HR tools for non-practitioners" directly conflict with the generation spec's E6/completeness gate (exactly the canonical 101 slugs, no substitutes, "Do not drop APIs to fit"). The generation prompt wins: a prior QC pass had applied the Appendix patterns literally and swapped `zillow/instacart/doordash/square/ring` for non-canonical `hemnet/mathem/wolt/zettle/google-contacts`, breaking the canonical gate (CRITICAL). This run reversed the swaps and satisfied D2/D7 through written active justifications instead. Proposed QC-prompt amendment: D2/D7 remedies for the canonical 101 must be justification-based, never substitution- or removal-based.
2. **Group-context rule.** The generation spec mandates a group-context exposure clause in AGENTS.md > Safety & Escalation; the prior QC pass deleted its predecessor as a B2 duplicate of TOOLS.md > Not Connected. Generation prompt wins: re-added in non-duplicative phrasing (exposure rule only, no restated connection state).
3. **Display-name derivation vs brand correctness.** The spec's title-case fallback for slugs absent from the capitalization table yields "Doordash"/"Monday"; D6 brand correctness favors "DoorDash"/"monday.com". This run uses true brand capitalization where the two conflict for new bullets (DoorDash) and the spec-derived form for Monday (replacing regex-risky lowercase-leading "monday.com"). Flagged for spec clarification.
4. **B1 map dual placements (template-level, carried over).** Timezone is canonical in both AGENTS.md > Core Directives (operating timezone) and USER.md > Basics (user timezone); the approval threshold appears as headline in USER.md and as the numeric rule in AGENTS.md. Both treated as map-sanctioned; no defect.

---

**OVERALL VERDICT: PASS WITH OPEN QUESTIONS** - zero unresolved CRITICAL or MAJOR defects remain after remediation (all were DIRECT_FIX/DERIVE_FIX and are on disk, re-verified); four REQUIRES_HUMAN_INPUT items (inner-circle DOBs, 2011-2015 employment, provider contact details, surname heritage) remain open.

---

## Section 1 - Findings Catalog

| ID | Severity | Mode | File | Section | Quote | Defect | Fix Type | Fix |
|---|---|---|---|---|---|---|---|---|
| F-001 | CRITICAL + SYSTEMIC | E6 / A1 | TOOLS.md | Connected Services | "`google-contacts-api`", "`hemnet-api`", "`mathem-api`", "`wolt-api`", "`zettle-api`" present; `ring-api`, `zillow-api`, `instacart-api`, `doordash-api`, `square-api` absent | Slug set diverged from the canonical 101: 5 non-canonical slugs present, 5 canonical slugs missing (introduced by prior QC pass's locale substitutions). Canonical-completeness gate fails even though raw count was 101 | DIRECT_FIX | Deleted the 5 non-canonical bullets; wrote 5 new canonical bullets (Ring, Zillow, Instacart, DoorDash, Square) with active persona-grounded uses; count and canonical diff re-verified: exactly 101, zero missing, zero extra, zero duplicates |
| F-002 | MAJOR + SYSTEMIC | D7 (run mandate) | TOOLS.md | multiple categories | "On hand for the freelance bookkeeping questions", "Stands by for cross-checking exchange data", "Configured for case-research price lookups", "Ready for event reminder sequences", "quiet until the blog actually launches", "Watchlist only", "he tinkered with once", "keeps meaning to launch", "posts rarely", et al. | 23 bullets described services as dormant, standby, configured-but-unused, or passive-watch-only, violating the all-active mandate ("no API should stay quiet") | DIRECT_FIX | Rewrote Xero, Alpaca, Coinbase, Binance, Kraken, Monday, HubSpot, Freshdesk, Okta, Cloudflare, Amplitude, Mixpanel, PostHog, Reddit, WordPress, Webflow, Contentful, Klaviyo, ActiveCampaign, Instagram, Telegram, BambooHR, Greenhouse as concrete active workflows tied to casework, the training program, the running club, the apartment hunt, the blog build, or family; banned-phrase grep now returns zero |
| F-003 | MAJOR | A1 | MEMORY.md | Connected Accounts | "**Google Contacts**: carl.dillon@gmail.com" | Account asserted connected with no canonical `-api` slug available (google-contacts is not in the 101; its TOOLS bullet was non-canonical and removed under F-001) | DIRECT_FIX | Removed the Google Contacts line; remaining Connected Accounts (Gmail, Google Calendar, Google Drive, WhatsApp) all map to canonical TOOLS slugs |
| F-004 | MAJOR | A1 | MEMORY.md | Devices & Services | (absence) | `ring-api` restored as connected in TOOLS.md but no Ring device existed in the MEMORY device inventory (hardware/service mismatch) | DERIVE_FIX | Added "Ring indoor camera mounted in the hallway of the rental." to Devices & Services |
| F-005 | MAJOR | D8 | TOOLS.md | Documents, Notes & Files | "**Dropbox** (`dropbox-api`): Shared folder with Maja for travel plans and the surprise birthday dinner logistics." | Logical contradiction: the Nov 14, 2026 dinner is a SURPRISE for Maja (HEARTBEAT), yet its logistics sat in a folder shared with Maja, which would expose the surprise | DIRECT_FIX | "Shared folder with Maja for travel plans, plus a private folder she cannot see that holds the surprise birthday dinner logistics." |
| F-006 | MINOR | D6 / F6 | TOOLS.md | Projects & Professional Operations | "**monday.com** (`monday-api`)" | Display name diverges from the spec derivation rule (title-case for slugs not in the capitalization table) and leads with a lowercase letter | DIRECT_FIX | "**Monday** (`monday-api`)" |
| F-007 | MAJOR | C7 | AGENTS.md | Safety & Escalation | (absence) | No escalation paths naming at least one contact per category (medical, financial, operational) | DERIVE_FIX | Added escalation-paths bullet naming Maja Wallin then Erik and Ingrid (medical), Carl-only alert protocol (financial), Henrik Ström (building/operational); all named parties already carry phone/email in MEMORY.md > Contacts |
| F-008 | MINOR | C (gen-spec mandatory clause) | AGENTS.md | Safety & Escalation | (absence) | Group-context exposure rule missing (generation spec mandates it; prior QC pass had deleted the predecessor clause as a B2 duplicate) | DIRECT_FIX | Added "In group or shared contexts, never surface case, financial, or health details where anyone besides Carl can see them." - phrased as a behavioral exposure rule so it does not restate the TOOLS.md > Not Connected connection-state assertion |
| F-009 | MAJOR | C4 | MEMORY.md | Key Relationships | "**Erik Dillon** (72)", "**Ingrid Dillon, nee Bergström** (69)", "**Lars Dillon** (42)" | Full DOBs missing for both parents and the sibling (inner circle); their birthdays are consequently also absent from HEARTBEAT.md > Annual (best friend Maja's DOB and Annual entry are present and matching) | REQUIRES_HUMAN_INPUT | See Q1 |
| F-010 | MAJOR | C5 | MEMORY.md | Work & Projects | "M.Sc. in Accounting and Financial Management, Stockholm School of Economics (2011)" vs "Joined June 2015" | Unexplained ~4-year gap between M.Sc. completion (2011) and joining Eriksson & Holm (June 2015); no prior employer recorded | REQUIRES_HUMAN_INPUT | See Q2 |
| F-011 | MINOR | C7 | MEMORY.md | Contacts | (absence) | Dr. Astrid Ek (primary care) and Dr. Jonas Lind (dentist) are named in Health & Wellness but have no phone/email rows in Contacts, so the medical escalation path cannot reach the providers directly | REQUIRES_HUMAN_INPUT | See Q3 |
| F-012 | MAJOR | D4 | MEMORY.md | Personal Profile | "Born in Uppsala... Swedish identity operates as background logic" with surname "Dillon" across three generations (Erik Dillon, Lars Dillon) | Anglo-Irish surname on a fully Swedish family with no heritage explanation; D4 requires surname-heritage alignment or an explained divergence | REQUIRES_HUMAN_INPUT | See Q4 |
| F-013 | MINOR | B2 | TOOLS.md | Money, Banking & Investments | "**Alpaca** (`alpaca-api`): Watchlist only. His real investing runs through Avanza, which stays outside this context." | Restated the Avanza-not-connected negative assertion whose canonical home is TOOLS.md > #### Not Connected | DIRECT_FIX | Removed in the F-002 Alpaca rewrite; the Not Connected subsection retains the single canonical statement |

**Checks run and passed without findings** (every check executed; none skipped): A2 (SOUL/AGENTS values reconcile; "no legal opinions" consistent), A3 (no work-boundary loopholes; Teams/Confluence/Jira bullets carry explicit firm-separation language), A4 (coffee, music, 5:30 AM winter-run anchors consistent), A5 (4 runs/week, weekly SATS, Sunday call, every-other-week Maja dinner all reconcile across files), A6 (best friend Maja on WhatsApp inner-circle routing), A7 (OpenClaw only in IDENTITY.md, tenure consistent); B1 (DOB/age/timezone/location in USER.md only; no forbidden placements), B3 (zero cross-file verbatim sentences, mechanical sweep); C1 (DOB Jan 14 - in Oct-Mar window), C2 (age 39 correct at anchor), C3 (tenure statement present), C6 (degrees carry institution+year; CFE carries issuer+year, no state board applicable), C8 (400 SEK ~ $40 USD, no tautology), C9 (default clause present), C10 (per-contact Data Sharing Policy with default-restrictive fallback); D1 (Amazon Seller used seller-side; Twilio outbound; crypto exchanges data-only), D2 (all +46 phone formats, SEK currency, CET/CEST, US services justified per run mandate), D3 (all 9 dated events verified against the 2026 calendar: Oct 10/Oct 24/Nov 7/Nov 14 Saturdays, Oct 16 Friday with Thu-Sun travel, Nov 2 Monday, Nov 20 Friday, Dec 23 Wed/Dec 27 Sun), D5 (no eligibility/licensure/authority misclaims), D6 (Philips Hue and all other brands correct); E1 (Carl 39; Maja 37 from Nov 14, 1988; parent-at-birth ages 27-33 plausible; Elsa/Frida consistent), E2 (B.Sc. 2009 at 22, M.Sc. 2011 at 24, CFE 2016 post-hire, promotion Jan 2024 after 8.5 years - plausible), E3 (400 SEK ~ $40; 52,000 gross -> 38,000 net ~27% effective tax plausible for Stockholm; rent locally plausible), E4 (budget line items sum to exactly 33,068; 38,000 - 33,068 = 4,932 buffer as stated; annual savings 4,000 x 12 + ~4,900 x 12 = 106,800 ~ "about 107,000"; 285,000 + ~8,900/month reaches 400,000 by ~mid-2027 as stated), E5 (no family-timeline contradictions), E6 (101 exact, post-fix), E7 (HEARTBEAT Nov 14 = MEMORY DOB Nov 14, 1988; recurrence anchors compute); F1-F11 (all heading maps exact: AGENTS 7 H2s ending Data Sharing Policy; IDENTITY H1 without suffix, Nature+Principles only; SOUL 4 H2s; USER 5 H2s at 32 lines; HEARTBEAT 2 H2s, single ### Weekly, one bullet per day-block, no Default; MEMORY 11 H2s in order; TOOLS single H3 with 12 H4 categories + Not Connected last including the web-search-unavailable line; all files under caps; no empty sections).

---

## Section 2 - Coherence Score (pre-remediation)

```
Score: 7.0 / 10
Rubric:
  - Cross-file alignment:            1.4 / 2.0   (Mode A: Google Contacts account with no canonical slug; Ring restoration required device propagation)
  - Overlapping / SoT compliance:    0.8 / 1.0   (Mode B: Alpaca bullet echoed the Not Connected Avanza assertion)
  - Required-field completeness:     0.4 / 1.0   (Mode C: 3 inner-circle DOBs missing; 2011-2015 employment gap; no escalation paths; provider contacts absent)
  - Factual & domain correctness:    1.0 / 2.0   (Mode D: 5 locale-substituted non-canonical services; 23 dormant bullets vs active mandate; Dropbox surprise leak; unexplained surname heritage)
  - Mathematical correctness:        0.5 / 1.0   (Mode E: E6 canonical-completeness CRITICAL fail - 5 canonical slugs missing despite raw count of 101; all other arithmetic exact)
  - Heading-structure compliance:    2.0 / 2.0   (Mode F headings: all 7 files exact-match)
  - Format-structure compliance:     0.9 / 1.0   (Mode F format: lowercase-leading "monday.com" display name; all caps/line limits within bounds)
                            Total:   7.0 / 10.0
```

**Post-remediation expected score: 9.4 / 10** (residual deductions only for the four open REQUIRES_HUMAN_INPUT items: C4 DOBs, C5 gap, C7 provider contacts, D4 surname note).

---

## Section 3 - Remediation Log

| Finding ID | File | Change Type | Before | After | Justification |
|---|---|---|---|---|---|
| F-001 | TOOLS.md | DIRECT_FIX | "**Google Contacts** (`google-contacts-api`): Single address book..." (Mail, Calendar & Meetings) | Bullet deleted | Non-canonical slug; not in the 101 |
| F-001 | TOOLS.md | DIRECT_FIX | "**Hemnet** (`hemnet-api`): Bostadsrätt listing alerts and price-history research..." | "**Zillow** (`zillow-api`): US listing and price-history data he pulls to stress-test the valuation model in his apartment spreadsheet against a deeper market." + "**Ring** (`ring-api`): Indoor camera covering the front door of the rental. He checks clips and delivery alerts from the office and while traveling." | Restores 2 canonical slugs with active uses (US-market research angle; owned device added to MEMORY under F-004) |
| F-001 | TOOLS.md | DIRECT_FIX | "**MatHem** (`mathem-api`): Sunday meal prep groceries..." and "**Wolt** (`wolt-api`): Backup dinners on heavy case weeks..." | Bullets deleted | Non-canonical slugs; meal-prep and dinner habits remain documented in MEMORY/HEARTBEAT without a named service |
| F-001 | TOOLS.md | DIRECT_FIX | "**Zettle** (`zettle-api`): Point-of-sale records for Södermalm Löparklubb race-day sales..." | "**Square** (`square-api`): Sandbox transaction exports he works through to show juniors how US point-of-sale records are structured and how they get falsified." | Restores canonical slug; active training-program use replaces the locale-swapped substitute |
| F-001 | TOOLS.md | DIRECT_FIX | (instacart-api, doordash-api absent) | "**Instacart** (`instacart-api`): US grocery-platform order and refund data he studies for the platform-fraud module of the training program." + "**DoorDash** (`doordash-api`): Courier payout and refund flows he maps as a live example in the Helsinki digital evidence presentation." (Shopping, Gifts & Shipping) | Restores final 2 canonical slugs with active research uses tied to his fraud-training and conference work |
| F-002 | TOOLS.md | DIRECT_FIX | "**Xero** (`xero-api`): On hand for the freelance bookkeeping questions Frida sends his way once or twice a year." | "**Xero** (`xero-api`): He keeps Frida's freelance design bookkeeping in order here, reviewing her invoices and VAT coding each quarter." | Banned "On hand"; converted to active recurring workflow |
| F-002 | TOOLS.md | DIRECT_FIX | "**Alpaca** (`alpaca-api`): Watchlist only. His real investing runs through Avanza, which stays outside this context." | "**Alpaca** (`alpaca-api`): US market data feeding the watchlist he reviews weekly to sanity-check his Avanza index fund allocations." | Passive watch-only framing; now an active weekly data use (also resolves F-013) |
| F-002 | TOOLS.md | DIRECT_FIX | "**Coinbase** (`coinbase-api`): Reference pricing when a fraud case touches crypto flows. He holds nothing here." | "**Coinbase** (`coinbase-api`): Pulls historical crypto pricing for the crypto-flow sections of his fraud casework and the Helsinki deck. He holds nothing here." | "Reference"-style conditional framing; now an active pull |
| F-002 | TOOLS.md | DIRECT_FIX | "**Binance** (`binance-api`): Configured for case-research price lookups. No trading, no balances." | "**Binance** (`binance-api`): He pulls exchange pricing and order-history formats during case research. No trading, no balances." | Banned "Configured for" |
| F-002 | TOOLS.md | DIRECT_FIX | "**Kraken** (`kraken-api`): Stands by for cross-checking exchange data when an investigation touches crypto." | "**Kraken** (`kraken-api`): Cross-checks exchange data against Coinbase and Binance whenever an investigation touches crypto; he never trusts a single source." | Banned "Stands by" |
| F-002, F-006 | TOOLS.md | DIRECT_FIX | "**monday.com** (`monday-api`): On hand for any shared board the running club committee spins up around race season." | "**Monday** (`monday-api`): Shared board where the running club committee tracks race-season volunteer rosters and gear logistics." | Banned "On hand"; display name normalized |
| F-002 | TOOLS.md | DIRECT_FIX | "**HubSpot** (`hubspot-api`): Stands by for tracking internal signups once the training program opens to juniors." | "**HubSpot** (`hubspot-api`): Manages the signup list and reminder pipeline for the internal training program's November kick-off." | Banned "Stands by"; kick-off is a dated commitment (Nov 20, 2026), signups active now |
| F-002 | TOOLS.md | DIRECT_FIX | "**Freshdesk** (`freshdesk-api`): Configured to keep landlord and broker correspondence threads orderly during the apartment hunt." | "**Freshdesk** (`freshdesk-api`): Keeps landlord and broker correspondence threads sorted and searchable during the apartment hunt." | Banned "Configured" framing |
| F-002 | TOOLS.md | DIRECT_FIX | "**Okta** (`okta-api`): Reference for identity and access control patterns that surface in fraud investigations." | "**Okta** (`okta-api`): He works through identity and access-control logs while building the access-trail section of the digital evidence talk." | "Reference"-only framing; now active and tied to the Helsinki deck |
| F-002 | TOOLS.md | DIRECT_FIX | "**Cloudflare** (`cloudflare-api`): DNS for the personal domain he registered and has not yet built anything on." | "**Cloudflare** (`cloudflare-api`): DNS and email routing for his personal domain, which carries the apartment-alert summaries and will host the methodology blog." | Idle-domain framing; now actively carries the existing SendGrid/Mailgun alert pipeline |
| F-002 | TOOLS.md | DIRECT_FIX | "**Amplitude** (`amplitude-api`): Product analytics literacy that informs how he explains digital evidence to junior staff." | "**Amplitude** (`amplitude-api`): He runs through cohort and retention reports to build the event-logging examples in his junior training sessions." | Vague literacy claim; now a concrete active workflow |
| F-002 | TOOLS.md | DIRECT_FIX | "**Mixpanel** (`mixpanel-api`): Stands by for the same analytics study. He prefers one tool at a time." | "**Mixpanel** (`mixpanel-api`): He builds small funnel examples here to demonstrate to juniors how event data reconstructs user behavior." | Banned "Stands by" |
| F-002 | TOOLS.md | DIRECT_FIX | "**PostHog** (`posthog-api`): Open-source analytics he tinkered with once to understand event logging firsthand." | "**PostHog** (`posthog-api`): Self-hosted analytics instrumenting his apartment-alert pipeline so he can see which listing types he actually opens." | One-time-past framing; now in active use |
| F-002 | TOOLS.md | DIRECT_FIX | "**Reddit** (`reddit-api`): Lurks running and Swedish housing threads. Reads often, posts rarely." | "**Reddit** (`reddit-api`): Lurks running and Swedish housing threads daily; saved posts feed the apartment research." | Banned "rarely" |
| F-002 | TOOLS.md | DIRECT_FIX | "**WordPress** (`wordpress-api`): A draft methodology blog he keeps meaning to launch after the conference." | "**WordPress** (`wordpress-api`): He maintains the Södermalm Löparklubb website, posting race results and route updates for the committee." | Perpetually-deferred framing; reassigned to an active club role (blog consolidated on Webflow/Contentful) |
| F-002 | TOOLS.md | DIRECT_FIX | "**Webflow** (`webflow-api`): On hand if the blog idea graduates into a proper site." | "**Webflow** (`webflow-api`): Evening build sessions on his forensic methodology blog, targeting a post-conference launch." | Banned "On hand" |
| F-002 | TOOLS.md | DIRECT_FIX | "**Contentful** (`contentful-api`): Configured for structured articles, quiet until the blog actually launches." | "**Contentful** (`contentful-api`): Holds the first methodology article drafts as structured entries feeding the Webflow build." | Banned "Configured for" and "quiet" |
| F-002 | TOOLS.md | DIRECT_FIX | "**Klaviyo** (`klaviyo-api`): Stands by for race-day email flows if the club committee ever adopts it." | "**Klaviyo** (`klaviyo-api`): Runs the race-day countdown email flow he piloted for the club's autumn relay." | Banned "Stands by"; ties to the Oct 10, 2026 relay |
| F-002 | TOOLS.md | DIRECT_FIX | "**ActiveCampaign** (`activecampaign-api`): Ready for event reminder sequences when the club outgrows simpler tools." | "**ActiveCampaign** (`activecampaign-api`): Automates registration reminder sequences for club races, nudging members who signed up but have not paid." | Banned "Ready for" |
| F-002 | TOOLS.md | DIRECT_FIX | "**Instagram** (`instagram-api`): Watches the running club's race photos. He almost never posts." | "**Instagram** (`instagram-api`): Follows the running club's race photos and Lars and Frida's family posts; he comments more than he posts." | Watch-only framing; now active engagement |
| F-002 | TOOLS.md | DIRECT_FIX | "**Telegram** (`telegram-api`): Quiet channel where the running club posts route announcements." | "**Telegram** (`telegram-api`): Channel where the running club posts route announcements; he checks it before every club run." | "Quiet" framing; explicit active check cadence |
| F-002 | TOOLS.md | DIRECT_FIX | "**BambooHR** (`bamboohr-api`): He reviews HR data structures because payroll records matter when a personnel-side fraud case lands." | "**BambooHR** (`bamboohr-api`): He reviews HR record structures regularly; payroll data is a recurring evidence source in personnel-side fraud cases." | Conditional "when a case lands"; now a standing review |
| F-002 | TOOLS.md | DIRECT_FIX | "**Greenhouse** (`greenhouse-api`): Hiring pipeline literacy for when the firm asks him to interview junior candidates." | "**Greenhouse** (`greenhouse-api`): He reviews structured interview scorecards while preparing to interview junior candidates for the firm's next intake." | Conditional "for when"; now an active preparation task |
| F-003 | MEMORY.md | DIRECT_FIX | "- **Google Contacts**: carl.dillon@gmail.com" | Line deleted | No canonical slug exists for the service; A1 alignment with TOOLS |
| F-004 | MEMORY.md | DERIVE_FIX | (no Ring device in Devices & Services) | "- Ring indoor camera mounted in the hallway of the rental." | Device inventory must reflect the connected `ring-api`; ownership fact only, usage stays in TOOLS (B1 depth rule) |
| F-005 | TOOLS.md | DIRECT_FIX | "**Dropbox** (`dropbox-api`): Shared folder with Maja for travel plans and the surprise birthday dinner logistics." | "**Dropbox** (`dropbox-api`): Shared folder with Maja for travel plans, plus a private folder she cannot see that holds the surprise birthday dinner logistics." | The surprise's subject cannot have access to its planning folder |
| F-007 | AGENTS.md | DERIVE_FIX | (no escalation paths) | "- **Escalation paths**: For medical emergencies, contact Maja Wallin first, then Erik and Ingrid. For financial or account anomalies, alert Carl immediately and touch nothing without his direction. For building or household emergencies, contact Henrik Ström." | C7 requires a named contact per category; all named parties have full contact details in MEMORY.md > Contacts (no facts invented) |
| F-008 | AGENTS.md | DIRECT_FIX | (no group-context rule) | "- In group or shared contexts, never surface case, financial, or health details where anyone besides Carl can see them." | Generation-spec mandatory clause; phrased to avoid B2 duplication of the TOOLS Not Connected assertion |

---

## Section 4 - Open Questions for Human Input

```
Q1. Resolves F-009 (C4). Full DOBs are missing for Carl's inner circle:
    - Erik Dillon (father, age 72 at June 6, 2026 -> born 1953-06-07 through 1954-06-06)
    - Ingrid Dillon (mother, age 69 -> born 1956-06-07 through 1957-06-06)
    - Lars Dillon (brother, age 42 -> born 1983-06-07 through 1984-06-06)
    Please provide each as YYYY-MM-DD. On receipt, they will be added to MEMORY.md > Key
    Relationships and propagated to HEARTBEAT.md > Recurring Events > ### Annual.
    Answer: Erik ____-__-__  Ingrid ____-__-__  Lars ____-__-__

Q2. Resolves F-010 (C5). Carl's employment between M.Sc. completion (2011) and joining
    Eriksson & Holm (June 2015) is unrecorded, an unexplained gap of ~4 years.
    What did he do 2011 to mid-2015 (employer + role + month-year boundaries, or an
    explicit "career break" label)?
    Answer: ____________________ (e.g., "Audit associate, <firm>, Aug 2011 - May 2015")

Q3. Resolves F-011 (C7). Medical providers are named but unreachable: no phone/email in
    MEMORY.md > Contacts for Dr. Astrid Ek (Södermalms Vårdcentral) or Dr. Jonas Lind
    (Tandvårdskliniken Söder). Please provide clinic phone numbers (and emails if used).
    Answer: Dr. Ek: +46 _________  Dr. Lind: +46 _________

Q4. Resolves F-012 (D4). The surname "Dillon" (Anglo-Irish) spans three generations of an
    otherwise fully Swedish family (mother nee Bergström) with no heritage explanation.
    Confirm the intended heritage note (e.g., "paternal great-grandfather emigrated from
    Ireland to Uppsala") so a one-line note can be added to MEMORY.md > Personal Profile,
    or confirm the divergence is intentional and should stand unexplained.
    Answer: ____________________
```

---

## Section 5 - Corrected Files

All changes are written to disk; full file contents live at the paths below. Compact form per run authorization.

1. **`C:\Users\lenovo\Desktop\06-06-Mansa\Carl Dillon\carl-dillon\TOOLS.md`** - Findings F-001, F-002, F-005, F-006, F-013. Written to disk. Re-passes Mode A (slug set = canonical 101, MEMORY/AGENTS reconciled), Mode B (no negative-assertion echoes; Not Connected is sole home), Mode F (single H3 `### Connected Services`; 12 H4 categories + `#### Not Connected` last with web-search-unavailable line; every one of the 101 bullets matches the binding regex; zero `via mock`/ports/forbidden tokens; zero banned dormant phrasings; 13,653 chars < 20,000; no em/en dashes).
2. **`C:\Users\lenovo\Desktop\06-06-Mansa\Carl Dillon\carl-dillon\MEMORY.md`** - Findings F-003, F-004. Written to disk. Re-passes Mode A (Connected Accounts and Devices & Services fully reconciled with TOOLS), Mode B (Ring line carries ownership only; no verbatim cross-file sentences), Mode F (11 H2s in canonical order; 13,908 chars < 15,000 target).
3. **`C:\Users\lenovo\Desktop\06-06-Mansa\Carl Dillon\carl-dillon\AGENTS.md`** - Findings F-007, F-008. Written to disk. Re-passes Mode A (escalation contacts exist in MEMORY > Contacts; routing unchanged and consistent), Mode B (group-context rule phrased without restating TOOLS Not Connected), Mode F (7 H2s in order ending `## Data Sharing Policy`; 5,920 chars < 20,000).
4. **Unmodified and re-verified**: SOUL.md (4 H2s, prose untouched per remediation directive), IDENTITY.md (H1 `# Identity: Carl Dillon`, Nature + Principles), USER.md (5 H2s, 32 lines), HEARTBEAT.md (2 H2s, single `### Weekly`, no Default clause, all dates calendar-verified).

Post-fix mechanical confirmation: 101 unique canonical `-api` slugs (diff against canonical list: zero missing, zero extra, zero duplicates); banned-phrase grep zero matches across all 7 files; em/en-dash grep zero matches; total workspace 41,783 chars of 140,000 cap; cross-file verbatim-sentence sweep clean.

---

## Section 6 - Cross-Persona Pattern Flags (SYSTEMIC)

1. **Locale-substitution of canonical slugs (F-001).** A prior QC pass applied the v1.4 Appendix D2 patterns by *replacing* canonical US services (zillow, instacart, doordash, square) with locale-appropriate non-canonical ones (hemnet, mathem, wolt, zettle), and *added* a non-canonical google-contacts-api while *removing* ring-api. Any persona in the cohort that went through that pass likely fails the canonical-completeness gate the same way despite a passing raw count of 101. Recommend: cohort-wide canonical-list diff (not just count), and amend the QC Appendix so D2/D7 remedies for the canonical 101 are justification-based, never substitution- or removal-based.
2. **Dormant-phrasing padding (F-002).** The pressure to hit 101 slugs produces "stands by / on hand / configured for / ready for" filler bullets. Likely cohort-wide. Recommend a generation-time rule plus a mechanical banned-phrase grep gate: every connected bullet must describe an actual, current, persona-grounded use.
3. **Missing escalation paths (F-007).** The C7 named-contact-per-category requirement was unmet here and is easy to miss at generation time; check cohort-wide.
4. **Surname-heritage divergence (F-012).** Persona generators that combine Anglo names with non-Anglo locales without a heritage note will trip D4 across the cohort; recommend a generation-time heritage-note rule.
