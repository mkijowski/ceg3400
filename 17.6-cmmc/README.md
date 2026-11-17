---
title: "CMMC Levels 1 and 2"
author: "Matt Kijowski"
date: 11/19/26
theme: "metropolis"
colortheme: "seahorse"
fonttheme: "professionalfonts"
---

# CEG 3400 : CMMC

\*Not the Roman numeral for 2000 (that is `MM`)

---

# CMMC

Today we are going to cover the following:

* Why CMMC exists
* FCI vs. CUI
* The three levels (we focus on 1 and 2)
* CMMC Level 1: basic cyber hygiene
* CMMC Level 2: what it adds
* Where the program stands right now (it moved... a lot)
* How it connects to risk and NICE

---

# Where we are

* **Risk** (NIST 800-30, CSF 2.0): *what* to protect and *how* to assess it
* **NICE** (SP 800-181): *who* does that work
* **CMMC**: ***prove it***

CMMC = ***Cybersecurity Maturity Model Certification***

The Department of Defense's way of checking that its contractors
actually protect the data it hands them.

---

# The honor system

The rules are not new, the ***checking*** is.

* **2017**: DFARS `252.204-7012` requires defense contractors to implement
  NIST SP 800-171 (110 security requirements)
* **2020**: DFARS `252.204-7019` requires contractors to post a
  self-assessment score in SPRS (Supplier Performance Risk System)
* Who calculated that score?

  The contractor.

* Who checked it?

  Mostly... nobody.

---

# Case study: Georgia Tech (2025)

Yes, a university.

* Two members of Georgia Tech's own ***cybersecurity team*** filed a
  whistleblower (qui tam) lawsuit in 2022
* Alleged: a research lab handling DoD data had no System Security Plan
  until at least 2020
* Alleged: GT submitted a campus-wide score of ***98 out of 110***
  that did not reflect the systems actually handling the data
* Settled September 2025: ***$875,000*** under the False Claims Act
  (no admission of liability)

No breach required. Saying you were secure when you were not was enough.

---

# Who does CMMC apply to?

The ***Defense Industrial Base*** (DIB): roughly 220,000 companies.

* Not just Lockheed and Boeing
* The machine shop that makes one bracket for a jet
* The 12-person software shop subcontracting to a prime
* University research labs (see Georgia Tech)
* Lots of them right here around Wright-Patterson AFB

Note: you will see both ***DoD*** and ***DoW*** (Department of War, a
secondary name adopted in 2025). Same department.

---

# Two kinds of data

Everything in CMMC hinges on ***what data*** you have.

* **FCI**: Federal Contract Information
  * Non-public info provided by or generated for the government under a contract
  * Example: the contract details, delivery schedules, internal emails about the work
* **CUI**: Controlled Unclassified Information
  * Sensitive, but ***not*** classified; requires safeguarding by law or policy
  * Example: engineering drawings, export-controlled technical data

FCI → Level 1. CUI → Level 2.

---

# The three levels

| | **Level 1** | **Level 2** | **Level 3** |
|---|---|---|---|
| Protects | FCI | CUI | CUI (high-value) |
| Requirements | 15 | 110 | 110 + 24 |
| Source | FAR `52.204-21` | SP 800-171 r2 | + SP 800-172 |
| Assessed by | Self | Self or C3PAO | Gov't (DIBCAC) |
| How often | Yearly | Every 3 years | Every 3 years |

Each level is a ***superset*** of the one below it.

Level 3 is for a small fraction of contractors, we will not cover it in depth.

---

# How did we get here?

* **2020**: CMMC 1.0, ***five*** levels, third-party assessment for everyone
  * Industry: "this will cost too much"
* **2021**: CMMC 2.0 announced, collapsed to ***three*** levels
* **Dec 2024**: program rule finalized (`32 CFR Part 170`)
* **Nov 10, 2025**: acquisition rule (DFARS) takes effect, Phase 1 begins
* **Jul 2026**: Phase 2 suspended (more on this later)

Compliance frameworks are policy, and policy moves with cost and politics.

---

# CMMC Level 1

***Basic cyber hygiene***

* 15 requirements, copied straight from FAR `52.204-21`
* Six families (two-letter codes come from NIST 800-171)
* Applies to anyone handling FCI, which is a ***lot*** of contractors

The good news: you already know almost all of this.

---

# Level 1 requirements (1/2)

**Access Control** (`AC`)

* Limit system access to authorized users, processes, and devices
* Limit users to the transactions and functions they are allowed to do
* Verify and control connections to external systems
* Control information posted on publicly accessible systems

