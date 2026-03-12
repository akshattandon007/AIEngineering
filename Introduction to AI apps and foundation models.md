# 🤖 AI Engineering — Study Notes
### *Building Applications with Foundation Models*

> 📖 **Source:** *AI Engineering: Building Applications with Foundation Models* by **Chip Huyen** (O'Reilly Media)
> Chapters 1 & 2 — Notes for aspiring AI Engineers

---

## 📚 Table of Contents

- [Chapter 1: Introduction to AI Engineering](#chapter-1-introduction-to-building-ai-applications-with-foundation-models)
  - [1.1 From Language Models → LLMs → Foundation Models](#11-from-language-models--llms--foundation-models)
  - [1.2 Why AI Engineering Exploded: 3 Key Factors](#12-why-ai-engineering-exploded-3-key-factors)
  - [1.3 Foundation Model Use Cases](#13-foundation-model-use-cases)
  - [1.4 Planning an AI Application](#14-planning-an-ai-application--key-questions-to-ask)
  - [1.5 The AI Engineering Stack](#15-the-ai-engineering-stack)
- [Chapter 2: Understanding Foundation Models](#chapter-2-understanding-foundation-models)
  - [2.1 Training Data](#21-training-data)
- [📖 Glossary](#-quick-reference-glossary)
- [✅ Action Checklist](#-action-checklist-for-aspiring-ai-engineers)

---

# Chapter 1: Introduction to Building AI Applications with Foundation Models

## 1. The Big Picture: What is AI Engineering?

If you had to describe post-2020 AI in one word, that word would be **scale**. AI models powering ChatGPT, Google Gemini, and Midjourney are consuming a non-trivial portion of the world's electricity — and we're on track to run out of public internet data to train them.

> ### 🔑 Two Key Consequences of Scaling
>
> 1. AI models are becoming more powerful → enabling more applications
> 2. Training large models requires massive data, compute & talent → only a few orgs can do it
>
> → This gave rise to **"Model as a Service"**: use powerful models via API without building your own

The result: demand for AI applications shot up while the barrier to building them collapsed. This created **AI Engineering** — the fastest-growing engineering discipline.

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 1–2*

---

## 1.1 From Language Models → LLMs → Foundation Models

### Language Models: The Basics

| Term | Definition |
|------|-----------|
| **Language Model** | Encodes statistical information about language — tells us how likely a word is to appear in a given context. Think of it as a **completion machine**. |

Quick history: Claude Shannon's 1951 landmark paper *"Prediction and Entropy of Printed English"* introduced concepts (including entropy) still used in language modeling today.

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 3*

---

### 🪙 Tokens — The Basic Unit

A language model does not work with letters or full words — it works with **tokens**. A token can be a character, a word, or a part of a word (like `-tion`), depending on the model.

> ### 📌 Example: How GPT-4 Tokenises a Phrase
>
> **Phrase:** `"I can't wait to build AI applications"`
>
> **Tokens:** `I` | `can` | `'t` | `wait` | `to` | `build` | `AI` | `applic` | `ations` → **9 tokens**
>
> **Rule of thumb:** ~1 token ≈ ¾ of a word. So **100 tokens ≈ 75 words**.
>
> | Model | Vocabulary Size |
> |-------|----------------|
> | GPT-4 | 100,256 tokens |
> | Mixtral 8x7B | 32,000 tokens |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 3 (Figure 1-1)*

**Why tokens and not words?**

- Tokens break words into meaningful parts (e.g., `'cooking'` → `'cook'` + `'ing'`)
- Fewer unique tokens than unique words → smaller vocabulary → more efficient model
- Tokens help process unknown/made-up words (e.g., `'chatgpting'` → `'chatgpt'` + `'ing'`)

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 4*

---

### 🧠 Two Types of Language Models

| Feature | Masked LM (e.g. BERT) | Autoregressive LM (e.g. GPT) |
|---------|----------------------|------------------------------|
| **What it predicts** | Missing token ANYWHERE in a sequence | NEXT token using only preceding tokens |
| **Context used** | Both before AND after the masked token | Only tokens that came before |
| **Good for** | Classification, sentiment analysis, code debugging | Text generation, chat, writing |
| **Key example** | BERT (Devlin et al., 2018) | GPT-4, Claude, LLaMA |
| **Popular today?** | Less popular | **Dominant** — what most people mean by "LLM" |

```
Autoregressive LM:
"Why does the chicken cross the" → [prediction]
                Context: previous tokens only ↑

Masked LM:
"Why does the [prediction] cross the road"
         Context: surrounding tokens ↑ ↓
```
*Figure 1-2: Autoregressive vs Masked Language Models — Chip Huyen, AI Engineering, p. 5*

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 4–5 (Figure 1-2)*

---

> ### ⚡ Key Insight: Completion = Power
>
> A language model is a **COMPLETION MACHINE**. Given `"To be or not to be"`, it predicts `", that is the question."`
>
> This simple idea unlocks many tasks:
> - **Translation** → `"How are you in French is…"` → `"Comment ça va"`
> - **Spam detection** → `"Is this email spam? Answer:"` → `"Yes, likely spam"`
> - **Summarisation, coding, Q&A, maths** — all can be framed as completion tasks!

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 5–6*

---

### ⚙️ Self-Supervision: The Secret to Scale

Traditional ML needs labelled data, which is expensive. Language modelling is **self-supervised** — the model infers its own labels directly from the raw text.

**Example:** The sentence `"I love street food."` gives **6 training samples automatically:**

| Input (context) | Output (next token to predict) |
|----------------|-------------------------------|
| `<BOS>` | `I` |
| `<BOS>, I` | `love` |
| `<BOS>, I, love` | `street` |
| `<BOS>, I, love, street` | `food` |
| `<BOS>, I, love, street, food` | `.` |
| `<BOS>, I, love, street, food, .` | `<EOS>` |

*Table 1-1: Self-supervised training samples — Chip Huyen, AI Engineering, p. 7*

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 7 (Table 1-1)*

> ### 🔑 Why This Matters for Scale
>
> Text is **EVERYWHERE** — books, blogs, Reddit, Wikipedia, code repos.
>
> No labelling cost → unlimited training data → models can scale to **billions of parameters**.
>
> **This is why LLMs could exist at all!**

---

### 📏 Model Size & Parameters

| Term | Definition |
|------|-----------|
| **Parameter** | A variable inside an ML model that is updated during training. More params generally = more capacity to learn *(but not always)*. |

| Model | Year | Parameters | Status at the time |
|-------|------|-----------|-------------------|
| GPT-1 | June 2018 | 117 million | Considered "large" |
| GPT-2 | February 2019 | 1.5 billion | Made GPT-1 look "small" |
| GPT-4 (estimated) | 2023 | ~1 trillion (rumoured) | State of the art |
| Threshold today | 2024 | ~100 billion+ | Considered "large" |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 8*

> **💡 Note:** Bigger models need MORE data because they have more capacity to fill — training a huge model on a small dataset wastes compute. You could've achieved the same result with a smaller model.

---

### 🌐 From LLMs to Foundation Models

Language models are limited to text. But humans perceive the world through vision, audio, touch, etc. To operate in the real world, AI needs to go **multimodal**.

| Term | Definition |
|------|-----------|
| **Foundation Model** | A large-scale model (text + potentially image/audio/video) that can be used as a base ("foundation") for many downstream tasks. Examples: GPT-4, Claude 3, Gemini. |
| **Multimodal Model** | A model that can work with more than one data modality (e.g., text + images). Also called **LMM** (Large Multimodal Model). |

> ### 📌 How Multimodal Models Work
>
> ```
> Text tokens: "This is a"  ──┐
>                              ├──► Multimodal Model ──► Next token: "Puppy"
> Visual tokens: [🐶 image] ──┘
> ```
> *Figure 1-3: Multimodal model token generation — Chip Huyen, AI Engineering, p. 9*
>
> **OpenAI's CLIP (2021):** trained on **400 million** (image, text) pairs from the internet — zero manual labelling cost. This made CLIP the first model to generalise across multiple image classification tasks without extra training.

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 9–10 (Figure 1-3)*

Foundation models also mark the shift from **task-specific → general-purpose models**:

- ❌ **Old way:** a spam classifier ONLY does spam; a translation model ONLY translates
- ✅ **New way:** one foundation model can do spam classification AND translation AND coding AND maths

**Three techniques to adapt a foundation model to your needs:**

| Technique | What it does | Changes weights? |
|-----------|-------------|-----------------|
| **Prompt Engineering** | Give the model better instructions | ❌ No |
| **RAG** | Connect model to an external knowledge database | ❌ No |
| **Finetuning** | Continue training on your own dataset | ✅ Yes |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 11*

---

## 1.2 Why AI Engineering Exploded: 3 Key Factors

| Factor | What it means | Example |
|--------|--------------|---------|
| **1. General-purpose AI capabilities** | Foundation models can do MORE tasks than ever — including tasks previously impossible | AI now writes emails, generates images, writes code, synthesises training data |
| **2. Increased AI investment** | ChatGPT's success triggered massive investment. Cost of AI use cases dropped **100x** in 1 year (2022→2023) | Goldman Sachs: AI investment heading toward **$200B globally by 2025** |
| **3. Low entry barrier (Model as a Service)** | Models exposed via simple APIs — no infrastructure needed. Even non-coders can build AI apps | OpenAI, Anthropic, Mistral, Cohere all offer pay-per-use API access |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 12–14*

> ### 📊 How Fast is AI Engineering Growing?
>
> - **4 open-source AI tools** (AutoGPT, Stable Diffusion WebUI, LangChain, Ollama) got **more GitHub stars in 2 years** than Bitcoin accumulated in a decade
> - **LinkedIn (Aug 2023):** professionals adding "Generative AI" / "ChatGPT" / "Prompt Engineering" to their profiles grew an average of **75% per month**
> - **ComputerWorld declared:** *"Teaching AI to behave is the fastest-growing career skill"*

*Figure 1-6: GitHub star growth of AI engineering tools vs Bitcoin, Vue, React — Chip Huyen, AI Engineering, p. 15*

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 14 (Figure 1-6)*

---

## 1.3 Foundation Model Use Cases

The book analysed **205 open-source AI apps** (500+ GitHub stars) and **50 enterprise case studies**.

```
Distribution of AI Application Categories (n=205)
─────────────────────────────────────────────────
Coding                    ██████████████████ 30.4%
Conversational Bots       ████████████████  26.5%
Info Aggregation          ████████          12.7%
Image & Video Production  ████████          12.7%
Workflow Automation       ███████           11.3%
Writing                   ██                 3.4%
Education                 █                  1.5%
Data Organisation         █                  1.5%
```
*Figure 1-7: Use case distribution — Chip Huyen, AI Engineering, p. 19*

| Category | Consumer Examples | Enterprise Examples |
|----------|------------------|---------------------|
| **Coding** (30.4%) | Code completion, screenshot-to-code, AI commits | Automated testing, code migration, documentation |
| **Conversational Bots** (26.5%) | General chatbot, AI companion, therapy bot | Customer support, product copilots, NPC characters in games |
| **Info Aggregation** (12.7%) | Summarise websites, talk-to-your-docs | Market research, summarise Slack/emails, competitor tracking |
| **Image & Video** (12.7%) | Profile photo generation, photo editing | Ad generation, marketing visuals, design |
| **Workflow Automation** (11.3%) | Travel planning, event booking, form filling | Lead management, data extraction, invoicing |
| **Writing** (3.4%) | Email drafting, social posts, essay writing | Copywriting, SEO content, performance reports |
| **Education** (1.5%) | Tutoring, language learning (Duolingo) | Employee onboarding, training, quiz generation |
| **Data Organisation** (1.5%) | Image search, photo memex | Document processing, knowledge management |

*Table 1-3: Common generative AI use cases — Chip Huyen, AI Engineering, p. 18*

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 18 (Table 1-3, Figure 1-7)*

> ### 💡 Enterprise Deployment Pattern (a16z 2024 Research)
>
> Companies deploy **INTERNAL** apps first (lower risk):
>
> | Use Case | % Deployed to Production |
> |----------|-------------------------|
> | Text summarisation | **62%** |
> | Enterprise knowledge management | **60%** |
> | Customer service | 59% |
> | Marketing copy | 53% |
> | Software development | 53% |
> | Contract review | 45% |
> | External chatbot | 39% |
> | Recommendation algorithm | 39% |
>
> *Figure 1-8 — Chip Huyen, AI Engineering, p. 19*
>
> **Lesson:** If building for a company, **start with an internal tool** to prove value!

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 19 (Figure 1-8)*

---

## 1.4 Planning an AI Application — Key Questions to Ask

### Step 1: Should You Build It at All?

| Risk Level | Situation | Action |
|-----------|-----------|--------|
| 🔴 **Existential** | AI could make your business obsolete (e.g., document processing, financial analysis) | AI adoption must be **highest priority** — no choice |
| 🟡 **Opportunity** | AI can boost profits & productivity (most companies) | Build strategically — evaluate ROI carefully |
| 🟢 **Exploratory** | Unsure where AI fits but don't want to fall behind | Invest in R&D — experiment to learn (if budget allows) |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 29*

---

### Step 2: What Role Does AI Play?

- **Critical vs Complementary** — Is the app useless without AI (Face ID) or does AI just enhance it (Gmail Smart Compose)?
- **Reactive vs Proactive** — Does AI respond to user action (chatbot) or trigger itself opportunistically (Google Maps traffic alerts)?
- **Dynamic vs Static** — Is the model updated continuously per user (personalised) or updated periodically for all users?

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 30*

---

### Step 3: Human-in-the-Loop (Microsoft Crawl-Walk-Run Framework)

> ### 🚦 Microsoft's 3-Stage AI Automation Framework
>
> | Stage | Human Involvement | Example |
> |-------|-----------------|---------|
> | 🐛 **CRAWL** | Mandatory — AI only assists | AI suggests responses; human agent chooses which to send |
> | 🚶 **WALK** | AI interacts with internal employees | AI handles internal helpdesk tickets autonomously |
> | 🏃 **RUN** | Increased automation; AI talks to external users | AI responds to customers directly for simple requests |
>
> **Key:** Move from Crawl → Run gradually as quality improves (e.g., when 95% of AI suggestions are used verbatim by human agents)

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 31 (Microsoft, 2023)*

---

### ⚠️ The 'Last Mile' Problem — Critical Warning!

> ### ⚠️ Do NOT Underestimate the Gap Between Demo and Product
>
> **LinkedIn's real experience building an AI feature:**
>
> ```
> Month 1:        0% ──────────────────────────► 80%  ✅ Fast & easy
> Next 4 months: 80% ──────────────────────────► 95%  😰 BRUTALLY slow
> ```
>
> **Cause:** Edge cases, hallucinations, product kinks, evaluation overhead
>
> > *"The journey from 0 to 60 is easy; progressing from 60 to 100 is exceedingly challenging."*
> > — Ding et al., UltraChat (2023)
>
> **Plan for this. Budget 4–5x more time than your demo suggests.**

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 33–34*

---

## 1.5 The AI Engineering Stack

AI Engineering evolved out of ML Engineering. The stack has **three layers:**

```
┌─────────────────────────────────────────────────────────────────┐
│           LAYER 1: APPLICATION DEVELOPMENT                       │
│                  (Most active — last 2 years)                    │
│  ┌─────────────────────┐  ┌──────────────────────────────────┐  │
│  │  What it is         │  │  Responsibilities                │  │
│  │                     │  │  • Prompt engineering            │  │
│  │  Building apps on   │  │  • Context construction (RAG)    │  │
│  │  top of models via  │  │  • Evaluation                    │  │
│  │  prompts, RAG, eval │  │  • AI interface design           │  │
│  └─────────────────────┘  └──────────────────────────────────┘  │
├─────────────────────────────────────────────────────────────────┤
│                LAYER 2: MODEL DEVELOPMENT                        │
│  ┌─────────────────────┐  ┌──────────────────────────────────┐  │
│  │  What it is         │  │  Responsibilities                │  │
│  │                     │  │  • Modelling & training          │  │
│  │  Training, finetune,│  │  • Dataset engineering           │  │
│  │  dataset eng.,      │  │  • Inference optimisation        │  │
│  │  inference optim.   │  │  • Evaluation                    │  │
│  └─────────────────────┘  └──────────────────────────────────┘  │
├─────────────────────────────────────────────────────────────────┤
│     LAYER 3: INFRASTRUCTURE  (Most stable — core unchanged)      │
│  ┌─────────────────────┐  ┌──────────────────────────────────┐  │
│  │  What it is         │  │  Responsibilities                │  │
│  │                     │  │  • Model serving                 │  │
│  │  Serving, compute,  │  │  • Compute management            │  │
│  │  data, monitoring   │  │  • Data management               │  │
│  │                     │  │  • Monitoring                    │  │
│  └─────────────────────┘  └──────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
```
*Figure 1-14: Three layers of the AI engineering stack — Chip Huyen, AI Engineering, p. 38*

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 37–38 (Figure 1-14)*

---

### ⚔️ AI Engineering vs Traditional ML Engineering — Key Differences

| Area | Traditional ML Engineering | AI Engineering |
|------|---------------------------|----------------|
| **Model source** | Build your own model from scratch | Use someone else's pre-trained model (API or open source) |
| **Main focus** | Modelling, training, feature engineering | Model adaptation, prompt engineering, evaluation |
| **ML knowledge required?** | Yes — must understand gradient descent, architectures etc. | Nice-to-have, no longer mandatory to start |
| **Model size & compute** | Smaller models, lower inference cost | Bigger models, higher latency & cost → inference optimisation critical |
| **Outputs** | Usually close-ended (classification, regression) | Open-ended (free text, images) → evaluation is MUCH harder |
| **Dataset engineering** | Feature engineering on tabular data | Deduplication, tokenisation, context retrieval, quality control |
| **Workflow order** | `Data → Model → Product` | `Product → Data → Model` (iterate fast!) |

*Tables 1-4 & 1-6 — Chip Huyen, AI Engineering, p. 43 & 46*

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 39–43 (Tables 1-4, 1-6)*

---

### 🏷️ Training Terminology — Know the Difference!

> ### Pre-training vs Finetuning vs Post-training
>
> | Term | What happens | Who does it | Resources needed |
> |------|-------------|-------------|-----------------|
> | **Pre-training** | Train from scratch — weights randomly initialised. For InstructGPT: uses ~**98% of all compute & data**! | OpenAI, Anthropic, Google, Meta… | 🔴 Extreme — weeks/months |
> | **Finetuning** | Continue training a pre-trained model. Weights from previous run. | Application developers (you!) | 🟡 Moderate |
> | **Post-training** | Everything after pre-training (SFT, RLHF, DPO). Makes model safe & helpful. | Model developers before release | 🟡 Moderate |
> | **Prompt Engineering** | NOT training! Teaching via context, not changing weights. | Anyone | 🟢 Zero |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 41–42*

---

### 🗺️ Model Adaptation Techniques — Quick Reference

| Technique | Changes weights? | Data needed | Complexity | When to use |
|-----------|-----------------|-------------|-----------|-------------|
| **Prompt Engineering** | ❌ No | 0 examples (zero-shot) to ~50 (few-shot) | 🟢 Low — **start here** | Always try first. Best for exploration. |
| **RAG** | ❌ No | Your own knowledge base/docs | 🟡 Medium | When model needs up-to-date or proprietary info |
| **Finetuning** | ✅ Yes | Hundreds to thousands of examples | 🔴 High | When prompt engineering hits a ceiling |

> 📖 *Chip Huyen, AI Engineering, Chapter 1, p. 40*

---

# Chapter 2: Understanding Foundation Models

To build AI applications effectively, you need a working mental model of what's happening inside foundation models. You don't need to implement one — but you **do** need to understand the design choices that affect your downstream applications.

> ### What Shapes a Model's Capabilities? (Chip Huyen's Framework)
>
> | # | Factor | Why it matters |
> |---|--------|---------------|
> | 1 | **Training Data** | What the model learned from → what it knows / doesn't know |
> | 2 | **Model Architecture** | Mostly transformer-based; shapes speed, context window, capabilities |
> | 3 | **Model Size** | More parameters ≠ always better; must balance capacity vs compute vs latency |
> | 4 | **Post-Training** | How the model was aligned to be helpful, safe, and follow instructions |
> | 5 | **Sampling** | How the model *chooses* its output from all possible options — **hugely underrated!** |

> 📖 *Chip Huyen, AI Engineering, Chapter 2, p. 49–50*

---

## 2.1 Training Data

> *"An AI model is only as good as the data it was trained on."* — Chip Huyen

| Data Source | What it is | Quality concern |
|-------------|-----------|----------------|
| **Common Crawl** | Nonprofit crawls 2–3 billion web pages/month. Free and massive. | ⚠️ Low quality — clickbait, fake news, propaganda, racist content |
| **C4** (Colossal Clean Crawled Corpus) | Google's cleaned subset of Common Crawl | Still contains low-trustworthiness media (NewsGuard data) |
| **Books / Papers** | High quality, formal writing, domain knowledge | Copyright issues; limited volume |
| **Code (GitHub)** | High-quality, structured, logical text | Licence issues; biased toward popular languages |
| **Wikipedia** | Factual, encyclopaedic, multilingual | Reflects Wikipedia's own biases and gaps |

> 📖 *Chip Huyen, AI Engineering, Chapter 2, p. 50 (Washington Post study on Common Crawl)*

> ### 🧠 Practical Implication for AI Engineers
>
> Understanding a model's training data tells you a LOT about its strengths and weaknesses:
>
> | If training data contains… | Then the model… |
> |---------------------------|----------------|
> | Heavy code corpus | ✅ Great at coding tasks |
> | Mostly English text | ⚠️ Poor on low-resource languages |
> | Knowledge cutoff date | ❌ Won't know about recent events |
> | Common Crawl heavily | ⚠️ May have absorbed misinformation |
>
> **This is why you must EVALUATE models on YOUR specific use case — don't just trust benchmarks!**

> 📖 *Chip Huyen, AI Engineering, Chapter 2, p. 50*

---

# 📖 Quick Reference Glossary

| Term | Definition |
|------|-----------|
| **AI Engineering** | Building applications on top of pre-trained foundation models. Focus on adaptation and evaluation rather than model building. |
| **Foundation Model** | A large-scale, general-purpose model trained on broad data that can be adapted to many tasks. Encompasses both LLMs and multimodal models. |
| **LLM** | Large Language Model — a very large autoregressive language model. Technically text-only, but often used loosely for any big AI model. |
| **Token** | The basic unit a language model processes. Roughly ¾ of a word on average. GPT-4 uses ~100,256 unique tokens. |
| **Self-supervision** | A training approach where labels are derived from the input data itself (no manual labelling needed). Critical for LLMs to scale. |
| **Parameter** | A variable in an ML model updated during training. More parameters generally = more capacity. *Not the same as tokens!* |
| **Prompt Engineering** | Adapting a model's behaviour through carefully crafted input instructions — without changing model weights. |
| **RAG** | Retrieval-Augmented Generation — connecting a model to an external knowledge source to supplement its context. |
| **Finetuning** | Continuing to train a pre-trained model on new data to specialise it for a task. Changes model weights. |
| **Pre-training** | Training a model from scratch on massive data. Extremely resource-intensive. Done by very few organisations. |
| **Post-training** | Training done after pre-training — e.g. instruction tuning, RLHF. Makes models safe and easy to use. |
| **RLHF** | Reinforcement Learning from Human Feedback — a post-training technique where humans rate outputs to align the model. |
| **Inference** | Running a trained model to produce an output given an input. Cost and latency of inference is a major concern at scale. |
| **Hallucination** | When a model generates plausible-sounding but factually wrong output. Results from its probabilistic, completion-based nature. |
| **Autoregressive LM** | A language model that predicts the next token using only previous tokens. The dominant approach today (GPT, Claude, LLaMA). |
| **Masked LM** | A language model that predicts missing tokens using context from both sides (e.g., BERT). Better for classification tasks. |
| **Multimodal model** | A model that can work with multiple data types — e.g., both text and images (GPT-4V, Claude 3, Gemini). |
| **Model as a Service** | Business model where powerful models are exposed via API. Democratises access to AI without requiring own infrastructure. |
| **Generalisation** | A model's ability to perform well on unseen data / tasks it wasn't explicitly trained on. |
| **Benchmark** | A standardised test to evaluate model performance. Example: MMLU (Massive Multitask Language Understanding). |

> 📖 *All definitions: Chip Huyen, AI Engineering, Chapters 1–2*

---

# ✅ Action Checklist for Aspiring AI Engineers

### Before Building Anything

- [ ] Understand the difference between pre-training, finetuning, post-training, and prompt engineering
- [ ] Know your goal: are you doing application development (Layer 1) or model development (Layer 2)?
- [ ] Ask: can I solve this with prompt engineering alone before investing in finetuning?
- [ ] Always evaluate the base model first — it may already do 60–80% of what you need

### When Choosing a Model

- [ ] Understand what training data it was trained on — this reveals its strengths and blind spots
- [ ] Run your own evaluation on YOUR use case — don't just trust public benchmarks (they can be misleading)
- [ ] Check the tokeniser vocabulary — especially important for non-English or technical domains
- [ ] Consider: is this model well-aligned via post-training? Is it safe for your use case?

### When Scoping the Project

- [ ] Define usefulness threshold early: what quality level makes this worth deploying?
- [ ] Plan for the 'last mile': the gap from 80% → 95% quality takes **4–5x** more time than 0% → 80%
- [ ] Decide role of humans: **Crawl** (human in the loop) → **Walk** → **Run** (full automation)
- [ ] Think about product defensibility: what's your moat? Technology, data, or distribution?

### Technical Skills to Build Next

- [ ] **Prompt engineering:** structured instructions, chain-of-thought, few-shot examples *(Chapter 5)*
- [ ] **RAG fundamentals:** embeddings, vector databases, retrieval algorithms *(Chapters 4–6)*
- [ ] **Evaluation frameworks:** how to measure open-ended outputs reliably *(Chapter 3)*
- [ ] **Finetuning basics:** when and how to update model weights *(Chapter 7)*
- [ ] **Sampling & temperature:** understanding how models choose their outputs *(Chapter 2)*

---

> 📖 **All content sourced from:**
> *Chip Huyen, AI Engineering: Building Applications with Foundation Models (O'Reilly Media)*
