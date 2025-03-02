Below is a revised version of your README text with improved clarity and formatting:

---

## Project Overview

This project documents my journey in learning, building, and iterating on LLM applications. The focus is on developing text-to-text interactions initially, with plans to expand to image and sound capabilities in the future.

## Roadmap

1. **Model Flexibility:**  
   The first step is selecting a group API provider that allows seamless switching between different models. This will enable easy experimentation and testing of various models.

2. **Provider Choice:**  
   We have chosen to work with [OpenRouter](https://openrouter.ai) (with [Together.ai](https://together.ai) as an alternative).  
   > **Note:** OpenRouter has occasionally been known to censor its output. However, in the absence of a better alternative, we will continue using it for now.
3. **Pricing:**  
   We have chosen to work with [OpenRouter](https://openrouter.ai) (with [Together.ai](https://together.ai) as an alternative). 
I will format this additional section properly so that it is **GitHub README-ready**, with **consistent styling, better readability, and well-structured Markdown tables**. I'll provide the updated version shortly.

Here’s your **GitHub-optimized** version of the **LLM Model Building Reference Guide**, including the additional section you requested. This version ensures **clear formatting, consistent styling, and readability for GitHub**.

---

# 🚀 LLM Model Building Reference Guide

This guide categorizes LLMs based on **size, architecture, context length, cost, and use case**, helping developers choose the best models for their needs.

---

## 🔥 Proprietary Frontier Models (Important to Study)

| **Model Name** | **Parameters** | **Architecture** | **Context Length** | **Special Features** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|---------------|------------------|-------------|------------------|
| **OpenAI: GPT-4** | Unknown (~1.8T est.) | GPT | 8K-128K | Multimodal, RLHF | ❌ No | $0.03-$0.06 |
| **OpenAI: GPT-4o** | Unknown | GPT | 128K | Fast multimodal | ❌ No | $0.0025-$0.01 |
| **OpenAI: o1** | Unknown | GPT | 200K | Reasoning focus | ❌ No | $0.015-$0.06 |
| **Anthropic: Claude 3 Opus** | Unknown (~2T est.) | Claude | 200K | Document analysis | ❌ No | $0.015-$0.075 |
| **Anthropic: Claude 3.5 Sonnet** | Unknown | Claude | 200K | Advanced reasoning | ❌ No | $0.003-$0.015 |
| **Google: Gemini Pro 1.5** | Unknown | Gemini | 2M | Long context | ❌ No | $0.00125-$0.005 |
| **Mistral: Mistral Large** | Unknown | Mistral | 128K | Reasoning, multilingual | ❌ No | $0.002-$0.006 |

---

## 🔓 Leading Open Source Models (Best for Direct Learning)

| **Model Name** | **Parameters** | **Architecture** | **Context Length** | **Special Features** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|---------------|------------------|-------------|------------------|
| **Meta: Llama 3.1 405B** | 405B | Llama | 32K | Frontier level | ✅ Yes | $0.0008 |
| **Meta: Llama 3.1 70B** | 70B | Llama | 131K | Strong general purpose | ✅ Yes | $0.00012-$0.0003 |
| **DeepSeek: R1** | 671B (37B active) | DeepSeek | 64K | MoE, reasoning | ✅ Yes | $0.00055-$0.00219 |
| **Mistral: Mixtral 8×22B** | 141B (39B active) | Mistral | 65K | MoE architecture | ✅ Yes | $0.0009 |
| **Qwen: Qwen 2.5 72B** | 72B | Qwen | 128K | Multilingual | ✅ Yes | $0.00013-$0.0004 |
| **Microsoft: WizardLM-2 8×22B** | 141B (39B active) | Mistral | 65K | MoE instruction tuning | ✅ Yes | $0.0005 |
| **Databricks: DBRX 132B** | 132B (36B active) | MoE | 32K | Fine-grained MoE | ✅ Yes | $0.0012 |

---

## ⚖️ Mid-Size Models (Good Balance of Performance & Accessibility)

| **Model Name** | **Parameters** | **Architecture** | **Context Length** | **Special Features** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|---------------|------------------|-------------|------------------|
| **Meta: Llama 3 8B** | 8B | Llama | 8K | Strong base model | ✅ Yes | $0.00003-$0.00006 |
| **Microsoft: Phi-3 Medium** | 14B | Phi | 128K | Strong for size | ✅ Yes | $0.001 |
| **Mistral: Mistral Small** | 22B | Mistral | 32K | Fast inference | ✅ Yes | $0.0002-$0.0006 |
| **Google: Gemma 2 27B** | 27B | Gemini | 8K | Google research | ✅ Yes | $0.00027 |
| **Cohere: Command R** | 35B | Cohere | 128K | RAG optimized | ❌ No | $0.000475-$0.001425 |
| **OpenAI: GPT-3.5 Turbo** | Unknown | GPT | 16K | Fast, affordable | ❌ No | $0.0005-$0.0015 |
| **Qwen: Qwen 2 7B** | 7B | Qwen | 32K | Efficient | ✅ Yes | $0.000054 |

---

## 🛠 Small Models (Best for Starting Implementation)

| **Model Name** | **Parameters** | **Architecture** | **Context Length** | **Special Features** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|---------------|------------------|-------------|------------------|
| **Meta: Llama 3.2 1B** | 1B | Llama | 131K | Multilingual | ✅ Yes | Free / $0.00001 |
| **Meta: Llama 3.2 3B** | 3B | Llama | 131K | Efficient | ✅ Yes | $0.000015-$0.000025 |
| **Microsoft: Phi-3 Mini** | 3.8B | Phi | 128K | Strong reasoning | ✅ Yes | $0.0001 |
| **Google: Gemma 2 9B** | 9B | Gemini | 8K | Gemini variant | ✅ Yes | $0.00003-$0.00006 |
| **Mistral: Mistral 7B** | 7B | Mistral | 32K | Fast, efficient | ✅ Yes | $0.00003-$0.000055 |
| **Mistral: Ministral 3B** | 3B | Mistral | 128K | Edge computing | ✅ Yes | $0.00004 |
| **OpenAI: GPT-4o Mini** | Unknown | GPT | 128K | Affordable | ❌ No | $0.00015-$0.0006 |

---

## 🔬 Specialized Architecture Models (For Advanced Study)

| **Model Name** | **Parameters** | **Architecture** | **Context Length** | **Special Features** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|---------------|------------------|-------------|------------------|
| **Mistral: Codestral Mamba** | 7.3B | Mamba | 256K | Linear attention | ✅ Yes | $0.00025 |
| **AI21: Jamba** | Variable | SSM-Transformer | 256K | Novel architecture | ❌ No | $0.0005-$0.0007 |
| **Liquid: LFM 40B** | 40B | RNN hybrid | 32K | Dynamic systems | ✅ Yes | $0.00015 |
| **Liquid: LFM 7B** | 7B | RNN hybrid | 32K | Efficient | ✅ Yes | $0.00001 |
| **Anthropic: Claude 3.5 Haiku** | Unknown | Claude | 200K | Fast response | ❌ No | $0.0008-$0.004 |
| **DeepSeek: DeepSeek-V3** | Unknown | DeepSeek | 131K | RLHF techniques | ✅ Yes | $0.00125 |
| **Google: Gemini Flash 1.5 8B** | 8B | Gemini | 1M | Long context | ❌ No | $0.0000375-$0.00015 |

---

### 📌 **GitHub Ready!**
This version is **well-structured for GitHub README** with:
✅ **Markdown tables**  
✅ **Clear pricing & categories**  
✅ **Consistent spacing & readability**  
✅ **Emoji enhancements for UX**  

Let me know if you need **further refinements**! 🚀