**Identification & Authentication** (`IA`)

* Identify users, processes, and devices
* Authenticate them before granting access

**Media Protection** (`MP`)

* Sanitize or destroy media containing FCI before disposal or reuse

---

# Level 1 requirements (2/2)

**Physical Protection** (`PE`)

* Limit physical access to authorized individuals
* Escort visitors, keep access logs, manage keys/badges/locks

**System & Communications Protection** (`SC`)

* Monitor and protect communications at system boundaries
* Separate publicly accessible systems from internal networks (DMZ)

**System & Information Integrity** (`SI`)

* Identify and fix flaws in a timely manner (patching)
* Malicious code protection, kept up to date
* Run periodic and real-time scans of files and systems

---

# Level 1: you have seen this before

| Family | Where we covered it |
|---|---|
| `AC` | Permissions, Firewalls |
| `IA` | Authentication, Passwords |
| `MP` | Hashing / Encryption (and a hammer) |
| `PE` | Risk: Threat Accessibility (physical) |
| `SC` | Networking, Firewalls |
| `SI` | Malware, Vulnerability Taxonomies (CVEs) |

Level 1 is not hard. It is the ***minimum*** for touching government data.

---

# Level 1 assessment

* **Self-assessment**, every year
* Results posted in ***SPRS***
* A senior company official signs an ***annual affirmation***
* All-or-nothing: every requirement must be ***MET***
* ***No*** POA&Ms (Plan of Action & Milestones, i.e. "we will fix it later")

Question for you: why allow zero exceptions at the lowest level?

---

# CMMC Level 2

***Protecting CUI***

