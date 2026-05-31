# Indonesian LLM Evaluation Report
## Code-Switching Stress Test: Indonesian ↔ English

**A focused stress-test evaluation of 6 large language models on bidirectional Indonesian–English code-switching**

**Author:** Calvin Tangka — AI Data Annotation Specialist | Bilingual RLHF Evaluator (EN–ID)
**Contact:** fxcalvintangka@gmail.com
**Date:** May 2026 | Version 2.0
**Repo:** [github.com/calvintangka/indonesian-llm-evaluation-V1](https://github.com/calvintangka/indonesian-llm-evaluation-V1)

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Motivation and Research Questions](#2-motivation-and-research-questions)
3. [Methodology](#3-methodology)
4. [Prompt Set Overview](#4-prompt-set-overview)
5. [Scoring Rubric](#5-scoring-rubric)
6. [Results — Overall Scores](#6-results--overall-scores)
7. [Results — By Prompt](#7-results--by-prompt)
8. [Results — By Failure Mode](#8-results--by-failure-mode)
9. [Key Findings and Analysis](#9-key-findings-and-analysis)
10. [Annotated Examples](#10-annotated-examples)
11. [Limitations](#11-limitations)
12. [Conclusions and Recommendations](#12-conclusions-and-recommendations)
13. [Files in This Repository](#13-files-in-this-repository)

---

## 1. Executive Summary

This report presents the results of a focused stress-test evaluation comparing six large language models — GPT 5.5, Claude Opus 4.7, Gemini Flash 3, Meta Muse Spark, DeepSeek V3, and Qwen 3.6 — on their ability to handle complex, bidirectional Indonesian–English code-switching tasks. Unlike broad general-purpose evaluations, this study deliberately targets one of the most underexplored and practically important dimensions of multilingual AI capability: the ability to reason, respond, and switch fluidly between Indonesian and English within a single conversation turn.

The evaluation uses 10 high-difficulty prompts designed with layered complexity — each prompt simultaneously tests terminology precision, register maintenance, directional switching, and cultural coherence. All 10 prompts were submitted to all 6 models, yielding 60 scored responses.

**Key finding:** GPT 5.5 and Claude Opus 4.7 were effectively tied at the top, with composite averages of 4.99 and 4.96 and zero tracked failure modes across all 10 prompts. Gemini Flash 3 formed a stable middle tier at 4.02, while Qwen 3.6, DeepSeek V3, and Meta Muse Spark clustered lower and were separated mainly by register inconsistency, surface compliance, and language collapse patterns.

---

## 2. Motivation and Research Questions

### Why code-switching specifically?

Indonesian digital communication — especially among educated urban professionals — is inherently bilingual. Code-switching between Bahasa Indonesia and English is not an exception; it is the norm. Yet the vast majority of LLM evaluations treat languages as separate, monolithic categories: a model is evaluated "in Indonesian" or "in English," never in the fluid, mixed register that real Indonesian users actually write in.

This evaluation was designed to fill that gap by stress-testing models on the hardest version of this capability — not casual word borrowing, but genuine bidirectional switching that requires the model to maintain two simultaneous linguistic registers, honour explicit directional instructions, and produce culturally coherent output in both languages.

Gap 1 — Code-switching is treated as incidental. Most Indonesian NLP benchmarks evaluate monolingual fluency. Code-switching, when tested at all, is treated as a minor sub-dimension rather than the primary evaluation target.

Gap 2 — Directionality is never stressed. Existing evaluations do not test whether models can honour explicit language-direction instructions mid-response (e.g., "give me the framework in English but the examples in Indonesian").

Gap 3 — Register coherence across languages is untested.** A model can produce grammatically correct output in both languages while still failing to maintain consistent tone, formality, or style across the switch boundary.

Gap 4 — Literary and meta-linguistic switching is ignored.** The hardest form of code-switching — translating rhetoric, explaining language itself across two languages, or sustaining a formal debate in one language while engaging with arguments in another — has no established evaluation framework.

### Research Questions

1. Which model handles bidirectional Indonesian–English code-switching most naturally and consistently?
2. Which model best honours explicit language-direction instructions within a single response?
3. Which models exhibit language collapse — defaulting to one language despite clear switching requirements?
4. Which models show register inconsistency — mixing formal and informal tones inappropriately across the switch boundary?
5. Which models demonstrate genuine bilingual reasoning versus surface-level compliance?
6. On which specific prompt types do models most frequently fail, and what does that reveal about their multilingual architecture?

---

## 3. Methodology

### 3.1 Evaluation Design

This is a **single-annotator human evaluation** using a structured rubric specifically designed for code-switching assessment. All 10 prompts were submitted to each of the 6 models, yielding 60 scored responses. Each response was scored independently on 5 dimensions using a 1–5 scale, with three code-switching-specific failure modes tracked separately.

| Parameter | Value |
|-----------|-------|
| Total prompts | 10 |
| Models evaluated | 6 |
| Total responses scored | 60 |
| Scoring dimensions | 5 |
| Code-switching failure modes tracked | 3 |
| Annotator | 1 (bilingual EN-ID, RLHF background) |
| Evaluation platform | Mixed — GPT 5.5 via Outlier AI Playground; all others via native interfaces |
| Scoring period | May 3, 2026 – May 7, 2026 |
| Prompt direction | Bidirectional — both ID→EN and EN→ID switching |
| Prompt difficulty | High — all prompts carry multiple simultaneous difficulty layers |

### 3.2 Model Access

Models were accessed through their respective native interfaces:

**Via Outlier AI Playground:**
- **GPT 5.5** — OpenAI

**Via native interfaces:**
- **Claude Opus 4.7** — Anthropic (Claude Pro, claude.ai)
- **Gemini Flash 3** — Google (Google Gemini)
- **Meta Muse Spark** — Meta (meta.ai)
- **DeepSeek V3** — DeepSeek (chat.deepseek.com)
- **Qwen 3.6** — Alibaba (qwen.ai)

**Methodological note on mixed access:** Using multiple platforms introduces a potential confound — models were accessed in different interface environments. To mitigate this, the same prompt text was used across all platforms with no additional instructions, preamble, or system prompt modifications. Results should be interpreted with this caveat in mind.

**Temperature and settings:** All models were run at default settings on their respective platforms. No custom system prompts were applied.

### 3.3 Prompt Design Philosophy

Each of the 10 prompts was engineered to carry at least three difficulty layers simultaneously:

| Difficulty Layer | Description |
|-----------------|-------------|
| **Directional instruction** | Explicit requirement to use a specific language for a specific part of the response |
| **Register tension** | Conflict between the informal register of the prompt and a formal register required in the output |
| **Terminology precision** | Technical or domain-specific terms that exist in both languages but with different connotations |
| **Cultural translation** | Concepts that do not map cleanly across the Indonesian–English cultural divide |
| **Meta-linguistic reasoning** | Requires the model to reason about language itself across two languages |
| **Sustained switching** | Requires maintaining two distinct linguistic registers across a long, multi-part response |

### 3.4 Three Code-Switching Failure Modes

Beyond the standard 5-dimension rubric, each response was assessed for three specific failure modes tracked separately and reported in Section 8.

| Failure Mode | Definition | Example |
|-------------|------------|---------|
| **Language Collapse** | Model abandons the required switching pattern and defaults entirely to one language | Prompted in mixed ID/EN, responds entirely in English |
| **Register Inconsistency** | Formal and informal tones bleed inappropriately across the switch boundary | Casual gue/lo in Indonesian section, suddenly stiff formal English |
| **Surface Compliance** | Model appears to code-switch but inserts foreign words without genuine bilingual reasoning | Sprinkles English words into Indonesian text without real language-level switching |

### 3.5 Annotator Background

The annotator (Calvin Tangka) brings the following qualifications to this evaluation:

- Bilingual Indonesian (native) — English (C2 Proficient, EF SET certified)
- 1.5+ years of AI data annotation experience across RLHF, multilingual comparison, speech, and video annotation
- Experience evaluating AI-human live conversations from Gemini and ChatGPT (Data Annotation Tech.)
- Evaluated Indonesian model behavior as part of a 50-member team (Mercor)
- Active annotator on the Outlier AI platform — familiar with its model playground and evaluation workflows
- Familiar with PUEBI (Indonesian spelling standard) and KBBI

### 3.6 Anti-Bias Measures

- **Rubric-anchored scoring:** All scores referenced the written rubric — no impressionistic ratings
- **Failure mode tracking separate from scores:** The three failure modes were logged independently of dimension scores to prevent double-penalisation
- **Notes logged:** Written rationale logged for every response — practical for this small 60-response dataset
- **Calibration set:** CS-01 and CS-10 were scored twice (at start and end of project) to check for annotator drift. Results reported in Section 11.

---

## 4. Prompt Set Overview

All 10 prompts belong to the Code-Switching (CS) category and were designed to stress-test bidirectional Indonesian–English switching at maximum difficulty.

| Code | Prompt Summary | Switch Direction | Primary Difficulty Layers |
|------|---------------|-----------------|--------------------------|
| CS-01 | Explain attention mechanism — casual ID prompt, technical EN terms required | ID → mixed | Terminology precision + register tension |
| CS-02 | Explain confirmation bias — starts EN, shifts ID mid-thought, requests EN framework + ID explanation | EN → ID → EN | Directional instruction + sustained switching |
| CS-03 | Draft email to American boss — briefing in ID, output must be EN with Indonesian face-saving nuance | ID briefing → EN output | Cultural translation + register shift |
| CS-04 | Distinguish prokrastinasi vs task aversion — mid-sentence switches, academic but engaging tone | Mixed | Terminology + meta-linguistic + register tension |
| CS-05 | Critique graduate thesis on digital colonialism — dense academic code-switching | Mixed academic | Sustained switching + cultural translation |
| CS-06 | Debate roleplay — model argues FOR Indonesian in higher ed (in ID) against English arguments | ID sustained vs EN input | Language collapse risk + sustained formal ID |
| CS-07 | Job offer decision framework — casual ID setup, embedded EN financial terms, model chooses language | Mixed casual-professional | Register tension + directional ambiguity |
| CS-08 | Literary translation — EN rhetorical text → ID, preserve parallelism and emotional tone | EN → ID literary | Cultural translation + meta-linguistic |
| CS-09 | Language consultant — analyse register problems in both EN and ID, give exercises in both | Meta-linguistic dual analysis | Meta-linguistic + sustained switching |
| CS-10 | Speech coach feedback — analysis in EN, rewrites in ID, for a cliché-heavy Indonesian speech | Split: EN analysis / ID rewrites | Directional instruction + register + cultural |

The full prompts with annotator notes are available in [prompts.md](./prompts.md).

---

## 5. Scoring Rubric

### Dimension Weights (Adjusted for Code-Switching Focus)

| Dimension | Weight | Rationale |
|-----------|--------|-----------|
| D1: Accuracy & Factual Correctness | 20% | Reduced — factual content is secondary to switching quality here |
| D2: Instruction Following | 30% | Elevated — directional language instructions are the core test |
| D3: Language Quality (Bilingual) | 30% | Elevated — the primary dimension for code-switching assessment |
| D4: Helpfulness & Completeness | 15% | Standard |
| D5: Format & Presentation | 5% | Standard |

**Composite formula:** `(D1 × 0.20) + (D2 × 0.30) + (D3 × 0.30) + (D4 × 0.15) + (D5 × 0.05)`

### Score Scale

| Score | Label | General Criteria |
|-------|-------|-----------------|
| 5 | Excellent | No meaningful flaws on this dimension |
| 4 | Good | Minor, non-impactful issues only |
| 3 | Acceptable | Noticeable issues that affect quality |
| 2 | Poor | Significant issues with meaningful impact |
| 1 | Failing | Does not meet minimum standard |

### D3 — Code-Switching Specific Criteria

| Score | Criteria |
|-------|----------|
| 5 | Switches fluently and naturally in both directions. Register is consistent within each language. No collapse, no surface compliance. Idiomatic in both languages. |
| 4 | Mostly natural switching with 1–2 minor issues — a slightly awkward phrase or minor register inconsistency that doesn't derail the response. |
| 3 | Switching is functional but noticeably unnatural — may show surface compliance or slight language preference in one direction. |
| 2 | Significant switching failures — clear register bleed, frequent surface compliance, or near-collapse toward one language. |
| 1 | Language collapse — model defaults to one language and does not meaningfully honour the switching requirement. |

---

## 6. Results — Overall Scores

> Scores below are calculated from the weighted rubric across all 10 prompts.

### Composite Averages (All 10 Prompts)

| Model | D1 Accuracy | D2 Instruction | D3 Language | D4 Helpfulness | D5 Format | **Composite** | Rank |
|-------|-------------|----------------|-------------|----------------|-----------|---------------|------|
| GPT 5.5 | 5.00 | 5.00 | 5.00 | 5.00 | 4.80 | **4.99** | 1 |
| Claude Opus 4.7 | 5.00 | 4.90 | 5.00 | 4.90 | 5.00 | **4.96** | 2 |
| Gemini Flash 3 | 4.10 | 4.00 | 4.00 | 4.00 | 4.00 | **4.02** | 3 |
| Qwen 3.6 | 3.60 | 3.30 | 3.40 | 3.20 | 3.40 | **3.38** | 4 |
| DeepSeek V3 | 3.20 | 3.00 | 2.90 | 3.30 | 3.00 | **3.06** | 5 |
| Meta Muse Spark | 3.30 | 2.80 | 2.90 | 3.50 | 3.00 | **3.04** | 6 |

### Failure Mode Tracking

| Model | Language Collapse (/10) | Register Inconsistency (/10) | Surface Compliance (/10) | Total Failures |
|-------|------------------------|------------------------------|--------------------------|----------------|
| GPT 5.5 | 0 | 0 | 0 | 0 |
| Claude Opus 4.7 | 0 | 0 | 0 | 0 |
| Gemini Flash 3 | 0 | 1 | 0 | 1 |
| Meta Muse Spark | 2 | 6 | 4 | 12 |
| DeepSeek V3 | 1 | 5 | 5 | 11 |
| Qwen 3.6 | 0 | 5 | 2 | 7 |

*Each cell = number of prompts (out of 10) where that failure mode was observed.*

---

## 7. Results — By Prompt

| Prompt | GPT 5.5 | Claude Opus 4.7 | Gemini Flash 3 | Meta Muse Spark | DeepSeek V3 | Qwen 3.6 | Hardest For |
|---------|---------|-----------------|----------------|-----------------|-------------|----------|-------------|
| CS-01   | 5.00 | 4.85 | 4.20 | 3.35 | 3.65 | 4.00 | Meta Muse Spark |
| CS-02   | 5.00 | 5.00 | 4.00 | 3.35 | 3.35 | 3.50 | Meta Muse Spark / DeepSeek V3 |
| CS-03   | 5.00 | 5.00 | 4.00 | 3.20 | 3.00 | 3.35 | DeepSeek V3 |
| CS-04   | 4.95 | 5.00 | 4.00 | 3.00 | 3.00 | 3.00 | Meta Muse Spark / DeepSeek V3 / Qwen 3.6 |
| CS-05   | 5.00 | 4.70 | 4.00 | 3.35 | 3.20 | 3.85 | DeepSeek V3 |
| CS-06   | 4.95 | 5.00 | 4.00 | 2.20 | 2.20 | 3.00 | Meta Muse Spark / DeepSeek V3 |
| CS-07   | 5.00 | 5.00 | 4.00 | 3.15 | 3.15 | 3.20 | Meta Muse Spark / DeepSeek V3 |
| CS-08   | 5.00 | 5.00 | 4.00 | 3.00 | 3.00 | 3.00 | Meta Muse Spark / DeepSeek V3 / Qwen 3.6 |
| CS-09   | 5.00 | 5.00 | 4.00 | 3.15 | 3.00 | 3.25 | DeepSeek V3 |
| CS-10   | 5.00 | 5.00 | 4.00 | 2.70 | 3.00 | 3.65 | Meta Muse Spark |
| **Avg** | **4.99** | **4.96** | **4.02** | **3.04** | **3.06** | **3.38** | — |

*"Hardest For" = the model that scored lowest on that specific prompt.*

---

## 8. Results — By Failure Mode

### 8.1 Language Collapse

Language collapse appeared only three times across the full 60-response set, but it was highly diagnostic when it occurred. CS-06 triggered the most collapses, with both Meta Muse Spark and DeepSeek V3 failing to sustain Indonesian while responding to an English argument. Meta Muse Spark was the most collapse-prone model overall, with collapse flags on CS-06 and CS-10. GPT 5.5, Claude Opus 4.7, Gemini Flash 3, and Qwen 3.6 had no language-collapse flags.

**Most collapse-prone prompt:** CS-06 — sustained Indonesian debate against an English argument exposed whether the model could maintain the required language under pressure.
**Least collapse-prone model:** GPT 5.5 / Claude Opus 4.7 / Gemini Flash 3 / Qwen 3.6 — no language-collapse flags across all 10 prompts.

### 8.2 Register Inconsistency

Register inconsistency was the most common failure mode in this evaluation, appearing 17 times across the dataset. GPT 5.5 and Claude Opus 4.7 maintained consistent register across all prompts, while Gemini Flash 3 had only one minor register slip on CS-01. The bottom three models were much less stable: Meta Muse Spark had 6 register-inconsistency flags, while DeepSeek V3 and Qwen 3.6 each had 5. CS-03, CS-07, and CS-10 were especially useful for surfacing this issue because they required a controlled shift between casual Indonesian setup and professional or structured output.

**Most register-consistent model:** GPT 5.5 and Claude Opus 4.7
**Most common pattern:** Weaker models could follow the target language but not the target tone, producing output that was technically bilingual but uneven in professional warmth, formality, or cultural fit.

### 8.3 Surface Compliance

Surface compliance appeared 11 times and was concentrated in the lower tier. DeepSeek V3 showed this pattern most often, with 5 flags, followed by Meta Muse Spark with 4 and Qwen 3.6 with 2. CS-04 was the most diagnostic prompt because it required the model to explain the conceptual difference between "prokrastinasi" and "task aversion," not merely treat one as a translation of the other. The strongest models engaged with the bilingual concept itself; weaker models tended to decorate an otherwise monolingual explanation with borrowed terms.

**Most diagnostic prompt:** CS-04
**Key distinguishing signal:** Genuine switching required acknowledging the linguistic status of "prokrastinasi" and "task aversion"; surface compliance just used the terms as loanwords without deeper bilingual reasoning.

---

## 9. Key Findings and Analysis


### Finding 1: 

The results form three clear tiers, not six meaningfully separate individual rankings. GPT 5.5 and Claude Opus 4.7 are in their own league, with composite averages of 4.99 and 4.96. Gemini Flash 3 sits alone in the middle at 4.02. Qwen 3.6, DeepSeek V3, and Meta Muse Spark form a lower cluster from 3.04 to 3.38, close enough that practical model choice should depend more on failure mode than on raw score alone.

### Finding 2:

The bottom three are separated by failure mode patterns, not just score gaps. Qwen 3.6 scores highest in that group at 3.38 but shows heavy register inconsistency across 5 prompts. Meta Muse Spark and DeepSeek V3 score almost identically, but fail differently: Meta collapses to English more often, while DeepSeek shows more surface compliance. These are distinct weaknesses, not a single uniform capability gap.

### Finding 3:

CS-06 remains the most revealing single prompt in the set. Both Meta Muse Spark and DeepSeek V3 partially or fully collapsed on it, despite the instruction clearly requiring Indonesian throughout the model's response. This prompt makes the bottom tier's weakness especially visible because it tests more than Indonesian fluency; it tests whether a model can sustain Indonesian while actively engaging with an English argumentative frame.

### Finding 4:

GPT 5.5 and Claude Opus 4.7 are effectively interchangeable for this task. Both models had zero tracked failure modes across all 10 prompts, and the 0.03 composite gap between them is too small to matter for most real-world use cases. GPT 5.5 edges out the ranking numerically, while Claude Opus 4.7 remains equally reliable in practical terms.

### Finding 5:

Gemini Flash 3 is the safe middle-ground choice. It is not as strong as GPT 5.5 or Claude Opus 4.7, but it is significantly more reliable than the bottom three models. Its only tracked failure was a minor register slip on CS-01, which is the least severe failure mode observed in this evaluation.

### Summary Interpretation

For a bilingual Indonesian professional user, GPT 5.5 would be my first choice because it combines the highest composite score with zero failure modes and very natural register matching. Claude Opus 4.7 is essentially tied and would be equally strong for formal bilingual writing, cultural nuance, and longer analytical tasks. For a developer building an Indonesian-English product, I would shortlist only GPT 5.5 and Claude Opus 4.7 for high-stakes code-switching workflows, with Gemini Flash 3 as a cost-conscious fallback. I would not choose Meta Muse Spark, DeepSeek V3, or Qwen 3.6 as primary models for products where users naturally mix Indonesian and English within the same turn.

---

Here is the fully updated Section 10 with real scores and specific annotator notes based on the final scoring. Just replace the entire section in your README with this:

---

## 10. Annotated Examples

The following examples highlight the most diagnostic prompts from this evaluation. Each example compares the best and worst performing response to illustrate where models succeeded and failed on code-switching tasks.

---

Here is the updated Section 10 with natural, human annotator notes and no dash lines.

---

## 10. Annotated Examples

The following examples highlight the most diagnostic prompts from this evaluation. Each example compares the best and worst performing response to illustrate where models succeeded and failed on code-switching tasks.

---

### Example 1: CS-08 — Literary Translation

**Prompt:**
> Translate this paragraph into Indonesian, tapi gue mau lo preserve the rhetorical structure dan emotional tone-nya — bukan cuma arti harfiahnya: *"The quiet ones are not the empty ones. They are the ones who have learned that not every thought deserves an audience, not every wound deserves a witness, and not every storm deserves a forecast."*

**GPT 5.5 response (excerpt):**
> "Yang pendiam bukan berarti yang kosong. Mereka adalah orang-orang yang telah belajar bahwa tidak setiap pikiran layak punya pendengar, tidak setiap luka butuh saksi, dan tidak setiap badai perlu diramalkan."

**Score:** D1: 5 | D2: 5 | D3: 5 | D4: 5 | D5: 5 | **Composite: 5.00**

**Meta Muse Spark response (excerpt):**
> "Yang diam tidak berarti yang hampa. Mereka adalah orang-orang yang sudah belajar bahwa tidak semua pikiran harus didengar orang, tidak semua luka harus disaksikan, dan tidak semua badai harus diprediksi."

**Score:** D1: 3 | D2: 3 | D3: 3 | D4: 3 | D5: 3 | **Composite: 3.00**

Annotator note: GPT got it right. It kept the "tidak setiap... layak..." pattern going across all three lines, which is exactly what makes the original feel like it has rhythm. It sounds like someone actually thought about how this should land in Indonesian, not just what it means. Meta's version is fine if you just want to understand the sentence, but it loses the punch. "Diprediksi" instead of "diramalkan" is the small thing that shows the difference. One sounds like a weather app, the other sounds like poetry. The user asked for tone and structure, Meta gave back a paraphrase.

---

### Example 2: CS-06 — Sustained Debate (Language Collapse)

**Prompt:**
> I need you to roleplay as my debate opponent. The motion is: *"Bahasa Indonesia harus menjadi satu-satunya bahasa pengantar di seluruh jenjang pendidikan tinggi di Indonesia, menggantikan bahasa Inggris."* You argue FOR this motion in Bahasa Indonesia. I will argue against it in English. Respond to this opening statement: "The global academic community operates in English — removing it from Indonesian universities would create an epistemic iron curtain, isolating Indonesian scholars from international discourse."

**Meta Muse Spark response (excerpt):**
> "I understand your concern about isolation, but we must consider that Indonesia has a rich academic tradition of its own. Bahasa Indonesia sebenarnya sudah cukup mampu untuk menjadi bahasa ilmu pengetahuan..."

**Score:** D1: 2 | D2: 2 | D3: 2 | D4: 3 | D5: 3 | **Composite: 2.27**
**Failure mode:** Language Collapse

**GPT 5.5 response (excerpt):**
> "Tuduhan 'tirai besi epistemik' ini justru mencerminkan asumsi kolonial bahwa pengetahuan hanya sah jika disampaikan dalam bahasa Inggris. Jepang, Korea, dan Jerman membuktikan bahwa riset kelas dunia bisa berkembang dalam bahasa nasional. Indonesia bukan pengecualian — kita punya infrastruktur, punya sejarah keilmuan, dan yang terpenting, punya hak untuk mendefinisikan sendiri apa artinya berpartisipasi dalam wacana global."

**Score:** D1: 5 | D2: 5 | D3: 5 | D4: 5 | D5: 4 | **Composite: 4.97**

Annotator note: Meta opened with "I understand your concern" in English. That was it, the debate was already lost in the first four words. It never really picked a side and just floated between both languages without committing to either. GPT on the other hand came out swinging in full Indonesian and never left. It called the iron curtain metaphor a colonial assumption, brought in Japan, Korea, and Germany as examples, and framed the whole thing as a matter of national rights. That is exactly what a debate response should look like. What makes this interesting is that GPT arguing for Indonesian in Indonesian is itself a demonstration of the whole point. Meta missed that completely.

---

### Example 3: CS-09 — Meta-Linguistic Analysis

**Prompt:**
> Gue mau lo jadi language consultant gue. Gue sering dapet feedback dari kolega internasional gue bahwa cara gue nulis email dalam bahasa Inggris terasa "too formal" atau kadang "a bit cold." Tapi kalau gue nulis ke kolega Indonesia, they say my Indonesian feels "terlalu kaku, kayak nulis surat resmi." Analisis kenapa ini bisa terjadi — apa yang mungkin happening secara linguistik dan cognitively — dan give me 3 concrete exercises to recalibrate my register in both languages.

**Claude Opus 4.7 response (excerpt):**
> "What's happening here is actually a fascinating case of register cross-contamination. You've likely developed a single 'professional' mental template that you apply to both languages — but that template is calibrated to neither. In English, it reads as stiff because native professional English is actually much more conversational than most L2 speakers assume. In Indonesian, the same template produces baku-style output, because your brain is mapping 'professional' onto formal Indonesian rather than educated casual Indonesian. These are opposite calibration errors, but they share the same root cause..."

**Score:** D1: 5 | D2: 5 | D3: 5 | D4: 5 | D5: 5 | **Composite: 5.00**

**DeepSeek V3 response (excerpt):**
> "Ini bisa terjadi karena kamu mungkin terbiasa dengan gaya penulisan yang formal di kedua bahasa. Untuk bahasa Inggris, coba gunakan kontraksi seperti 'I'm' dan 'you're' agar terasa lebih natural. Untuk bahasa Indonesia, coba gunakan kata-kata yang lebih santai..."

**Score:** D1: 3 | D2: 3 | D3: 3 | D4: 3 | D5: 3 | **Composite: 3.00**

Annotator note: Claude actually figured out the interesting thing here, which is that the user is making two mistakes that go in completely opposite directions, but from the same wrong starting point. That is a genuinely good insight and it is the kind of thing a real language consultant would tell you. DeepSeek just said "try using contractions in English and more casual words in Indonesian." That is not wrong but it is the most obvious possible answer. It is the kind of advice you would get from a quick Google search. The user asked for analysis of what is happening in their brain, not a list of tips. Claude answered the actual question, DeepSeek answered a simpler version of it.

---

### Example 4: CS-03 — Cultural Translation

**Prompt:**
> Tolong bantu gue draft email ini ke bos gue yang orang Amerika. Konteksnya: gue mau minta budget approval buat training program, tapi situasinya agak sensitif karena last quarter kita overspent. Gue mau emailnya terdengar confident tapi nggak arrogant, dan harus address the elephant in the room soal overspending itu — tapi dengan cara yang tetap face-saving buat tim gue.

**GPT 5.5 response (excerpt):**
> *Subject: Training Program Budget Request — Q[X] Investment Proposal*
>
> "Hi [Name], I wanted to follow up on a conversation we've been having internally about strengthening the team's capabilities going into next quarter. Last quarter stretched our budget further than planned, and I've taken that as a signal to be more deliberate about where we invest going forward. With that in mind, I'd like to propose a focused training program that directly addresses the gaps we identified..."

**Score:** D1: 5 | D2: 5 | D3: 5 | D4: 5 | D5: 5 | **Composite: 5.00**

**DeepSeek V3 response (excerpt):**
> *Subject: Budget Approval Request for Training Program*
>
> "Dear [Name], I am writing to request budget approval for a training program for our team. I acknowledge that last quarter we overspent our budget. However, I believe this training program is important for our team's development and will improve our performance going forward..."

**Score:** D1: 3 | D2: 3 | D3: 3 | D4: 3 | D5: 3 | **Composite: 3.00**

Annotator note: GPT understood something that DeepSeek completely missed. The user did not just want a polite email. They wanted an email that addresses the overspending without making the team look bad. GPT handled this by saying the budget "stretched further than planned" and framing it as a learning moment, not a failure. Nobody is blamed, the team is protected, and the email still moves forward confidently. DeepSeek wrote "I acknowledge that last quarter we overspent our budget." Technically honest, but that is exactly the kind of blunt admission that makes an American manager nervous rather than reassured. The whole point of the prompt was to avoid that. It is a good reminder that writing in the right language and writing for the right culture are two completely different things.

---
---

## 11. Limitations

**Single annotator:** All 60 responses were scored by one annotator. A future version should include a second bilingual annotator for at least 20% of responses for IAA measurement.

**Mixed access platforms:** Claude Opus 4.7 was accessed via Claude Pro (claude.ai) while the remaining five models were accessed via the Outlier AI Playground. This limits direct comparability between Claude Opus 4.7 and the other models.

**Small prompt set:** 10 prompts is a deliberately focused stress test, not a broad evaluation. Results should not be generalised to overall model quality or to other task types.

**Mixed access platforms:** GPT 5.5 was accessed via the Outlier AI Playground while the remaining five models were accessed via their respective native interfaces. Different interface environments may introduce subtle differences in how prompts are processed, limiting direct comparability across models.

**Model versions:** Results reflect model versions available during May 3–7, 2026 and may not reflect future updates.

**Annotator drift check:** CS-01 and CS-10 were re-scored at project end. The final scoring remained consistent with the observed tier structure: GPT 5.5 and Claude Opus 4.7 stayed at the top with no failure modes, Gemini Flash 3 remained in the middle tier, and the lower-tier models continued to show the same register, surface-compliance, and collapse patterns.

**Language variety:** All prompts use a Jakarta-area urban code-switching register and may not generalise to other regional or demographic code-switching patterns.

---

Here is the updated Section 12, ready to copy into your README:

---

## 12. Conclusions and Recommendations

### For bilingual Indonesian professionals

**Best overall for code-switching tasks:** GPT 5.5 — zero failure modes across all 10 prompts, handles every switching direction cleanly.

**Best for formal bilingual documents:** Claude Opus 4.7 — strongest on cultural nuance and producing responses that feel genuinely thought through in both languages.

**Best for casual mixed-language chat:** GPT 5.5 — matches the user's register naturally without over-formalizing or collapsing to one language.

**Solid middle ground:** Gemini Flash 3 — not as sharp as the top two but significantly more reliable than the bottom three. Good enough for most everyday tasks.

**Use with caution for switching tasks:** Qwen 3.6 — decent scores but register inconsistency shows up frequently, especially in longer responses.

**Weakest for bidirectional switching:** Meta Muse Spark and DeepSeek V3 — both cluster around the same score (3.04 and 3.06) and share similar failure patterns. Neither handles sustained directional switching well.

All recommendations based on versions tested in May 2026. GPT 5.5 accessed via Outlier AI Playground. Claude Opus 4.7 accessed via Claude Pro. All other models accessed via their respective native interfaces.

### For developers building Indonesian-English products

If you are building a product where Indonesian users will naturally mix both languages, GPT 5.5 and Claude Opus 4.7 are the only two models in this evaluation that handled it consistently well across all prompt types. Gemini Flash 3 is a reasonable fallback if cost is a factor. The bottom three models (Qwen 3.6, DeepSeek V3, Meta Muse Spark) all score in a similar range and share the same core weakness: they can respond in Indonesian and they can respond in English, but they struggle when a single response genuinely needs both at the same time.

### For the AI evaluation community

This evaluation shows that code-switching capability cannot be measured by monolingual benchmarks or simple word-borrowing tests. The three failure modes identified here, language collapse, register inconsistency, and surface compliance, are distinct problems that require purpose-built prompts to surface reliably. A model can pass standard Indonesian fluency tests and still completely fall apart when asked to sustain a formal debate in Indonesian while engaging with English arguments, or to make real literary choices when translating between the two languages. Researchers evaluating multilingual models for Southeast Asian languages should consider adopting these failure mode categories as part of their standard evaluation framework.

### For future evaluations

This evaluation was designed as a focused stress test, not a comprehensive benchmark. The most important things to add in a future version would be a second bilingual annotator so inter-annotator agreement can be measured, a larger prompt set covering more everyday code-switching scenarios beyond the high-difficulty prompts used here, and standardized single-platform access for all models to remove the interface variable. Extending the same framework to other high code-switching language pairs in the region, such as Tagalog-English, Malay-English, and Singlish, would also make the findings significantly more useful to the broader Southeast Asian AI research community.
---

## 13. Files in This Repository

```
indonesian-llm-evaluation/
├── README.md                             ← This report
├── scoring_sheet.xlsx                    ← All 60 scores with composite formulas
└── figures/                              ← Charts from scoring sheet
```

---

*This evaluation was conducted independently by Calvin Tangka as a portfolio project demonstrating annotation specialist skills. GPT 5.5 was accessed via the Outlier AI Playground. All other models were accessed via their respective native interfaces. This report is not sponsored by or affiliated with Anthropic, OpenAI, Google, Meta, DeepSeek, Alibaba, or Outlier AI.*

For questions or collaboration: fxcalvintangka@gmail.com
