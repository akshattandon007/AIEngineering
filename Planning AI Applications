# 🗺️ Planning AI Applications — Structured Step-by-Step Guide

> 📖 **Source:** *AI Engineering: Building Applications with Foundation Models* by **Chip Huyen** (O'Reilly Media, Chapter 1, p. 28–35)

---

## 📋 Table of Contents

- [Overview: The Complete Planning Flow](#-overview-the-complete-planning-flow)
- [Phase 1 — Use Case Evaluation](#phase-1--use-case-evaluation-should-you-build-this)
- [Phase 2 — Buy or Build?](#phase-2--buy-or-build)
- [Phase 3 — Define the Role of AI & Humans](#phase-3--define-the-role-of-ai--humans-in-the-application)
- [Phase 4 — Setting Expectations & Metrics](#phase-4--setting-expectations--metrics)
- [Phase 5 — Milestone Planning](#phase-5--milestone-planning)
- [Phase 6 — Maintenance Planning](#phase-6--maintenance-planning)
- [Complete End-to-End Decision Map](#-complete-end-to-end-decision-map)

---

## 🔭 Overview: The Complete Planning Flow

> There are **6 sequential phases** to planning an AI application properly.
> Most people skip to Phase 5. Don't be most people.

```mermaid
flowchart TD
    START([🚀 You have an AI application idea]) --> P1

    P1["📋 PHASE 1\nUse Case Evaluation\nShould you build this at all?"]
    P2["🛒 PHASE 2\nBuy or Build?\nDo you have to build it yourself?"]
    P3["🤝 PHASE 3\nDefine Role of AI & Humans\nHow does AI fit into the product?"]
    P4["📏 PHASE 4\nSet Expectations & Metrics\nWhat does success look like?"]
    P5["🪜 PHASE 5\nMilestone Planning\nHow do you get there step by step?"]
    P6["🔧 PHASE 6\nMaintenance Planning\nHow do you keep it running & improving?"]

    P1 --> P2 --> P3 --> P4 --> P5 --> P6

    P6 --> LAUNCH([✅ Ship & Iterate])

    style START fill:#1a3c5e,color:#fff,stroke:#1a3c5e
    style LAUNCH fill:#375623,color:#fff,stroke:#375623
    style P1 fill:#2e75b6,color:#fff,stroke:#2e75b6
    style P2 fill:#2e75b6,color:#fff,stroke:#2e75b6
    style P3 fill:#2e75b6,color:#fff,stroke:#2e75b6
    style P4 fill:#2e75b6,color:#fff,stroke:#2e75b6
    style P5 fill:#2e75b6,color:#fff,stroke:#2e75b6
    style P6 fill:#2e75b6,color:#fff,stroke:#2e75b6
```

---

## Phase 1 — Use Case Evaluation: Should You Build This?

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 29*
>
> *"If you're doing this for a living, it might be worthwhile to take a step back and consider why you're building this."*

The first question is not *how* to build — it's *why*. Every AI project starts from one of three motivations, each with a different urgency level.

```mermaid
flowchart TD
    START([💡 AI application idea]) --> Q1{"Does AI pose an\nexistential threat\nto your business?"}

    Q1 -- "Yes — competitors with AI\ncould make you obsolete" --> EXIST["🔴 EXISTENTIAL RISK\n\nIndustries: document processing,\nfinancial analysis, insurance,\nadvertising, web design, writing"]
    EXIST --> ACT1["⚡ Highest priority action\nAI adoption is non-negotiable.\nStart NOW — no ROI debate needed.\n\nRef: 7% of Gartner 2023 survey\ncited 'business continuity'"]

    Q1 -- "No" --> Q2{"Does AI offer a clear\nopportunity to boost\nprofits or productivity?"}

    Q2 -- "Yes — can improve\noperations meaningfully" --> OPP["🟡 OPPORTUNITY\n\nUse cases: user acquisition,\ncustomer retention, sales leads,\nmarket research, internal comms"]
    OPP --> ACT2["📊 Build strategically\nEvaluate ROI carefully.\nPrioritise high-impact, lower-risk\nuse cases first (e.g. internal tools)"]

    Q2 -- "Not sure yet" --> Q3{"Can you afford to\nexperiment and\nnot fall behind?"}

    Q3 -- "Yes — budget for R&D" --> EXPLORE["🟢 EXPLORATORY\n\nGoal: build AI engineering\nexpertise before you need it"]
    EXPLORE --> ACT3["🔬 Invest in R&D\nAssign a small team to experiment.\nAvoid chasing every hype cycle.\nLearn what's feasible for your domain."]

    Q3 -- "No — too resource constrained" --> WAIT["⏸️ Monitor & Wait\nTrack AI developments.\nRevisit in 3–6 months.\nDon't build just to be seen as 'AI'."]

    ACT1 --> NEXT([➡️ Proceed to Phase 2])
    ACT2 --> NEXT
    ACT3 --> NEXT
    WAIT --> DONE([🔚 Pause project])

    style START fill:#1a3c5e,color:#fff
    style EXIST fill:#c00000,color:#fff
    style OPP fill:#c55a11,color:#fff
    style EXPLORE fill:#375623,color:#fff
    style WAIT fill:#7f7f7f,color:#fff
    style ACT1 fill:#fce4e4,color:#000
    style ACT2 fill:#fef3e2,color:#000
    style ACT3 fill:#e2efda,color:#000
    style NEXT fill:#375623,color:#fff
    style DONE fill:#595959,color:#fff
```

### Phase 1 Summary Table

| Risk Level | Trigger | Urgency | Example Industries |
|-----------|---------|---------|-------------------|
| 🔴 **Existential** | AI could make your core business obsolete | Immediate — no debate | Document processing, financial analysis, insurance, advertising |
| 🟡 **Opportunity** | AI can meaningfully boost profits or productivity | High — build strategically | Most businesses — sales, support, content, operations |
| 🟢 **Exploratory** | Don't want to be left behind like Kodak / Blockbuster | Moderate — R&D budget | Large enterprises with dedicated R&D teams |
| ⏸️ **Wait** | Too resource-constrained and no immediate threat | Low — monitor | Early-stage startups, resource-constrained teams |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 29*

---

## Phase 2 — Buy or Build?

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 29–30*
>
> *"Once you've found a good reason to develop this use case, you might consider whether you have to build it yourself."*

```mermaid
flowchart TD
    START([✅ Confirmed: we need AI for this use case]) --> Q1{"Is this use case\nCORE to your\nbusiness / product?"}

    Q1 -- "Yes — competitive\ndifferentiator" --> Q2{"Does an off-the-shelf\nsolution already exist\nthat meets your needs?"}

    Q2 -- "No good solution exists" --> BUILD["🔨 BUILD in-house\n\nReason: AI is a core competitive moat.\nYou cannot outsource your differentiation."]

    Q2 -- "Yes, but it's owned\nby a competitor" --> BUILD2["🔨 BUILD in-house\n\nReason: Giving a competitor access\nto your core workflow is too risky."]

    Q2 -- "Yes — neutral vendor,\ngood fit" --> EVAL["🔍 Evaluate the vendor\nDoes it meet quality, latency,\ncost, privacy & compliance needs?"]

    EVAL -- "Meets all requirements" --> BUY["🛒 BUY / Use existing solution\n\nFaster to market.\nLower upfront cost.\nFocus your team on differentiation."]

    EVAL -- "Gaps exist" --> HYBRID["🔀 HYBRID\nBuy base capability,\nbuild custom layer on top.\nCommon pattern: use model API\n+ build your own prompt/RAG layer"]

    Q1 -- "No — peripheral /\nsupporting function" --> Q3{"Can an off-the-shelf\ntool handle this well\nenough?"}

    Q3 -- "Yes" --> BUY
    Q3 -- "No" --> HYBRID

    BUILD --> NEXT
    BUILD2 --> NEXT
    BUY --> NEXT
    HYBRID --> NEXT

    NEXT([➡️ Proceed to Phase 3])

    style START fill:#1a3c5e,color:#fff
    style BUILD fill:#c55a11,color:#fff
    style BUILD2 fill:#c55a11,color:#fff
    style BUY fill:#375623,color:#fff
    style HYBRID fill:#2e75b6,color:#fff
    style NEXT fill:#375623,color:#fff
    style EVAL fill:#fef3e2,color:#000
```

> **Key insight from the book:** The low entry barrier to AI is a *double-edged sword*. If it's easy for you to build, it's easy for competitors too. Ask yourself: what's your **moat**? Is it technology, proprietary data, or distribution?

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 31–32*

---

## Phase 3 — Define the Role of AI & Humans in the Application

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 30–31*
>
> This phase has **two parallel decisions** to make: (A) the product role of AI, and (B) the level of human involvement.

### 3A — What is AI's Role in the Product?

```mermaid
flowchart TD
    START([🤖 Defining AI's product role]) --> D1 & D2 & D3

    D1{"Is the app functional\nwithout AI?"}
    D1 -- "No — AI is essential" --> CRITICAL["🎯 CRITICAL\n\nAI must have very high\naccuracy & reliability.\nFace ID, fraud detection.\nZero tolerance for failure."]
    D1 -- "Yes — AI enhances it" --> COMP["🔧 COMPLEMENTARY\n\nAI adds value but isn't core.\nUsers accept occasional errors.\nGmail Smart Compose, autocorrect."]

    D2{"When does AI\nshow its output?"}
    D2 -- "In response to\nuser action" --> REACTIVE["💬 REACTIVE\n\nMust be fast — low latency.\nChatbots, search, code completion.\nUser expects immediate response."]
    D2 -- "Proactively, when\nopportunity arises" --> PROACTIVE["📣 PROACTIVE\n\nCan be precomputed.\nHigher quality bar — user didn't ask.\nTraffic alerts, smart suggestions.\nWrong suggestions feel intrusive."]

    D3{"How often is the\nmodel updated?"}
    D3 -- "Continuously — adapts\nto each user" --> DYNAMIC["🔄 DYNAMIC\n\nPersonalised per user.\nFace ID adapts as face changes.\nChatGPT memory feature.\nMore complex to build & maintain."]
    D3 -- "Periodically — one model\nfor all users" --> STATIC["📸 STATIC\n\nOne shared model, updated\nwhen new version is ready.\nSimpler to deploy & monitor."]

    CRITICAL & COMP --> NOTE1["📝 Impacts: quality threshold,\nerror tolerance, evaluation rigor"]
    REACTIVE & PROACTIVE --> NOTE2["📝 Impacts: latency budget,\nprecomputation strategy"]
    DYNAMIC & STATIC --> NOTE3["📝 Impacts: infrastructure,\npersonalisation, model versioning"]

    NOTE1 & NOTE2 & NOTE3 --> NEXT([➡️ Proceed to 3B: Human Role])

    style START fill:#1a3c5e,color:#fff
    style CRITICAL fill:#c00000,color:#fff
    style COMP fill:#2e75b6,color:#fff
    style REACTIVE fill:#c55a11,color:#fff
    style PROACTIVE fill:#375623,color:#fff
    style DYNAMIC fill:#7030a0,color:#fff
    style STATIC fill:#595959,color:#fff
    style NEXT fill:#375623,color:#fff
```

### 3B — The Human-in-the-Loop Decision (Microsoft Crawl-Walk-Run)

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 31 — citing Microsoft (2023)*

```mermaid
flowchart TD
    START([🤝 How much should humans be involved?]) --> Q1{"How confident are you\nin the AI's quality\nright now?"}

    Q1 -- "Low confidence —\nstill evaluating" --> CRAWL

    subgraph CRAWL ["🐛 CRAWL — Human involvement is mandatory"]
        C1["AI generates suggestions\nonly — humans review & decide"]
        C2["Example: AI drafts customer\nreply, human agent approves\nbefore sending"]
        C3["Measure: What % of AI\nsuggestions do humans accept?"]
    end

    Q1 -- "Moderate confidence —\nworks well internally" --> WALK

    subgraph WALK ["🚶 WALK — AI interacts with internal employees"]
        W1["AI handles tasks for\ninternal users autonomously"]
        W2["Example: AI answers\nemployee HR/IT queries directly"]
        W3["Measure: Employee satisfaction,\nerror rate, escalation rate"]
    end

    Q1 -- "High confidence —\nconsistently meets bar" --> RUN

    subgraph RUN ["🏃 RUN — Increased automation with external users"]
        R1["AI interacts with\nexternal customers directly"]
        R2["Example: AI resolves\ncustomer support tickets autonomously"]
        R3["Measure: CSAT, resolution rate,\nescalation to human rate"]
    end

    CRAWL -- "Acceptance rate > 90–95%\n→ Ready to progress" --> WALK
    WALK -- "Error rate acceptable\n→ Ready to progress" --> RUN
    RUN -- "Quality degrades\nor new risk found" --> CRAWL

    CRAWL & WALK & RUN --> NEXT([➡️ Proceed to Phase 4])

    style START fill:#1a3c5e,color:#fff
    style NEXT fill:#375623,color:#fff
```

> **Rule of thumb:** If 95% of AI-suggested responses to simple requests are used by human agents verbatim → consider letting AI respond directly to those request types.

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 31*

---

## Phase 4 — Setting Expectations & Metrics

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 32–33*
>
> *"The most important metric is how this will impact your business."*

```mermaid
flowchart TD
    START([📏 Define what success looks like]) --> BIZ

    BIZ["📊 Step 1: Define BUSINESS metrics\nWhat is the commercial impact?"]

    BIZ --> BIZ1["Automation rate\nWhat % of tasks should AI handle?"]
    BIZ --> BIZ2["Throughput\nHow many more requests can you process?"]
    BIZ --> BIZ3["Speed\nHow much faster is response time?"]
    BIZ --> BIZ4["Labour saved\nHow much human effort is replaced?"]
    BIZ --> BIZ5["User satisfaction\nCSSAT score, NPS, feedback sentiment"]

    BIZ1 & BIZ2 & BIZ3 & BIZ4 & BIZ5 --> THRESH

    THRESH["🎯 Step 2: Define USEFULNESS THRESHOLD\nHow good must the system be before\nyou'll put it in front of users?"]

    THRESH --> Q1["🔍 Quality metrics\nIs the output accurate, relevant, safe?\nHard to measure for open-ended outputs\n— needs human eval or LLM-as-judge"]
    THRESH --> Q2["⚡ Latency metrics\n• TTFT: Time to First Token\n• TPOT: Time Per Output Token\n• Total end-to-end latency\nContext: if humans respond in 1hr,\nanything faster may be good enough"]
    THRESH --> Q3["💰 Cost metrics\nCost per inference request.\nCost per 1,000 users.\nBudget ceiling for API spend."]
    THRESH --> Q4["⚖️ Other metrics\nFairness, interpretability,\ncompliance, privacy, safety"]

    Q1 & Q2 & Q3 & Q4 --> BASELINE

    BASELINE["📐 Step 3: Evaluate BASE MODEL first\nTest an off-the-shelf model on your use case.\nWhere does it land vs your usefulness threshold?"]

    BASELINE --> COMP{"How does the base model\nperform vs your threshold?"}

    COMP -- "Already meets\nor exceeds threshold" --> LOW["🟢 Low effort needed\nPrompt engineering\nmay be sufficient"]
    COMP -- "Partially meets\n(e.g. 30–60% of target)" --> MED["🟡 Moderate effort needed\nPrompt engineering + RAG\nor light finetuning"]
    COMP -- "Far below threshold\n(e.g. 0–30% of target)" --> HIGH["🔴 High effort needed\nFinetuning or custom\nmodel development\nRevisit ROI case"]

    LOW & MED & HIGH --> REVISE{"Do the effort estimates\nchange your decision\nto build?"}

    REVISE -- "Yes — too much effort\nfor the return" --> ABANDON["🚫 Abandon / Descope\nthe project"]
    REVISE -- "No — still worth it" --> NEXT([➡️ Proceed to Phase 5])

    style START fill:#1a3c5e,color:#fff
    style THRESH fill:#2e75b6,color:#fff
    style BASELINE fill:#2e75b6,color:#fff
    style NEXT fill:#375623,color:#fff
    style ABANDON fill:#c00000,color:#fff
    style LOW fill:#e2efda,color:#000
    style MED fill:#fef3e2,color:#000
    style HIGH fill:#fce4e4,color:#000
    style BIZ fill:#d5e8f0,color:#000
```

### Metrics Quick Reference

| Metric Category | What to measure | Example targets |
|----------------|----------------|-----------------|
| **Quality** | Accuracy, relevance, safety, hallucination rate | >90% correctness on eval set |
| **Latency — TTFT** | Time to first token (streaming perception) | <500ms for chat interfaces |
| **Latency — TPOT** | Time per output token | <50ms/token |
| **Latency — Total** | End-to-end response time | <5s for most use cases |
| **Cost** | Per-request API / compute cost | <$0.01 per customer interaction |
| **Automation rate** | % of tasks AI handles without human | >60% for support chatbot |
| **User satisfaction** | CSAT, NPS, thumbs up/down | CSAT >4.0/5.0 |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 32–33*

---

## Phase 5 — Milestone Planning

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 33–34*
>
> *"It might take a weekend to build a demo but months, and even years, to build a product."*

```mermaid
flowchart TD
    START([🪜 Build the roadmap to your target]) --> M1

    M1["🔬 Milestone 1: Baseline Evaluation\nTest off-the-shelf model on your use case.\nRecord current performance score."]
    M1 --> GAP{"What is the gap between\nbaseline and your\nusefulness threshold?"}

    GAP -- "Small gap\n< 20 points" --> M2A
    GAP -- "Medium gap\n20–50 points" --> M2B
    GAP -- "Large gap\n> 50 points" --> M2C

    M2A["🔧 Milestone 2A: Prompt Engineering Sprint\n1–2 weeks\nExperiment with instructions,\nfew-shot examples, chain-of-thought.\nNo code changes to model."]

    M2B["🔧 Milestone 2B: Prompt Engineering + RAG\n2–6 weeks\nAdd retrieval layer with your\nknowledge base / documents.\nBuild eval pipeline."]

    M2C["🔧 Milestone 2C: Finetuning\n4–12 weeks\nCurate training dataset.\nFiNetune model on your domain.\nRequires labelled examples."]

    M2A & M2B & M2C --> M3

    M3["📊 Milestone 3: Hit 60–80% of target\n⚠️ WARNING: This will feel fast.\nDo NOT assume the rest will be equally fast.\nThe last mile is 4–5x harder."]

    M3 --> LASTMILE

    subgraph LASTMILE ["⚠️ The Last Mile Problem — Budget carefully"]
        LM1["0% → 80% of target\nRelatively fast\n(days to weeks)"]
        LM2["80% → 95% of target\nBRUTALLY slow\n(weeks to months)\n\nCauses:\n• Edge cases & rare inputs\n• Hallucinations\n• Evaluation overhead\n• Product kinks\n• Conflicting requirements"]
        LM1 --> LM2
    end

    LASTMILE --> M4["🚀 Milestone 4: Reach Usefulness Threshold\nConduct final evaluation.\nGet sign-off from stakeholders.\nDeploy to limited users first (shadow mode / A-B test)."]

    M4 --> M5["📈 Milestone 5: Production Rollout\nMonitor business metrics.\nCollect user feedback.\nSet up feedback loop for continuous improvement."]

    M5 --> NEXT([➡️ Proceed to Phase 6: Maintenance])

    style START fill:#1a3c5e,color:#fff
    style M3 fill:#c55a11,color:#fff
    style M4 fill:#375623,color:#fff
    style M5 fill:#375623,color:#fff
    style NEXT fill:#375623,color:#fff
    style LM1 fill:#e2efda,color:#000
    style LM2 fill:#fce4e4,color:#000
    style M2A fill:#d5e8f0,color:#000
    style M2B fill:#fef3e2,color:#000
    style M2C fill:#fce4e4,color:#000
```

### The Last Mile — Time Budget Reality Check

| Stage | Typical Time | Feel |
|-------|-------------|------|
| 0% → 60% | Days to 1–2 weeks | 🟢 Fast & exciting — demo ready |
| 60% → 80% | 2–4 weeks | 🟡 Slowing down — edge cases appear |
| 80% → 90% | 4–8 weeks | 🔴 Grinding — each % gain is hard-won |
| 90% → 95% | 8–16 weeks | 🔴 Very slow — hallucinations, rare inputs dominate |
| 95% → 99% | Months+ | 🔴 May require model retraining or architecture changes |

> *"LinkedIn found it took one month to achieve 80% of the experience — then four more months to get to 95%."*
> — Chip Huyen, AI Engineering, Chapter 1, p. 33–34

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 33–34*

---

## Phase 6 — Maintenance Planning

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 34–35*
>
> *"Building on top of foundation models today means committing to riding this bullet train."*

```mermaid
flowchart TD
    START([🔧 Your product is live — now what?]) --> CAT

    CAT["Changes in the AI landscape fall into 3 categories"]
    CAT --> GOOD & HARD & FATAL

    subgraph GOOD ["🟢 GOOD CHANGES — Mostly positive, but still require action"]
        G1["📈 Model outputs improving\n→ Opportunity: switch to better model\n→ Risk: outputs behave differently, re-evaluate"]
        G2["💰 Inference costs dropping\n→ Opportunity: serve more users at lower cost\n→ Risk: in-house model you built now more expensive than API"]
        G3["📏 Context windows growing\n→ Opportunity: handle longer documents\n→ Risk: your RAG architecture may need rethinking"]
    end

    subgraph HARD ["🟡 HARD CHANGES — Significant adaptation needed"]
        H1["🔄 Model API changes / deprecations\n→ Action: monitor provider changelogs\n→ Mitigation: abstract model layer in your code"]
        H2["🏗️ New techniques emerge\n→ Action: run cost-benefit on each new approach\n→ Risk: best option today may be worst tomorrow"]
        H3["🌍 Regulatory changes (e.g. GDPR, AI Act)\n→ Action: legal review, compliance audit\n→ Cost: GDPR compliance estimated at $9B industry-wide"]
    end

    subgraph FATAL ["🔴 FATAL CHANGES — Existential risk to your product"]
        F1["⚖️ IP / copyright rulings against AI-generated content\n→ Action: track ongoing lawsuits\n→ Mitigation: use models with clear IP indemnification"]
        F2["🚫 Compute export restrictions / GPU bans\n→ Action: multi-cloud / multi-vendor strategy\n→ Risk: overnight supply chain disruption"]
        F3["📉 Model provider goes out of business\n→ Action: avoid single-vendor lock-in\n→ Mitigation: abstract API, have backup model ready"]
    end

    GOOD & HARD & FATAL --> STRATEGY

    STRATEGY["🛡️ Maintenance Strategy: How to stay resilient"]

    STRATEGY --> S1["📐 Abstract your model layer\nDon't hardcode one model's API.\nUse an abstraction so you can swap models\nwithout rewriting your whole app."]
    STRATEGY --> S2["🧪 Build a continuous eval pipeline\nAutomate regression tests.\nEvery model upgrade goes through eval\nbefore reaching production."]
    STRATEGY --> S3["📡 Monitor in production\nTrack quality, latency, cost metrics.\nSet up alerts for performance degradation.\nCollect user feedback signals."]
    STRATEGY --> S4["🔄 Build a feedback loop\nProduction data → improve prompts / RAG / model.\nThis is how you compound quality gains over time."]
    STRATEGY --> S5["📦 Version everything\nVersion your prompts, datasets, and model checkpoints.\nYou need to be able to roll back if something breaks."]

    S1 & S2 & S3 & S4 & S5 --> DONE([🔁 Continuous improvement cycle])

    style START fill:#1a3c5e,color:#fff
    style DONE fill:#375623,color:#fff
    style STRATEGY fill:#2e75b6,color:#fff
    style S1 fill:#d5e8f0,color:#000
    style S2 fill:#d5e8f0,color:#000
    style S3 fill:#d5e8f0,color:#000
    style S4 fill:#d5e8f0,color:#000
    style S5 fill:#d5e8f0,color:#000
```

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 34–35*

---

## 🗺️ Complete End-to-End Decision Map

> The full planning journey on a single flowchart — use this as a quick-reference map.

```mermaid
flowchart TD
    IDEA([💡 AI Application Idea]) --> EV

    subgraph EV ["PHASE 1 — Use Case Evaluation"]
        EV1{"Existential threat\nto business?"}
        EV1 -- Yes --> MUST["🔴 Must build — top priority"]
        EV1 -- No --> EV2{"Clear opportunity\nto grow or save?"}
        EV2 -- Yes --> SHOULD["🟡 Should build — evaluate ROI"]
        EV2 -- No --> EV3{"Afford to explore?"}
        EV3 -- Yes --> COULD["🟢 Could build — R&D mode"]
        EV3 -- No --> STOP1([🚫 Stop — not now])
    end

    MUST & SHOULD & COULD --> BB

    subgraph BB ["PHASE 2 — Buy or Build?"]
        BB1{"Core competitive\ndifferentiator?"}
        BB1 -- Yes --> BUILD["🔨 Build in-house"]
        BB1 -- No --> BB2{"Good vendor\nsolution exists?"}
        BB2 -- Yes --> BUY["🛒 Buy / Use API"]
        BB2 -- No --> HYBRID["🔀 Hybrid"]
    end

    BUILD & BUY & HYBRID --> ROLE

    subgraph ROLE ["PHASE 3 — Role of AI & Humans"]
        R1["Define: Critical vs Complementary"]
        R2["Define: Reactive vs Proactive"]
        R3["Define: Dynamic vs Static"]
        R4["Set automation level: Crawl → Walk → Run"]
        R1 --> R2 --> R3 --> R4
    end

    ROLE --> MET

    subgraph MET ["PHASE 4 — Set Expectations & Metrics"]
        M1["Define business metrics"]
        M2["Set usefulness threshold"]
        M3["Evaluate base model"]
        M4{"Gap acceptable?"}
        M1 --> M2 --> M3 --> M4
        M4 -- No --> STOP2([🚫 Abandon / Rescope])
        M4 -- Yes --> CONTINUE["✅ Proceed"]
    end

    MET --> MILE

    subgraph MILE ["PHASE 5 — Milestone Planning"]
        MS1["Start: Prompt engineering"]
        MS2["Add RAG if needed"]
        MS3["Finetune if needed"]
        MS4["⚠️ Hit 80% — do NOT celebrate yet"]
        MS5["Grind through last mile to 95%+"]
        MS1 --> MS2 --> MS3 --> MS4 --> MS5
    end

    MILE --> MAINT

    subgraph MAINT ["PHASE 6 — Maintenance"]
        MA1["Abstract model layer"]
        MA2["Continuous eval pipeline"]
        MA3["Production monitoring"]
        MA4["Feedback loop"]
        MA1 --> MA2 --> MA3 --> MA4
    end

    MAINT --> SHIP([🚀 Ship & Continuously Improve])

    style IDEA fill:#1a3c5e,color:#fff
    style STOP1 fill:#c00000,color:#fff
    style STOP2 fill:#c00000,color:#fff
    style SHIP fill:#375623,color:#fff
    style MUST fill:#c00000,color:#fff
    style SHOULD fill:#c55a11,color:#fff
    style COULD fill:#375623,color:#fff
    style BUILD fill:#2e75b6,color:#fff
    style BUY fill:#375623,color:#fff
    style HYBRID fill:#7030a0,color:#fff
    style CONTINUE fill:#375623,color:#fff
```

---

## 📝 Summary: The 6-Phase Planning Checklist

```
PHASE 1 — USE CASE EVALUATION
  ☐ Identify your motivation: Existential / Opportunity / Exploratory
  ☐ Validate the business case before writing a single line of code
  ☐ Ask: what happens if a competitor builds this and you don't?

PHASE 2 — BUY OR BUILD?
  ☐ Determine if AI is a core competitive differentiator
  ☐ Survey existing vendors and open-source models
  ☐ Assess defensibility: technology moat, data moat, or distribution moat

PHASE 3 — ROLE OF AI & HUMANS
  ☐ Classify: Critical vs Complementary
  ☐ Classify: Reactive vs Proactive
  ☐ Classify: Dynamic vs Static
  ☐ Set initial automation level: start at CRAWL, plan path to RUN

PHASE 4 — EXPECTATIONS & METRICS
  ☐ Define business metrics (automation rate, speed, cost, CSAT)
  ☐ Set a clear usefulness threshold before building
  ☐ Evaluate the base model first — record the baseline score
  ☐ Revisit the ROI case if the gap is too large

PHASE 5 — MILESTONE PLANNING
  ☐ Start with prompt engineering (fastest, cheapest)
  ☐ Add RAG if model needs external / proprietary knowledge
  ☐ Plan finetuning only if prompt engineering + RAG aren't enough
  ☐ Budget 4–5x more time for the last 20% of quality improvement
  ☐ Do not demo to stakeholders at 80% and promise 100% in 2 weeks

PHASE 6 — MAINTENANCE
  ☐ Abstract your model layer — avoid hard lock-in to one provider
  ☐ Build a continuous evaluation pipeline from day one
  ☐ Set up production monitoring (quality, latency, cost)
  ☐ Design a feedback loop so production data improves the system
  ☐ Version prompts, datasets, and model checkpoints
  ☐ Track regulatory developments in your region / industry
```

---

> 📖 **All content sourced from:**
> *Chip Huyen, AI Engineering: Building Applications with Foundation Models — Chapter 1, p. 28–35 (O'Reilly Media)*