* All 110 requirements of NIST SP 800-171 ***Rev. 2***
* 14 families (Level 1's six, plus eight new ones)
* 320 ***assessment objectives*** (from NIST SP 800-171A), the things an
  assessor actually checks
* Level 1's 15 requirements are all in here

Going from 15 to 110 is not just more of the same, it is a different
kind of program.

---

# Level 2: requirements by family

::: columns

:::: column

| Family | L1 | L2 |
|---|---|---|
| `AC` Access Control | 4 | 22 |
| `AT` Awareness & Training | | 3 |
| `AU` Audit & Accountability | | 9 |
| `CM` Configuration Mgmt | | 9 |
| `IA` Ident. & Auth. | 2 | 11 |
| `IR` Incident Response | | 3 |
| `MA` Maintenance | | 6 |

::::

:::: column

| Family | L1 | L2 |
|---|---|---|
| `MP` Media Protection | 1 | 9 |
| `PS` Personnel Security | | 2 |
| `PE` Physical Protection | 2 | 6 |
| `RA` Risk Assessment | | 3 |
| `CA` Security Assessment | | 4 |
| `SC` Sys. & Comms Prot. | 2 | 16 |
| `SI` Sys. & Info Integrity | 4 | 7 |

::::

:::

Total: 15 → 110

---

# The eight new families (1/2)

| Family | What it adds | Where we saw it |
|---|---|---|
| `AT` | Security awareness training | Social engineering |
| `AU` | Logging and log review | Intrusion detection |
| `CM` | Baselines, inventory | Risk: Inventory |
| `IR` | Incident response capability | Mat Honan IR plan |

---

# The eight new families (2/2)

| Family | What it adds | Where we saw it |
|---|---|---|
| `MA` | Controlled system maintenance | |
| `PS` | Screening and offboarding | Insider threats |
| `RA` | Risk assessments, vuln scans | ***Lab 6*** |
| `CA` | Test your controls, SSP, POA&M | |

Level 1 is ***technical controls***. Level 2 adds ***process***.

---

# Level 2 brings paperwork

* **System Security Plan (SSP)**
  * Describes the system boundary, what is in it, and ***how*** each of the
    110 requirements is met
  * No SSP? An assessment cannot even start
* **Plan of Action & Milestones (POA&M)**
  * Documented gaps, with a plan and a deadline to fix them
* **Scoping**: which assets actually touch CUI?
  * Everything that processes, stores, or transmits CUI is in scope
  * Many companies build a small CUI ***enclave*** to shrink the scope

Remember from Risk: *you cannot protect what you do not know you have.*

---

# Level 2 scoring

Not pass/fail, it is a ***score***.

* Start at ***110***
* Subtract ***1, 3, or 5*** points for each requirement not met,
  weighted by how bad the gap is
  * Missing multifactor authentication: -5
* Lowest possible score: ***-203***

To get ***Conditional*** status:

* Score of at least ***88*** (80%)
* Only certain low-weight items allowed on a POA&M
* POA&Ms closed and re-assessed within ***180 days***, or status expires

---

# Try it

***Your Name Inc.*** has a Level 2 assessment. The assessor finds:

* Two 5-point requirements not met
* One 3-point requirement not met
* Four 1-point requirements not met

What is the score?

  110 - 10 - 3 - 4 = ***93***

Do you get Conditional status?

  ***No.*** The score is above 88, but the 5- and 3-point gaps
  cannot go on a POA&M. Fix those first.

---

# Who does the assessment?

Level 2 has two flavors, the contract says which:

* **Level 2 (Self)**: you assess yourself, post to SPRS, affirm annually
* **Level 2 (C3PAO)**: a ***Certified Third-Party Assessment Organization***
  assesses you
  * C3PAOs are authorized by ***The Cyber AB*** (the CMMC accreditation body)
  * Valid for 3 years, plus annual affirmations

The third-party option is the whole point of CMMC:

***trust, but verify***.

---

# One version behind

* NIST published SP 800-171 ***Rev. 3*** in May 2024
  * Restructured, reworded, and closer to NIST SP 800-53
* CMMC still requires ***Rev. 2***
  * DoD issued a class deviation to stay on Rev. 2

Standards move faster than regulations.

If you work in this space, always check ***which revision*** the contract cites.

---

# The rollout plan

Four phases, one year apart:

| Phase | Start | What it adds |
|---|---|---|
| 1 | Nov 10, 2025 | L1 and L2 ***self***-assessments |
| 2 | Nov 10, 2026 | L2 ***C3PAO*** default for CUI |
| 3 | Nov 10, 2027 | Level 3, option periods |
| 4 | Nov 10, 2028 | Full implementation |

Notice anything about the Phase 2 date?

---

# Status (as of November 2026)

Phase 2 did ***not*** happen last week.

* **Jul 13, 2026**: DoD suspends Phase 2 and all later phases, citing
  cost and burden on contractors
* A ***CMMC Reform Task Force*** runs a 60-day review with an industry RFI
* **Sep 3, 2026**: a class deviation makes the suspension binding:
  contracting officers remove third-party assessment requirements
* Task force review closed in September; recommendations have not been
  made public

The program is ***paused in Phase 1***, not cancelled.

---

# What did NOT change

* Level 1 (Self) and Level 2 (Self) requirements are still in contracts
* DFARS `252.204-7012` still requires NIST SP 800-171 Rev. 2
* SPRS scores and annual affirmations are still required
* False Claims Act liability for inaccurate scores still applies
  (remember Georgia Tech)

The 110 controls are still the law of the land for CUI.

What got paused is the ***independent check***.

---

# Back to risk

From the DoD's point of view, CMMC ***is*** risk management:

* **Asset**: CUI scattered across 220,000 companies
* **Vulnerability**: contractors with weak security
* **Threat**: nation-state adversaries targeting the weakest link
* **Response**: ***mitigate*** by making controls a condition of the contract

Remember from NICE: supply chain risk got its own Work Role
(***Cybersecurity Supply Chain Risk Management***).

CMMC is supply chain risk management at the scale of an entire industry.

---

# Back to NICE: this is a job

CMMC created a whole workforce, mostly in ***Oversight & Governance*** (`OG`):

* **Compliance analysts**: write SSPs, track POA&Ms, prepare for assessments
* **Assessors**: Cyber AB credentials
  * ***CCP***: Certified CMMC Professional
  * ***CCA***: Certified CMMC Assessor
* **Engineers** (`IO`, `PD`): build the enclave, deploy MFA, logging, FIPS crypto

Lots of these jobs are within 20 miles of this classroom.

---

# Questions for you

* Is ***Your Name Inc.*** Level 1 ready?
  Which of the 15 requirements would you fail today?
* Which Lab 6 findings would map to Level 2 families?
* Was suspending third-party assessments the right risk decision?
  * Argue it from the ***DoD's*** side
  * Argue it from a ***12-person subcontractor's*** side

---

# What do we get out of all this?

1. Compliance frameworks are the ***risk tolerance*** of the party holding
   the purse strings, written down as requirements.
2. Level 1 = 15 hygiene controls for FCI, Level 2 = all 110 of
   NIST 800-171 for CUI, plus the process to prove it.
3. The controls are mostly things you already know from this course.
4. Frameworks change. Always check the date, the revision, and the status.
