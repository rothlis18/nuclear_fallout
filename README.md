# 🧪 Dynamic LLM Cross-Validation Benchmark (v7.0 - Hardened)

A multi-model cross-evaluation harness testing **8 local Ollama models** across **168 total runs** (`56` generator-validator pairs × `3` evaluation lenses). Each model acts as both a **Generator**—modeling the ecological and mathematical trade-offs of wildlife survival in nuclear exclusion zones—and as a **Validator**—grading peer outputs iteratively across *Conciseness*, *Technical* rigor, and *Objectivity*.

---

## 🎯 Benchmark Prompt (`todays_q.txt`)

* **Run Date:** November 27, 2026
* **Prompt Author:** `llama3.2:3b`
* **Domain:** Quantitative Ecology, Radiation Biology & Population Dynamics

> **Exact Benchmark Question:**
> *"Examine the paradox of wildlife thriving in the Chernobyl and Fukushima exclusion zones, where persistent ionizing radiation contamination would be expected to hinder survival. Investigate the mathematical trade-off between chronic radiation-induced DNA damage, shortened individual lifespans, and elevated mutation rates versus the benefits of reduced anthropogenic pressures, including habitat fragmentation, agriculture, hunting, and industrial pollution. Develop a quantitative population-dynamics assessment modeling net reproductive survival when the mortality reduction from human absence is compared to the fitness penalty of chronic radiation exposure, and explore the implications for conservation and management strategies in similar environments."*

---

## 📊 Executive Summary

* **Run Date:** November 27, 2026
* **Total Runtime:** `06:30:17` (Fastest full 168-run sweep in the `v7.0` series)
* **Completion Breakdown:** `168` PASS | `0` FAIL | `0` ERROR (`100.0%` Pass Rate)
* **Global Mean Score:** `85.82 / 100` across 168 scored runs (reported as `85.8` in log summary)
* **Evaluation Lenses:** `Conciseness`, `Technical`, `Objectivity`

---

## 🏆 Generator Leaderboard (Ranked by Avg. Score)

*Note: Ties in average score are broken by fastest average pass runtime.*

| Rank | Generator Model | Pass Rate | Avg. Score | Avg. Loops | Avg. Time (Pass) |
| :--- | :--- | :---: | :---: | :---: | :---: |
| 🥇 **1** | `huihui_ai/qwen3-abliterated:8b` | 21 / 21 | **88.24** | 1.00 | 206.44s |
| 🥈 **2** | `phi4:latest` | 21 / 21 | **87.29** | 1.14 | 202.98s |
| 🥉 **3** | `jaahas/gemma-2-9b-it-abliterated:latest` | 21 / 21 | **86.86** | 1.00 | 95.32s |
| **4** | `mistral-nemo:12b` | 21 / 21 | **86.38** | 1.05 | 132.45s |
| **5** | `llama3.2:3b` *(Prompt Author)* | 21 / 21 | **85.90** | 1.19 | **64.44s** |
| **6** | `qwen2.5-coder:14b` | 21 / 21 | **85.05** | 1.38 | 207.75s |
| **7** | `dolphin3:latest` | 21 / 21 | **84.43** | 1.33 | 95.21s |
| **8** | `qwen2.5-coder:7b` | 21 / 21 | **82.43** | 1.14 | 77.77s |

---

## ⚖️ Validator Strictness & Retry Behavior

How each model behaved when acting as an automated judge for the other 7 models:

| Validator Model | Avg. Score Given | Avg. Loops Forced | Retry Rate | Avg. Eval Time (Pass) | Judge Profile |
| :--- | :---: | :---: | :---: | :---: | :--- |
| `qwen2.5-coder:14b` | **84.52** | 1.24 | 23.8% | 141.73s | Strictest baseline scorer; forced 5 conciseness retries |
| `dolphin3:latest` | **84.52** | 1.00 | 0.0% | **113.48s** | Fastest single-pass strict grader |
| `mistral-nemo:12b` | **85.10** | 1.10 | 9.5% | 146.79s | Balanced baseline scorer |
| `phi4:latest` | **85.48** | 1.05 | 4.8% | 164.61s | Thorough grader; awarded a `100` on `Case 34` |
| `huihui_ai/qwen3-abliterated:8b` | **85.57** | 1.19 | 19.0% | 173.92s | Slowest overall judge; awarded `100` on `Case 67` |
| `qwen2.5-coder:7b` | **86.33** | 1.19 | 19.0% | 115.65s | Fast, balanced validator |
| `llama3.2:3b` | **87.24** | 1.05 | 4.8% | 114.62s | Generous single-pass scorer |
| `jaahas/gemma-2-9b-it-abliterated:latest` | **87.81** | **1.43** | **42.9%** | 161.34s | Most demanding editor (forced retries on 9 of 21 cases, yet awarded highest average passing scores) |

---

## 🔍 Performance by Evaluation Lens

| Evaluation Lens | Pass Rate | Avg. Score | Avg. Loops | Avg. Time (Pass) |
| :--- | :---: | :---: | :---: | :---: |
| **Technical** | 56 / 56 | **86.95** | 1.07 | 137.41s |
| **Objectivity** | 56 / 56 | **86.66** | 1.09 | 137.45s |
| **Conciseness** | 56 / 56 | **83.86** | **1.30** | 132.33s |

---

## 💡 Key Takeaways & Insights

1. **`qwen3-abliterated:8b` Extends Its Undefeated Streak to 5-0 (`88.24` Avg):** Facing a quantitative ecology and radiation-biology prompt authored by `llama3.2:3b`, `qwen3-abliterated:8b` claimed 1st place for the fifth consecutive benchmark (`86.95` → `88.86` → `90.52` → `88.14` → `88.24`), passing all 21 evaluations on the very first loop (`1.00` avg loops) and beating 2nd-place `phi4:latest` (`87.29`) by **+0.95 points**.
2. **`phi4:latest` Rebounds to #2 (`87.29`) as `Case 109` Clears Cleanly:** After stalling on `Case 109` (`GEN: phi4:latest | VAL: huihui_ai/qwen3-abliterated:8b | LENS: conciseness`) in three of the four previous runs, `phi4:latest` passed `Case 109` on the first loop in **`227.37s`** (`Score: 85`) and surged to 2nd place overall.
3. **`gemma-2-9b-it-abliterated` Delivers Best Speed-to-Quality Efficiency:** Finishing **3rd overall (`86.86`)** with a **`1.00` loop average** and an average pass runtime of just **`95.32s`**, `gemma-2-9b-it-abliterated` outperformed `mistral-nemo:12b` (`86.38`, `132.45s`) and matched the top tier in **less than half the inference time** of `qwen3-abliterated:8b` (`206.44s`) and `phi4:latest` (`202.98s`).
4. **`llama3.2:3b` Punches Above Its Weight on Its Own Prompt:** Authoring the Chernobyl/Fukushima prompt, the 3B-parameter `llama3.2:3b` finished **5th overall (`85.90`)**—beating both `qwen2.5-coder:14b` (`85.05`) and `dolphin3:latest` (`84.43`) while running at a blazing **`64.44s`** per pass.
5. **Conciseness Remains the Primary Bottleneck (`83.86` vs. `86.95` Technical):** Both `Technical` (`86.95`) and `Objectivity` (`86.66`) cleared easily across all 8 models, whereas `Conciseness` (`83.86`) dragged down overall scores by over 3 full points and triggered **65% of all retry loops** (17 of 26 total retries).

