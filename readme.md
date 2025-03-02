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

---

# 🚀 Complete OpenRouter AI Model Listing

This reference guide includes all AI models available via OpenRouter, **organized by provider**. Use it to explore **LLM architectures** and select models for **learning, benchmarking, or building applications**.

---

## 📌 Table of Contents
- [OpenAI Models](#openai-models)
- [Anthropic Models](#anthropic-models)
- [Meta (Llama) Models](#meta-llama-models)
- [Google Models](#google-models)
- [Mistral AI Models](#mistral-ai-models)
- [DeepSeek Models](#deepseek-models)
- [Cohere Models](#cohere-models)
- [Qwen Models](#qwen-models)
- [Microsoft Models](#microsoft-models)
- [Community and Merged Models](#community-and-merged-models)
- [Specialized/Niche Models](#specializedniche-models)

---

## 🔷 OpenAI Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **GPT-4o** | Unknown | 128K | GPT | ❌ No | $0.0025 - $0.01 |
| **GPT-4 Turbo** | Unknown | 128K | GPT | ❌ No | $0.01 - $0.03 |
| **GPT-4.5 (Preview)** | Unknown | 128K | GPT | ❌ No | $0.075 - $0.15 |
| **GPT-3.5 Turbo** | Unknown | 16K | GPT | ❌ No | $0.0005 - $0.0015 |
| **o1** | Unknown | 200K | GPT | ❌ No | $0.015 - $0.06 |
| **o1-mini** | Unknown | 128K | GPT | ❌ No | $0.0011 - $0.0044 |

---

## 🔶 Anthropic Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Claude 3.7 Sonnet** | Unknown | 200K | Claude | ❌ No | $0.003 - $0.015 |
| **Claude 3.5 Sonnet** | Unknown | 200K | Claude | ❌ No | $0.003 - $0.015 |
| **Claude 3.5 Haiku** | Unknown | 200K | Claude | ❌ No | $0.0008 - $0.004 |
| **Claude 3 Opus** | Unknown | 200K | Claude | ❌ No | $0.015 - $0.075 |
| **Claude 2.1** | Unknown | 200K | Claude | ❌ No | $0.008 - $0.024 |

---

## 🦙 Meta (Llama) Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Llama 3.3 70B Instruct** | 70B | 131K | Llama3 | ✅ Yes | $0.00012 - $0.0003 |
| **Llama 3.1 405B** | 405B | 32K | Llama3 | ✅ Yes | $0.0008 |
| **Llama 3.1 70B** | 70B | 131K | Llama3 | ✅ Yes | $0.00012 - $0.0003 |
| **Llama 3 8B** | 8B | 8K | Llama3 | ✅ Yes | $0.00003 - $0.00006 |

---

## 🟢 Google Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Gemini Pro 1.5** | Unknown | 2M | Gemini | ❌ No | $0.00125 - $0.005 |
| **Gemini Flash 1.5** | Unknown | 1M | Gemini | ❌ No | $0.0000375 - $0.00015 |
| **Gemma 2 27B** | 27B | 8K | Gemini | ✅ Yes | $0.00027 |
| **Gemma 2 9B** | 9B | 8K | Gemini | ✅ Yes | $0.00003 - $0.00006 |

---

## 🟣 Mistral AI Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Mixtral 8x7B Instruct** | 47B | 32K | Mistral | ✅ Yes | $0.00024 |
| **Mistral 7B** | 7B | 32K | Mistral | ✅ Yes | $0.00003 - $0.000055 |
| **Mistral Large** | Unknown | 128K | Mistral | ❌ No | $0.002 - $0.006 |

---

## 🔵 DeepSeek Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **DeepSeek R1** | 671B (37B active) | 64K | DeepSeek | ✅ Yes | $0.00055 - $0.00219 |

---

## 🟠 Cohere Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Command R** | 35B | 128K | Cohere | ❌ No | $0.000475 - $0.001425 |

---

## 🟡 Qwen Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Qwen 2.5 72B** | 72B | 128K | Qwen | ✅ Yes | $0.00013 - $0.0004 |

---

## 🟤 Microsoft Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Phi-3 Medium** | 14B | 128K | Phi | ✅ Yes | $0.001 |

---

## 🛠 Community and Merged Models

| **Model Name** | **Parameters** | **Context** | **Architecture** | **Open Source** | **Cost (per 1K tokens)** |
|--------------|----------|--------------|--------------|-------------|------------------|
| **Nous: Hermes 3 70B Instruct** | 70B | 131K | Llama3 | ✅ Yes | $0.00012 - $0.0003 |

---

### 📌 Cost Tier Explanation (per 1K tokens)

| **Cost Tier** | **Pricing** |
|--------------|-------------|
| **Free** | No cost |
| **Very Low** | < $0.001 |
| **Low** | $0.001 - $0.01 |
| **Medium** | $0.01 - $0.1 |
| **High** | > $0.1 |

---

### 🔗 **Recommended Resources**
- [Llama 3 Research](https://ai.meta.com/research/publications/llama-3-a-more-capable-and-aligned-large-language-model-family/)
- [Mistral AI Reports](https://mistral.ai/news/)
- [DeepSeek R1 Paper](https://arxiv.org/abs/2312.08673)

