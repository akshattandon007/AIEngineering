# 🤖 AI Concepts for Product Managers
### A Plain-English Guide · *Based on "AI Engineering: Building Applications with Foundation Models"*

---

## 📚 Table of Contents
- [Part 1: Core AI Concepts](#part-1-core-ai-concepts-explained-simply)
- [Part 2: Use Case Flash Cards](#part-2-use-case-flash-cards)
- [Part 3: PM Decision Framework](#part-3-pm-decision-framework)

---

# Part 1: Core AI Concepts Explained Simply

> Each concept includes: **what it means**, a plain-English analogy, and a real product example.

---

## 1. Language Model

| | |
|---|---|
| **What it means** | A computer program that has read enormous amounts of text and learned patterns in language — so it can predict what word or phrase comes next, given some context. |
| **Think of it like** | *A very well-read autocomplete. Like your phone's keyboard that suggests the next word, but trained on billions of books, articles, and websites instead of just your texts.* |
| **Real example** | Gmail's Smart Compose suggests "I hope you're well" after you type "Hi Sarah," because it has learned that phrase commonly follows a greeting in work emails. |

---

## 2. Token

| | |
|---|---|
| **What it means** | The smallest chunk of text an AI processes. Not always a full word — it could be part of a word, a punctuation mark, or a whole short word. **100 tokens ≈ 75 words.** |
| **Think of it like** | *Like how a cashier counts items at a supermarket checkout — they don't count each ingredient inside a tin, just the unit on the conveyor belt. Tokens are AI's "units".* |
| **Real example** | The word `can't` becomes two tokens: `can` and `'t`. So "I can't wait to build AI apps" = 9 tokens, not 9 words. This matters for pricing — most AI APIs charge per token. |

> 💡 **PM Tip:** API costs are calculated per token. A typical customer support message might be ~200 tokens. Understanding this helps you estimate costs accurately when pitching AI features to your finance team.

---

## 3. Vocabulary (of a model)

| | |
|---|---|
| **What it means** | The complete set of tokens a model knows about. Think of it as the model's "dictionary". GPT-4 knows 100,256 different tokens. A model can only work with text made up of tokens it knows. |
| **Think of it like** | *Like a Scrabble set — you can only make words from the tiles in the bag. More tiles (bigger vocabulary) = more flexibility in what you can express.* |
| **Real example** | Mixtral (open source) has a 32,000-token vocabulary. GPT-4 has 100,256. Bigger vocabulary = better at handling technical jargon, foreign languages, and unusual words — relevant if your product serves niche industries. |

---

## 4. Generative AI

| | |
|---|---|
| **What it means** | AI that can **CREATE** new content — text, images, code, audio — rather than just classifying or sorting existing content. It produces open-ended outputs that didn't exist before. |
| **Think of it like** | *Traditional AI is like a multiple-choice test (pick A, B, C or D). Generative AI is like an open essay question — the model writes its own answer from scratch, and the answer is different every time.* |
| **Real example** | ChatGPT generating a personalised marketing email vs. a spam filter (traditional AI) that just labels your email as "spam" or "not spam". Both are AI — only ChatGPT is generative. |

---

## 5. Completion / Prompt-Completion Model

| | |
|---|---|
| **What it means** | The core mechanic of language models: you give it text (the **prompt**) and it completes it. Almost everything AI does — answering questions, translating, summarising — is secretly a completion task in disguise. |
| **Think of it like** | *Like filling in the blank on a sentence. You write: "The capital of France is ___" and the model completes it. Even a full conversation is really just a very long fill-in-the-blank.* |
| **Real example** | Prompt: `"Is this email likely spam? Email: [email text]. Answer:"` — The model completes with `"Likely spam."` Suddenly your LLM is a spam classifier, built with zero additional training. |

> 💡 **PM Tip:** Almost any task you want AI to do can be framed as a prompt. Before asking engineers to build a complex ML pipeline, first try writing a clear prompt. It often works surprisingly well.

---

## 6. Probabilistic Outputs *(Why AI isn't always consistent)*

| | |
|---|---|
| **What it means** | AI doesn't look up the "right" answer — it calculates the **most probable next word** based on patterns in its training. This means the same question can get slightly different answers each time, and it can sometimes be confidently wrong. |
| **Think of it like** | *Like asking a very well-read person to guess the next word in a sentence. They're usually right, but they're making an educated guess — not looking up a fact. Sometimes they guess wrong, sometimes brilliantly.* |
| **Real example** | Ask ChatGPT `"What is 2+2?"` ten times — you'll get `"4"` every time (high probability). Ask `"Write me a tagline for my coffee shop"` ten times — you'll get ten different answers. This is a feature, not a bug, for creative tasks. |

> 💡 **PM Tip:** This is why AI outputs need human review for high-stakes decisions (medical, legal, financial). Design your product with a "human in the loop" for anything where a confident wrong answer could cause harm.

---

## 7. Self-Supervision *(How AI learns without humans labelling data)*

| | |
|---|---|
| **What it means** | A clever training trick: instead of paying humans to label millions of examples, the AI creates its own "exam questions" from raw text. For every sentence, it hides one word and tries to guess it — using the surrounding text as clues. |
| **Think of it like** | *Like a student who studies by covering up answers and quizzing themselves. Every sentence in every book becomes a practice question automatically, with no teacher needed.* |
| **Real example** | From the sentence `"I love street food."` the AI creates 6 free training examples: it tries to predict `I` from nothing, then `love` from `I`, then `street` from `I love`, and so on. Billions of sentences = trillions of free lessons. |

> 💡 **PM Tip:** This is WHY AI models can be so capable — they've essentially read and practised with most of the internet. It's also why data quality matters: garbage in, garbage out.

---

## 8. Supervision vs Self-Supervision

| | Traditional (Supervised) AI | Modern AI (Self-Supervised) |
|---|---|---|
| **How it learns** | Humans manually label examples (e.g. "this photo = cat") | AI creates its own labels from raw text automatically |
| **Data cost** | Expensive — $0.05 per image; $50K for 1 million images | Near zero — uses text that already exists online |
| **Scale limit** | Can only scale as fast as humans can label | Unlimited — train on billions of web pages |
| **PM implication** | Used for specific, narrow tasks (fraud detection, image tags) | Powers general assistants like ChatGPT |
| **Example product** | Google Photos recognising your friends' faces | ChatGPT writing your product specs |

---

## 9. Foundation Model

| | |
|---|---|
| **What it means** | A very large AI model trained on massive amounts of data that can be adapted for many different tasks. It's called a "foundation" because you **build on top of it** rather than starting from scratch each time. |
| **Think of it like** | *Like a Swiss Army knife vs. a single-purpose tool. An old-school AI was a single knife (just for cheese). A foundation model is the whole Swiss Army knife — you pick which tool to use depending on your task.* |
| **Real example** | GPT-4 (OpenAI), Claude (Anthropic), and Gemini (Google) are all foundation models. A company can take GPT-4 and adapt it to be a customer support bot, a code assistant, or a legal document summariser — all from the same base model. |

---

## 10. Multimodal Model

| | |
|---|---|
| **What it means** | An AI that can understand and work with **more than one type of input** — for example, both text AND images in the same conversation. "Multi" = many. "Modal" = type of data. |
| **Think of it like** | *Like a person who can both read a document AND look at a diagram to understand a problem — rather than only being able to read text or only look at pictures.* |
| **Real example** | You upload a photo of your product's dashboard and ask "What's wrong with this UX?" — a multimodal model like GPT-4V or Claude 3 can actually see the image and give you feedback. A text-only model couldn't. |

> 💡 **PM Tip:** Multimodal capabilities unlock new product features: photo-based customer support ("here's a photo of my broken device"), visual search, accessibility tools. Ask your team which model supports images if your use case involves visuals.

---

## 11. Parameters *(Why model size matters to you as a PM)*

| | |
|---|---|
| **What it means** | Parameters are the millions or billions of internal settings inside a model — think of them as the model's "memory". **More parameters = bigger capacity to learn.** Bigger models are generally smarter but cost more to run. |
| **Think of it like** | *Like a brain with more neural connections. A mouse brain has fewer connections than a human brain — so it can learn simpler things. More connections = more complexity you can handle.* |
| **Real example** | GPT-1 (2018): 117 million parameters. GPT-4 (estimated): 100+ billion parameters. A smaller model like Mistral 7B is cheaper to run and good for simple tasks. Bigger isn't always better — choose based on your task complexity and budget. |

### Quick guide: Which model size for which PM scenario?

| Scenario | Model Size to Consider | Why |
|---|---|---|
| Internal FAQ bot for 10 employees | Small (7B params) | Simple Q&A — cheap to run, fast |
| Customer support chatbot (millions of users) | Medium (70B params) | Needs nuance + reliability at scale |
| Legal document analysis | Large (100B+ params) | Complex reasoning required |
| Generating product descriptions | Small–Medium | Creative but not highly complex |
| Medical diagnosis support | Large + human review | High stakes — accuracy critical |

---

## 12. The 3 Ways to Adapt an AI Model to Your Product

> This is the most important thing a PM needs to understand — you rarely build from scratch. You take an existing model and adapt it one of three ways:

| Method | What it is | Analogy | Cost / Effort | When to use it |
|---|---|---|---|---|
| **Prompt Engineering** | Write better instructions to the AI. No code changes, no model changes. | Giving a new employee very clear instructions before their first day | 🟢 Low — days to weeks. No engineering needed | Starting point for everything. Good for 80% of use cases. |
| **RAG** *(Retrieval-Augmented Generation)* | Connect the AI to YOUR data. AI looks up relevant info before answering. | Giving the employee access to your company wiki before they answer a question | 🟡 Medium — weeks. Needs some engineering | When AI needs to know YOUR specific data: policies, products, customer history. |
| **Finetuning** | Retrain the model on your specific examples to change its behaviour. | Sending the employee on a specialist training course tailored to your business | 🔴 High — months + data. Needs ML engineers | When prompt engineering and RAG aren't enough. For very specific tone or style. |

> 💡 **PM Tip:** Always start with prompt engineering — it's free and fast. Only invest in RAG or finetuning if prompt engineering clearly isn't giving you the quality you need. The "last mile" from good to great can take months — budget for it.

---

## 13. Training Jargon Decoded

> When engineers and vendors use these terms, here's what they actually mean:

| Term | Plain English | PM Implication |
|---|---|---|
| **Pre-training** | Building the model from the ground up, training it on all of the internet. Takes months, costs millions. Done by companies like OpenAI, Anthropic, Google. | You will almost never do this. It's for AI labs only. Your job is to pick the right pre-trained model. |
| **Fine-tuning** | Taking a pre-trained model and giving it extra training on YOUR specific data to change how it behaves. Like sending a new hire on a specialist course. | You might do this after 6–12 months of using the base model, when you have enough data and a clear quality gap to close. |
| **Post-training** | What model companies do after pre-training to make the model safer and more helpful. This is how ChatGPT learned to be polite and follow instructions. | Handled by the model provider (OpenAI, Anthropic). Affects the model's tone, safety guardrails, and instruction-following. |
| **Prompt Engineering** *(NOT training)* | Writing better instructions to the model in plain text. No model weights are changed. People sometimes incorrectly call this "training". | This is what your team should start with. Fast, cheap, reversible. **Start here always.** |

---

## 14. Hallucination — The #1 PM Risk to Understand

| | |
|---|---|
| **What it means** | When an AI **confidently states something that is factually wrong**. It's not lying — it genuinely doesn't know it's wrong. It's predicting what sounds plausible based on patterns, not looking things up in a database. |
| **Think of it like** | *Like a student who didn't study but writes a very confident-sounding essay. The grammar is perfect, the tone is authoritative, but half the facts are made up.* |
| **Real example** | A customer asks your AI bot "What's your return policy?" and instead of saying "I don't know", the AI invents a policy that sounds plausible but is wrong. Customer acts on it. You have a legal and trust problem. |

> 💡 **PM Tip:** Mitigate hallucination with RAG (connect AI to your actual data) and always build in human review for high-stakes outputs. Design your product so the AI says "I'm not sure" rather than guessing. Position AI as a "helpful assistant" not an "oracle".

---

## 15. Inference *(and why it affects your product speed)*

| | |
|---|---|
| **What it means** | Inference = the model **generating an answer in real time** when a user asks something. Every time your product calls the AI, that's an inference. Faster inference = snappier product. Cheaper inference = better margins. |
| **Think of it like** | *Like a chef cooking a meal to order (inference) vs. a factory pre-making 10,000 meals (training). Inference is the on-demand part — it happens every time a user uses your product.* |
| **Real example** | GPT-4 might take 3–5 seconds to generate a long response. Newer, smaller, optimised models might do it in under 1 second. For a live customer chat feature, 5 seconds feels very slow — so model choice directly affects perceived product quality. |

> 💡 **PM Tip:** Always measure **TTFT (Time to First Token)** — how quickly does the first word appear? Even if the full response takes 5 seconds, showing the first word in 0.5 seconds feels much faster to users. Streaming responses dramatically improve perceived speed.

---

# Part 2: Use Case Flash Cards

> Each card covers: **what it is**, **when your product should use it**, and a **real-world example**.

---

## 🖥️ Use Case 1 — AI Coding Assistant

| | |
|---|---|
| **What is it?** | AI that helps developers write, review, document, and test code. It reads your codebase and suggests completions, fixes bugs, and writes docs. |
| **When to use?** | When your users are developers, or when you want to speed up your own engineering team. Best ROI for documentation (**+45–50% faster**) and code generation (**+35–45% faster**). Less useful for highly complex architectural decisions (<10% improvement). |
| **Real world example** | GitHub Copilot crossed $100M annual revenue in 2 years. Your dev team could write documentation 2× faster today by enabling Copilot in their IDE. If you're building a developer tool, a coding assistant is table stakes. |

---

## 💬 Use Case 2 — Customer Support Chatbot

| | |
|---|---|
| **What is it?** | An AI bot that handles customer questions automatically — 24/7, instantly, at a fraction of the cost of human agents. Can handle FAQs, policy questions, order status, and route complex issues to humans. |
| **When to use?** | When you have high volume, repetitive support tickets. Start with internal tools first (62% of companies deploy internal-facing apps before external). Go external once you've hit >90% accuracy on common queries. Always keep a human escalation path. |
| **Real world example** | A retailer deploys a chatbot for "Where's my order?" questions (60% of all tickets). Human agents now only handle complaints and complex cases. Response time drops from 4 hours to 30 seconds. CSAT improves because simple queries get instant answers. |

---

## ✍️ Use Case 3 — Writing Assistant

| | |
|---|---|
| **What is it?** | AI that helps users write better, faster. Can draft emails, blog posts, marketing copy, reports, performance reviews — and edit or improve existing text. |
| **When to use?** | When writing is a core part of your users' workflow. Particularly powerful for sales teams (cold outreach), marketing (copy generation), and managers (performance reviews, internal comms). Also great for non-native English speakers. |
| **Real world example** | MIT study: ChatGPT cut writing time by **40%** and improved quality by **18%** for 453 professionals. Workers were 2× more likely to keep using it after the experiment. HubSpot and Salesforce now have built-in AI writing for outreach emails. |

---

## 📄 Use Case 4 — Document Q&A / Talk-to-Your-Docs *(RAG)*

| | |
|---|---|
| **What is it?** | Upload a document (contract, policy, report, manual) and ask questions about it in plain English. The AI reads the document and answers based only on what's in it — no hallucination from general knowledge. |
| **When to use?** | When users need to extract information from long, dense documents. Ideal for legal teams (contracts), HR (policy questions), finance (reports), customer support (product manuals). Use RAG to ground answers in real data. |
| **Real world example** | A legal team uploads a 200-page supplier contract and asks "What are the termination clauses?" — gets the answer in 10 seconds instead of spending 2 hours reading. An HR chatbot answers "How many sick days do I get?" by reading the actual employee handbook. |

---

## 🎨 Use Case 5 — Image & Video Generation

| | |
|---|---|
| **What is it?** | AI creates original images or videos from a text description. Useful for marketing materials, product visualisation, social media content, and rapid prototyping of visual ideas. |
| **When to use?** | When your product needs visual content at scale or speed. Best for marketing teams needing many ad variants, design prototyping, or social media content. Think "fast draft" not "final asset". NOT a replacement for brand photography or complex creative direction. |
| **Real world example** | A retailer uses AI to generate 50 product image variations for different seasons (summer vs winter backgrounds) in 1 hour instead of 1 week of photography. Midjourney: **$200M annual revenue** at just 18 months old. Adobe Firefly is now built into Photoshop. |

---

## 📊 Use Case 6 — Summarisation & Information Aggregation

| | |
|---|---|
| **What is it?** | AI reads long content (meeting transcripts, emails, Slack threads, research papers) and produces a concise summary with key points and action items. |
| **When to use?** | When information overload is a pain point for your users. **74% of generative AI users** already use it for this. Particularly valuable for executives, researchers, and anyone in information-heavy roles. Very low hallucination risk when grounded in provided content. |
| **Real world example** | Instacart's most popular internal AI prompt is "Fast Breakdown" — it summarises meeting notes, emails, and Slack conversations into facts, open questions, and action items, then auto-assigns tasks in Jira. Your PM team could summarise every user research interview in 30 seconds. |

---

## 🎓 Use Case 7 — Education & Personalised Learning

| | |
|---|---|
| **What is it?** | AI acts as a tutor — explaining concepts, generating practice questions, providing feedback, and adapting content to the learner's pace and style. |
| **When to use?** | When your product needs to teach something. B2B: onboarding, compliance training, upskilling. B2C: language learning, exam prep, skills training. Most powerful for **personalisation** — same content, different learning styles. |
| **Real world example** | Duolingo uses AI most heavily for lesson personalisation. Khan Academy's "Khanmigo" is an AI tutor for students. Chegg lost **93% of its stock value** ($28 → $2) as students switched from homework help to ChatGPT — showing AI's disruption of this space is already happening. |

---

## ⚙️ Use Case 8 — Workflow Automation & AI Agents

| | |
|---|---|
| **What is it?** | AI that doesn't just answer questions — it **takes actions**. Books things, fills forms, sends emails, updates systems. An "agent" is an AI that can plan multi-step tasks and use tools to complete them. |
| **When to use?** | When your product involves repetitive multi-step processes. Think: lead generation, data entry, scheduling, research compilation. Still early stage — works well for well-defined tasks. Always include human review before irreversible actions. |
| **Real world example** | An AI agent for a sales team: given a list of prospects, it researches each one online, drafts a personalised outreach email, and adds it to the CRM — in minutes instead of hours. Your PM team could automate competitor tracking by having an agent monitor news and summarise weekly. |

---

# Part 3: PM Decision Framework

> Key questions to ask before building any AI feature.

---

## Before your next AI feature discussion, ask these 5 questions:

### ❓ 1. Does AI need to be CRITICAL or COMPLEMENTARY?

| | |
|---|---|
| **Critical** | The feature doesn't work without AI (e.g. real-time translation). Requires a much higher accuracy bar. Design for failure if you choose this path. |
| **Complementary** | The product works fine without it (e.g. Smart Compose in Gmail). More forgiving of mistakes — users can simply ignore bad suggestions. |
| **PM implication** | The more critical AI is to the application, the more accurate and reliable it must be. Start complementary; earn the right to go critical. |

---

### ❓ 2. Is this REACTIVE or PROACTIVE?

| | |
|---|---|
| **Reactive** | AI responds when a user asks something (e.g. chatbot). Usually needs low latency. More forgiving of errors because users asked for it. |
| **Proactive** | AI acts without being asked (e.g. Google Maps traffic alert). Can be precomputed. **Higher quality bar** — users didn't ask for it, so errors feel intrusive. |
| **PM implication** | Proactive features need to earn their place. If the signal isn't strong, don't show it. A noisy proactive AI quickly gets ignored or turned off. |

---

### ❓ 3. What is our USEFULNESS THRESHOLD?

| | |
|---|---|
| **Define it measurably** | "Automates 60% of tickets" or "Users rate responses 4+/5" or "Reduces handle time by 30%". |
| **Don't launch below it** | A bad AI experience is worse than no AI. It erodes trust and is hard to recover from. |
| **PM implication** | Set the threshold before you build. Tie it to your business metric. Don't let engineers or executives pressure you to ship before you hit it. |

---

### ❓ 4. Have we planned for the LAST MILE?

| Stage | Time | Reality |
|---|---|---|
| 0% → 80% quality | ~1 month | Fast — base models are impressive out of the box |
| 80% → 95% quality | ~4+ months | Disproportionately hard — hallucinations, edge cases, trust issues |
| Each subsequent 1% gain | Gets slower | Discouraging — budget for this explicitly |

> 💡 **PM Tip:** LinkedIn took 1 month to reach 80% of the experience they wanted, then 4 *more* months to reach 95%. Budget for the long tail — it's where most of the real work lives.

---

### ❓ 5. What is our HUMAN-IN-THE-LOOP strategy?

| Stage | What it means | When to use |
|---|---|---|
| 🐛 **CRAWL** | All AI outputs reviewed by humans before being acted on | Starting out, or for high-stakes outputs |
| 🚶 **WALK** | AI handles internal workflows autonomously | Once accuracy is proven internally |
| 🏃 **RUN** | AI interacts directly with external users | Only after earning trust at Walk stage |

> **Start at Crawl. Earn the right to Run by proving accuracy at each stage.**

---

## ⭐ Key Takeaway

> *It's easy to build a cool AI demo. It's hard to build a reliable AI product.*
>
> Your job as a PM is to bridge that gap — with **clear metrics**, **realistic timelines**, and the **right human oversight**.
