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
# Complete OpenRouter AI Model Listing
> **Note:** This models were available as of March 1st,2025
This comprehensive reference guide includes all AI models available from the OpenRouter dataset, organized by provider. Use this for identifying models to study when learning about LLM architecture and building.

## Table of Contents
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
- [Cost Tier Explanation (per 1K tokens)](#cost-tier-explanation-per-1k-tokens)
- [Learning LLM Building: Key Model Types To Study](#learning-llm-building-key-model-types-to-study)
- [Recommended Resources](#recommended-resources)

---

## OpenAI Models

| Model Name                   | Parameters | Context | Architecture | Open Source | Cost (per 1K tokens)    |
|-----------------------------|------------|---------|--------------|-------------|-------------------------|
| GPT-4o                      | Unknown    | 128K    | GPT          | No          | $0.0025-$0.01           |
| GPT-4o (2024-08-06)         | Unknown    | 128K    | GPT          | No          | $0.0025-$0.01           |
| GPT-4o (2024-05-13)         | Unknown    | 128K    | GPT          | No          | $0.005-$0.015           |
| GPT-4o (extended)           | Unknown    | 128K    | GPT          | No          | $0.006-$0.018           |
| GPT-4o-mini                 | Unknown    | 128K    | GPT          | No          | $0.00015-$0.0006        |
| GPT-4o-mini (2024-07-18)    | Unknown    | 128K    | GPT          | No          | $0.00015-$0.0006        |
| ChatGPT-4o                  | Unknown    | 128K    | GPT          | No          | $0.005-$0.015           |
| o1                          | Unknown    | 200K    | GPT          | No          | $0.015-$0.06            |
| o1-mini                     | Unknown    | 128K    | GPT          | No          | $0.0011-$0.0044         |
| o1-mini (2024-09-12)        | Unknown    | 128K    | GPT          | No          | $0.0011-$0.0044         |
| o1-preview                  | Unknown    | 128K    | GPT          | No          | $0.015-$0.06            |
| o1-preview (2024-09-12)     | Unknown    | 128K    | GPT          | No          | $0.015-$0.06            |
| GPT-4                       | Unknown    | 8K      | GPT          | No          | $0.03-$0.06             |
| GPT-4 (older v0314)         | Unknown    | 8K      | GPT          | No          | $0.03-$0.06             |
| GPT-4-32k                   | Unknown    | 32K     | GPT          | No          | $0.06-$0.12             |
| GPT-4-32k-0314              | Unknown    | 32K     | GPT          | No          | $0.06-$0.12             |
| GPT-4 Turbo                 | Unknown    | 128K    | GPT          | No          | $0.01-$0.03             |
| GPT-4 Turbo (older v1106)   | Unknown    | 128K    | GPT          | No          | $0.01-$0.03             |
| GPT-4 Turbo Preview         | Unknown    | 128K    | GPT          | No          | $0.01-$0.03             |
| GPT-3.5 Turbo               | Unknown    | 16K     | GPT          | No          | $0.0005-$0.0015         |
| GPT-3.5 Turbo 16k           | Unknown    | 16K     | GPT          | No          | $0.003-$0.004           |
| GPT-3.5 Turbo 16k (older v1106) | Unknown | 16K    | GPT          | No          | $0.001-$0.002           |
| GPT-3.5 Turbo (older v0613) | Unknown    | 4K      | GPT          | No          | $0.001-$0.002           |
| GPT-3.5 Turbo Instruct      | Unknown    | 4K      | GPT          | No          | $0.0015-$0.002          |

---

## Anthropic Models

| Model Name                                | Parameters | Context | Architecture | Open Source | Cost (per 1K tokens) |
|------------------------------------------|------------|---------|--------------|-------------|----------------------|
| Claude 3.7 Sonnet                        | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.7 Sonnet (beta)                 | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.7 Sonnet (thinking)             | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.5 Sonnet                        | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.5 Sonnet (beta)                 | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.5 Sonnet (2024-10-22)           | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.5 Sonnet (2024-10-22) (beta)    | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.5 Sonnet (2024-06-20)           | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.5 Sonnet (2024-06-20) (beta)    | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3.5 Haiku                         | Unknown    | 200K    | Claude       | No          | $0.0008-$0.004      |
| Claude 3.5 Haiku (beta)                  | Unknown    | 200K    | Claude       | No          | $0.0008-$0.004      |
| Claude 3.5 Haiku (2024-10-22)            | Unknown    | 200K    | Claude       | No          | $0.0008-$0.004      |
| Claude 3.5 Haiku (2024-10-22) (beta)     | Unknown    | 200K    | Claude       | No          | $0.0008-$0.004      |
| Claude 3 Opus                            | Unknown    | 200K    | Claude       | No          | $0.015-$0.075       |
| Claude 3 Opus (beta)                     | Unknown    | 200K    | Claude       | No          | $0.015-$0.075       |
| Claude 3 Sonnet                          | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3 Sonnet (beta)                   | Unknown    | 200K    | Claude       | No          | $0.003-$0.015       |
| Claude 3 Haiku                           | Unknown    | 200K    | Claude       | No          | $0.00025-$0.00125   |
| Claude 3 Haiku (beta)                    | Unknown    | 200K    | Claude       | No          | $0.00025-$0.00125   |
| Claude 2.1                               | Unknown    | 200K    | Claude       | No          | $0.008-$0.024       |
| Claude 2.1 (beta)                        | Unknown    | 200K    | Claude       | No          | $0.008-$0.024       |
| Claude 2                                 | Unknown    | 200K    | Claude       | No          | $0.008-$0.024       |
| Claude 2 (beta)                          | Unknown    | 200K    | Claude       | No          | $0.008-$0.024       |
| Claude 2.0                               | Unknown    | 100K    | Claude       | No          | $0.008-$0.024       |
| Claude 2.0 (beta)                        | Unknown    | 100K    | Claude       | No          | $0.008-$0.024       |

---

## Meta (Llama) Models

| Model Name                                 | Parameters | Context | Architecture | Open Source | Cost (per 1K tokens)           |
|-------------------------------------------|------------|---------|--------------|-------------|--------------------------------|
| Llama 3.3 70B Instruct                    | 70B        | 131K    | Llama3       | Yes         | $0.00012-$0.0003               |
| Llama 3.3 70B Instruct (free)             | 70B        | 131K    | Llama3       | Yes         | Free                           |
| Llama 3.2 90B Vision Instruct             | 90B        | 4K      | Llama3       | Yes         | $0.0008-$0.0016                |
| Llama 3.2 11B Vision Instruct             | 11B        | 16K     | Llama3       | Yes         | $0.000055                      |
| Llama 3.2 11B Vision Instruct (free)      | 11B        | 131K    | Llama3       | Yes         | Free                           |
| Llama 3.2 3B Instruct                     | 3B         | 131K    | Llama3       | Yes         | $0.000015-$0.000025            |
| Llama 3.2 1B Instruct                     | 1B         | 131K    | Llama3       | Yes         | $0.00000001                    |
| Llama 3.2 1B Instruct (free)              | 1B         | 131K    | Llama3       | Yes         | Free                           |
| Llama 3.1 405B Instruct                   | 405B       | 32K     | Llama3       | Yes         | $0.0008                        |
| Llama 3.1 405B (base)                     | 405B       | 32K     | Llama3       | Yes         | $0.000002                      |
| Llama 3.1 70B Instruct                    | 70B        | 131K    | Llama3       | Yes         | $0.00012-$0.0003               |
| Llama 3.1 8B Instruct                     | 8B         | 131K    | Llama3       | Yes         | $0.00000002-$0.00000005        |
| Llama 3.1 8B Instruct (free)              | 8B         | 131K    | Llama3       | Yes         | Free                           |
| Llama 3 70B Instruct                      | 70B        | 8K      | Llama3       | Yes         | $0.00023-$0.0004               |
| Llama 3 8B Instruct                       | 8B         | 8K      | Llama3       | Yes         | $0.00000003-$0.00000006        |
| Llama 3 8B Instruct (free)                | 8B         | 8K      | Llama3       | Yes         | Free                           |
| Llama 3 70B (Base)                        | 70B        | 8K      | Llama3       | Yes         | $0.00000059-$0.00000079        |
| Llama 3 8B (Base)                         | 8B         | 8K      | Llama3       | Yes         | $0.00000005-$0.00000008        |
| Llama Guard 2 8B                          | 8B         | 8K      | Llama3       | Yes         | $0.0000002                     |
| Llama Guard 3 8B                          | 8B         | 8K      | Llama3       | Yes         | $0.0000002                     |
| Llama 2 70B Chat                          | 70B        | 4K      | Llama2       | Yes         | $0.0000009                     |
| Llama 2 13B Chat                          | 13B        | 4K      | Llama2       | Yes         | $0.00000022                    |

---

## Google Models

| Model Name                               | Parameters | Context | Architecture | Open Source | Cost (per 1K tokens)               |
|-----------------------------------------|------------|---------|--------------|-------------|------------------------------------|
| Gemini Pro 1.5                          | Unknown    | 2M      | Gemini       | No          | $0.00125-$0.005                    |
| Gemini 2.0 Flash                        | Unknown    | 1M      | Gemini       | No          | $0.0000001-$0.0000004              |
| Gemini 2.0 Flash Lite                   | Unknown    | 1M      | Gemini       | No          | $0.000000075-$0.0000003            |
| Gemini 2.0 Flash Lite Preview (free)    | Unknown    | 1M      | Gemini       | No          | Free                                |
| Gemini 2.0 Pro Experimental (free)      | Unknown    | 2M      | Gemini       | No          | Free                                |
| Gemini 2.0 Flash Thinking Experimental (free) | Unknown | 1M | Gemini       | No          | Free                                |
| Gemini 2.0 Flash Thinking Experimental 01-21 (free) | Unknown | 1M | Gemini | No | Free                                |
| Gemini 2.0 Flash Experimental (free)    | Unknown    | 1M      | Gemini       | No          | Free                                |
| Gemini Experimental 1206 (free)         | Unknown    | 2M      | Gemini       | No          | Free                                |
| Gemini Flash 1.5                        | Unknown    | 1M      | Gemini       | No          | $0.000000075-$0.0000003            |
| Gemini Flash 1.5 8B                     | 8B         | 1M      | Gemini       | No          | $0.0000000375-$0.00000015          |
| Gemini Flash 1.5 8B Experimental        | 8B         | 1M      | Gemini       | No          | Free                                |
| LearnLM 1.5 Pro Experimental (free)     | Unknown    | 40K     | Gemini       | No          | Free                                |
| Gemini Pro                              | Unknown    | 32K     | Gemini       | No          | $0.0000005-$0.0000015              |
| Gemini Pro Vision 1.0                   | Unknown    | 16K     | Gemini       | No          | $0.0000005-$0.0000015              |
| PaLM 2 Chat                             | Unknown    | 9K      | PaLM         | No          | $0.000001-$0.000002                |
| PaLM 2 Chat 32k                         | Unknown    | 32K     | PaLM         | No          | $0.000001-$0.000002                |
| PaLM 2 Code Chat                        | Unknown    | 7K      | PaLM         | No          | $0.000001-$0.000002                |
| PaLM 2 Code Chat 32k                    | Unknown    | 32K     | PaLM         | No          | $0.000001-$0.000002                |
| Gemma 2 27B                             | 27B        | 8K      | Gemini       | Yes         | $0.00000027                         |
| Gemma 2 9B                              | 9B         | 8K      | Gemini       | Yes         | $0.00000003-$0.00000006            |
| Gemma 2 9B (free)                       | 9B         | 8K      | Gemini       | Yes         | Free                                |
| Gemma 7B                                | 7B         | 8K      | Gemini       | Yes         | $0.00000015                         |

---

## Mistral AI Models

| Model Name                      | Parameters              | Context | Architecture | Open Source | Cost (per 1K tokens)           |
|--------------------------------|-------------------------|---------|--------------|-------------|--------------------------------|
| Mistral Large 2411             | Unknown                 | 128K    | Mistral      | No          | $0.000002-$0.000006            |
| Mistral Large 2407             | Unknown                 | 128K    | Mistral      | No          | $0.000002-$0.000006            |
| Mistral Large                   | Unknown                 | 128K    | Mistral      | No          | $0.000002-$0.000006            |
| Mistral Medium                  | Unknown                 | 32K     | Mistral      | No          | $0.00000275-$0.0000081         |
| Mistral Small                   | 22B                     | 32K     | Mistral      | No          | $0.0000002-$0.0000006          |
| Mistral Small 3                 | 24B                     | 32K     | Mistral      | Yes         | $0.00000007-$0.00000014        |
| Mistral Small 3 (free)          | 24B                     | 32K     | Mistral      | Yes         | Free                           |
| Mistral Tiny                    | 7B                      | 32K     | Mistral      | No          | $0.00000025                    |
| Mistral Saba                    | 24B                     | 32K     | Mistral      | Yes         | $0.0000002-$0.0000006          |
| Ministral 8B                    | 8B                      | 128K    | Mistral      | Yes         | $0.0000001                     |
| Ministral 3B                    | 3B                      | 128K    | Mistral      | Yes         | $0.00000004                    |
| Mistral 7B Instruct             | 7B                      | 32K     | Mistral      | Yes         | $0.00000003-$0.000000055       |
| Mistral 7B Instruct (free)      | 7B                      | 8K      | Mistral      | Yes         | Free                           |
| Mistral 7B Instruct v0.3        | 7B                      | 32K     | Mistral      | Yes         | $0.00000003-$0.000000055       |
| Mistral 7B Instruct v0.1        | 7B                      | 32K     | Mistral      | Yes         | $0.0000002                     |
| Mistral Nemo                    | 12B                     | 131K    | Mistral      | Yes         | $0.000000035-$0.00000008       |
| Mistral Nemo (free)            | 12B                     | 128K    | Mistral      | Yes         | Free                           |
| Codestral 2501                  | Unknown                 | 256K    | Mistral      | Yes         | $0.0000003-$0.0000009          |
| Codestral Mamba                 | 7.3B                    | 256K    | Mistral      | Yes         | $0.00000025                    |
| Mixtral 8x22B Instruct          | 141B (39B active)       | 65K     | Mistral      | Yes         | $0.0000009                     |
| Mixtral 8x7B Instruct           | 47B (8x7B active)       | 32K     | Mistral      | Yes         | $0.00000024                    |
| Mixtral 8x7B (base)            | 47B (8x7B active)       | 32K     | Mistral      | Yes         | $0.0000006                     |
| Pixtral Large 2411              | 124B                    | 128K    | Mistral      | Yes         | $0.000002-$0.000006            |
| Pixtral 12B                     | 12B                     | 4K      | Mistral      | Yes         | $0.0000001                     |

---

## DeepSeek Models

| Model Name                                 | Parameters            | Context | Architecture | Open Source | Cost (per 1K tokens)                 |
|-------------------------------------------|-----------------------|---------|--------------|-------------|--------------------------------------|
| DeepSeek R1                               | 671B (37B active)     | 64K     | DeepSeek     | Yes         | $0.00000055-$0.00000219              |
| DeepSeek R1 (free)                        | 671B (37B active)     | 163K    | DeepSeek     | Yes         | Free                                 |
| DeepSeek R1 Distill Llama 70B            | 70B                   | 131K    | Llama3       | Yes         | $0.00000023-$0.00000069              |
| DeepSeek R1 Distill Llama 70B (free)      | 70B                   | 128K    | Llama3       | Yes         | Free                                 |
| DeepSeek R1 Distill Llama 8B             | 8B                    | 32K     | Llama3       | Yes         | $0.00000004                          |
| DeepSeek R1 Distill Qwen 32B             | 32B                   | 131K    | Qwen         | Yes         | $0.00000012-$0.00000018              |
| DeepSeek R1 Distill Qwen 14B             | 14B                   | 131K    | Qwen         | Yes         | $0.0000016                           |
| DeepSeek R1 Distill Qwen 1.5B            | 1.5B                  | 131K    | Other        | Yes         | $0.00000018                          |
| DeepSeek Chat                             | Unknown               | 131K    | DeepSeek     | Yes         | $0.00000125                          |
| DeepSeek Chat (free)                     | Unknown               | 131K    | DeepSeek     | Yes         | Free                                 |
| DeepSeek V2.5                             | Unknown               | 8K      | Other        | Yes         | $0.000002                            |

---

## Cohere Models

| Model Name             | Parameters | Context | Architecture | Open Source | Cost (per 1K tokens)              |
|------------------------|------------|---------|--------------|-------------|-----------------------------------|
| Command                | Unknown    | 4K      | Cohere       | No          | $0.00000095-$0.0000019            |
| Command R              | 35B       | 128K    | Cohere       | No          | $0.000000475-$0.000001425         |
| Command R (03-2024)    | 35B       | 128K    | Cohere       | No          | $0.000000475-$0.000001425         |
| Command R (08-2024)    | 35B       | 128K    | Cohere       | No          | $0.0000001425-$0.00000057         |
| Command R+             | 104B      | 128K    | Cohere       | No          | $0.00000285-$0.00001425           |
| Command R+ (04-2024)   | 104B      | 128K    | Cohere       | No          | $0.00000285-$0.00001425           |
| Command R+ (08-2024)   | 104B      | 128K    | Cohere       | No          | $0.000002375-$0.0000095           |
| Command R7B (12-2024)  | 7B        | 128K    | Cohere       | No          | $0.0000000375-$0.00000015         |

---

## Qwen Models

| Model Name                          | Parameters | Context | Architecture | Open Source | Cost (per 1K tokens)        |
|------------------------------------|-----------|---------|--------------|-------------|-----------------------------|
| Qwen 2.5 72B Instruct              | 72B       | 128K    | Qwen         | Yes         | $0.00000013-$0.0000004      |
| Qwen 2.5 7B Instruct               | 7B        | 32K     | Qwen         | Yes         | $0.000000025-$0.00000005    |
| Qwen 2.5 Coder 32B Instruct        | 32B       | 33K     | Qwen         | Yes         | $0.00000007-$0.00000016     |
| Qwen 2.5 Coder 32B Instruct (free) | 32B       | 128K    | Qwen         | Yes         | Free                        |
| Qwen 2 72B Instruct                | 72B       | 32K     | Qwen         | Yes         | $0.0000009                  |
| Qwen 2 7B Instruct                 | 7B        | 32K     | Qwen         | Yes         | $0.000000054                |
| Qwen 2 7B Instruct (free)          | 7B        | 8K      | Qwen         | Yes         | Free                        |
| Qwen 2-VL 72B Instruct             | 72B       | 4K      | Qwen         | Yes         | $0.0000004                  |
| Qwen 2-VL 7B Instruct              | 7B        | 4K      | Qwen         | Yes         | $0.0000001                  |
| Qwen VL Plus (free)                | Unknown   | 7.5K    | Qwen         | Yes         | Free                        |
| QVQ 72B Preview                    | 72B       | 32K     | Qwen         | Yes         | $0.00000025-$0.0000005      |
| QWQ 32B Preview                    | 32B       | 32K     | Qwen         | Yes         | $0.00000012-$0.00000018     |
| Qwen Max                           | Unknown   | 32K     | Qwen         | Yes         | $0.0000016-$0.0000064       |
| Qwen Plus                          | Unknown   | 131K    | Qwen         | Yes         | $0.0000004-$0.0000012       |
| Qwen Turbo                         | Unknown   | 1M      | Qwen         | Yes         | $0.00000005-$0.0000002      |

---

## Microsoft Models

| Model Name                            | Parameters | Context | Architecture | Open Source | Cost (per 1K tokens)         |
|--------------------------------------|-----------|---------|--------------|-------------|------------------------------|
| Phi 4                                | 14B       | 16K     | Other        | Yes         | $0.00000007-$0.00000014      |
| Phi-3.5 Mini 128K Instruct           | 3.8B      | 128K    | Other        | Yes         | $0.0000001                   |
| Phi-3.5 Mini 128K Instruct (free)    | 3.8B      | 8K      | Other        | Yes         | Free                         |
| Phi-3.5 Medium 128K Instruct         | 14B       | 128K    | Other        | Yes         | $0.000001                    |
| Phi-3.5 Medium 128K Instruct (free)  | 14B       | 8K      | Other        | Yes         | Free                         |
| Phi-3 Mini 128K Instruct             | 3.8B      | 128K    | Other        | Yes         | $0.0000001                   |
| Phi-3 Mini 128K Instruct (free)      | 3.8B      | 8K      | Other        | Yes         | Free                         |
| Phi-3 Medium 128K Instruct           | 14B       | 128K    | Other        | Yes         | $0.000001                    |
| Phi-3 Medium 128K Instruct (free)    | 14B       | 8K      | Other        | Yes         | Free                         |
| WizardLM-2 8x22B                     | 176B      | 65K     | Mistral      | Yes         | $0.0000005                   |
| WizardLM-2 7B                        | 7B        | 32K     | Mistral      | Yes         | $0.00000007                  |

---

## Community and Merged Models

| Model Name                                  | Parameters               | Context | Architecture | Open Source | Cost (per 1K tokens)            |
|--------------------------------------------|--------------------------|---------|--------------|-------------|---------------------------------|
| Dolphin 2.9.2 Mixtral 8x22B                | 176B                     | 16K     | Mistral      | Yes         | $0.0000009                      |
| Dolphin 2.6 Mixtral 8x7B                   | 47B                      | 32K     | Mistral      | Yes         | $0.0000005                      |
| Dolphin3.0 Mistral 24B (free)              | 24B                      | 32K     | Other        | Yes         | Free                            |
| Dolphin3.0 R1 Mistral 24B (free)           | 24B                      | 32K     | Other        | Yes         | Free                            |
| NeverSleep: Llama 3 Lumimaid 70B           | 70B                      | 8K      | Llama3       | Yes         | $0.000003375-$0.0000045         |
| NeverSleep: Llama 3 Lumimaid 8B            | 8B                       | 24K     | Llama3       | Yes         | $0.0000001875-$0.000001125      |
| NeverSleep: Llama 3 Lumimaid 8B (extended) | 8B                       | 24K     | Llama3       | Yes         | $0.0000001875-$0.000001125      |
| NeverSleep: Llama 3.1 Lumimaid 70B         | 70B                      | 16K     | Llama3       | Yes         | $0.000003375-$0.0000045         |
| NeverSleep: Llama 3.1 Lumimaid 8B          | 8B                       | 32K     | Llama3       | Yes         | $0.0000001875-$0.000001125      |
| EVA Llama 3 70B                            | 70B                      | 16K     | Llama3       | Yes         | $0.000004-$0.000006             |
| EVA Llama 3.1 70B                          | 70B                      | 16K     | Llama3       | Yes         | $0.000004-$0.000006             |
| EVA Qwen 2.5 32B                           | 32B                      | 16K     | Qwen         | Yes         | $0.0000026-$0.0000034           |
| EVA Qwen 2.5 72B                           | 72B                      | 32K     | Qwen         | Yes         | $0.0000007                      |
| Aetherwiing: Starcannon 12B               | 12B                      | 16K     | Mistral      | Yes         | $0.0000008-$0.0000012           |
| Mistral Nemo 12B Celeste                  | 12B                      | 16K     | Mistral      | Yes         | $0.0000008-$0.0000012           |
| Infermatic: Mistral Nemo Inferor 12B      | 12B                      | 16K     | Mistral      | Yes         | $0.0000008-$0.0000012           |
| Unslopnemo 12B                             | 12B                      | 32K     | Mistral      | Yes         | $0.0000005                      |
| Nous: Hermes 2 Mixtral 8x7B DPO           | 47B                      | 32K     | Mistral      | Yes         | $0.0000006                      |
| Nous: Hermes 2 Pro - Llama-3 8B           | 8B                       | 131K    | Llama3       | Yes         | $0.000000025-$0.00000004        |
| Nous: Hermes 3 70B Instruct               | 70B                      | 131K    | Llama3       | Yes         | $0.00000012-$0.0000003          |
| Nous: Hermes 3 405B Instruct              | 405B                     | 131K    | Llama3       | Yes         | $0.0000008                      |
| OpenHermes 2.5 Mistral 7B                 | 7B                       | 4K      | Mistral      | Yes         | $0.00000017                     |
| OpenChat 3.5 7B                           | 7B                       | 8K      | Mistral      | Yes         | $0.000000055                    |
| OpenChat 3.5 7B (free)                    | 7B                       | 8K      | Mistral      | Yes         | Free                            |
| Fimbulvetr 11B v2                         | 11B                      | 4K      | Llama2       | Yes         | $0.0000008-$0.0000012           |
| Toppy M 7B                                | 7B                       | 4K      | Mistral      | Yes         | $0.00000007                     |
| Toppy M 7B (free)                         | 7B                       | 4K      | Mistral      | Yes         | Free                            |
| Magnum v4 72B                             | 72B                      | 16K     | Qwen         | Yes         | $0.000001875-$0.00000225        |
| Magnum v2 72B                             | 72B                      | 32K     | Qwen         | Yes         | $0.000003                       |
| Alpindale/Goliath 120B                   | 120B                     | 6K      | Llama2       | Yes         | $0.000009375                    |
| Pygmalion: Mythalion 13B                 | 13B                      | 4K      | Llama2       | Yes         | $0.0000008-$0.0000012           |
| Airoboros 70B                             | 70B                      | 4K      | Llama2       | Yes         | $0.0000005                      |
| Xwin 70B                                  | 70B                      | 8K      | Llama2       | Yes         | $0.00000375                     |
| ReMM SLERP 13B                            | 13B                      | 4K      | Llama2       | Yes         | $0.0000008-$0.0000012           |
| MythoMax 13B                              | 13B                      | 4K      | Llama2       | Yes         | $0.000000065                    |
| MythoMax 13B (free)                       | 13B                      | 4K      | Llama2       | Yes         | Free                            |
| Midnight Rose 70B                         | 70B                      | 4K      | Llama2       | Yes         | $0.0000008                      |
| SorcererLM 8x22B                          | 176B                     | 16K     | Mistral      | Yes         | $0.0000045                      |

---

## Specialized/Niche Models

| Model Name                                   | Parameters          | Context | Architecture | Open Source | Cost (per 1K tokens)        |
|---------------------------------------------|---------------------|---------|--------------|-------------|-----------------------------|
| Perplexity: R1 1776                         | Unknown            | 128K    | DeepSeek     | Yes         | $0.000002-$0.000008         |
| Perplexity: Sonar Reasoning                 | Unknown            | 127K    | Other        | Yes         | $0.000001-$0.000005         |
| Perplexity: Sonar                           | Unknown            | 127K    | Other        | Yes         | $0.000001                   |
| Perplexity: Llama 3.1 Sonar 8B             | 8B                 | 131K    | Llama3       | Yes         | $0.0000002                  |
| Perplexity: Llama 3.1 Sonar 70B            | 70B                | 131K    | Llama3       | Yes         | $0.000001                   |
| Perplexity: Llama 3.1 Sonar 8B Online      | 8B                 | 127K    | Llama3       | Yes         | $0.0000002                  |
| Perplexity: Llama 3.1 Sonar 70B Online     | 70B                | 127K    | Llama3       | Yes         | $0.000001                   |
| Sao10K: Llama 3.1 Euryale 70B v2.2         | 70B                | 131K    | Llama3       | Yes         | $0.0000007-$0.0000008       |
| Sao10K: Llama 3.3 Euryale 70B              | 70B                | 131K    | Llama3       | Yes         | $0.0000007-$0.0000008       |
| Sao10K: Llama 3 Euryale 70B v2.1           | 70B                | 8K      | Llama3       | Yes         | $0.0000007-$0.0000008       |
| Sao10K: Llama 3 8B Lunaris                 | 8B                 | 8K      | Llama3       | Yes         | $0.00000003-$0.00000006     |
| Liquid: LFM 40B MoE                         | 40B                | 32K     | Other        | Yes         | $0.00000015                  |
| Liquid: LFM 7B                              | 7B                 | 32K     | Other        | Yes         | $0.00000001                  |
| Liquid: LFM 3B                              | 3B                 | 32K     | Other        | Yes         | $0.00000002                  |
| 01.AI: Yi Large                             | Unknown            | 32K     | Yi           | Yes         | $0.000003                    |
| AI21: Jamba Instruct                        | Unknown            | 256K    | Other        | No          | $0.0000005-$0.0000007        |
| AI21: Jamba 1.5 Large                       | Unknown            | 256K    | Other        | No          | $0.000002-$0.000008          |
| AI21: Jamba 1.5 Mini                        | Unknown            | 256K    | Other        | No          | $0.0000002-$0.0000004        |
| Inflection: Inflection 3 Pi                 | Unknown            | 8K      | Other        | No          | $0.0000025-$0.00001          |
| Inflection: Inflection 3 Productivity       | Unknown            | 8K      | Other        | No          | $0.0000025-$0.00001          |
| Rocinante 12B                               | 12B                | 32K     | Qwen         | Yes         | $0.00000025-$0.0000005       |
| NVIDIA: Llama 3.1 Nemotron 70B Instruct     | 70B                | 131K    | Llama3       | Yes         | $0.00000012-$0.0000003       |
| NVIDIA: Llama 3.1 Nemotron 70B Instruct (free) | 70B            | 131K    | Llama3       | Yes         | Free                         |
| Amazon: Nova Pro 1.0                       | Unknown            | 300K    | Nova         | No          | $0.0000008-$0.0000032        |
| Amazon: Nova Lite 1.0                      | Unknown            | 300K    | Nova         | No          | $0.00000006-$0.00000024      |
| Amazon: Nova Micro 1.0                     | Unknown            | 128K    | Nova         | No          | $0.000000035-$0.00000014     |
| Mancer: Weaver (alpha)                     | Unknown            | 8K      | Llama2       | Yes         | $0.0000015-$0.00000225       |
| Noromaid 20B                               | 20B                | 8K      | Llama2       | Yes         | $0.0000015-$0.00000225       |
| Rogue Rose 103B v0.2 (free)                | 103B               | 4K      | Llama2       | Yes         | Free                         |
| Hugging Face: Zephyr 7B (free)             | 7B                 | 4K      | Mistral      | Yes         | Free                         |
| MiniMax: MiniMax-01                        | 456B               | 1M      | Other        | No          | $0.0000002-$0.0000011        |
| XAI: Grok 2 Vision 1212                    | Unknown            | 32K     | Grok         | No          | $0.000002-$0.00001           |
| XAI: Grok 2 1212                           | Unknown            | 131K    | Grok         | No          | $0.000002-$0.00001           |
| XAI: Grok Vision Beta                      | Unknown            | 8K      | Grok         | No          | $0.000005-$0.000015          |
| XAI: Grok Beta                             | Unknown            | 131K    | Grok         | No          | $0.000005-$0.000015          |
| Auto Router                                | N/A                | 2M      | Router       | No          | Variable                      |

---

## Cost Tier Explanation (per 1K tokens)

- **Free**: No cost to use  
- **Very Low**: < $0.001 (less than $0.001 per 1K tokens)  
- **Low**: $0.001-$0.01 (between $0.001 and $0.01 per 1K tokens)  
- **Medium**: $0.01-$0.1 (between $0.01 and $0.1 per 1K tokens)  
- **High**: > $0.1 (more than $0.1 per 1K tokens)

---

## Learning LLM Building: Key Model Types To Study

- **Base Models**: Study foundational architectures (Llama 3/3.1/3.2, Mistral, Qwen2, etc.)  
- **MoE Models**: Examine Mixture of Experts (DeepSeek R1, Mixtral 8x7B/8x22B)  
- **Alternative Architectures**: Look at Mamba (state space models), Jamba (SSM-Transformer)  
- **Parameter Efficient Models**: Small but powerful (Phi-3, Ministral, Gemma)  
- **Open Source Frontier Models**: Llama 3.1 405B, Mixtral 8x22B, and DeepSeek R1  

---
# RAG Model Selection Guide

> Including OpenAI model recommendations

## Essential Factors for RAG Success

1. **Context Window Size** - Larger windows allow more retrieved documents to be included
2. **Information Synthesis** - Ability to combine multiple sources into coherent answers
3. **Factual Accuracy** - Tendency to accurately represent retrieved information
4. **Cost Efficiency** - Value relative to performance for production applications
5. **Speed** - Response time for interactive applications

## Refined Model Recommendations

### Best Overall RAG Models

1. **Gemini Pro 1.5**
   * 2M token context window (largest available)
   * Cost: $0.00125-$0.005 per 1K tokens
   * Strong synthesis capabilities for retrieved information
   * Best choice when maximum context is the priority

2. **Claude 3.5 Sonnet**
   * 200K token context window
   * Cost: $0.003-$0.015 per 1K tokens
   * Superior information synthesis and reasoning
   * Excels at maintaining factual accuracy from sources
   * Better instruction following than most alternatives

### Best Value for Production

1. **Gemini 2.0 Flash**
   * 1M token context window
   * Cost: $0.0000001-$0.0000004 per 1K tokens
   * Excellent balance of large context and affordability
   * Good for production systems with significant retrieval needs

2. **Claude 3.5 Haiku**
   * 200K token context window
   * Cost: $0.0008-$0.004 per 1K tokens
   * Faster response times than Sonnet
   * Strong reasoning with slightly reduced capabilities
   * Good for interactive RAG applications

### Most Cost-Effective

1. **Mistral Small**
   * 32K token context window
   * Cost: $0.0000002-$0.0000006 per 1K tokens
   * Remarkably cheap for its capabilities
   * Sufficient for most standard RAG applications
   * Best choice for cost-sensitive deployments

### For Development/Testing

1. **Llama 3.1 8B Instruct (free)**
   * 131K token context window
   * Free tier available
   * Good for iterative development and testing
   * Allows rapid prototyping without costs

### Where OpenAI Models Fit

1. **GPT-4o**
   * 128K token context window
   * Cost: $0.0025-$0.01 per 1K tokens
   * Excellent for complex reasoning and precise instruction following
   * Best OpenAI option for sophisticated RAG applications
   * Great at generating structured outputs from retrieved information

2. **o1-mini**
   * 128K token context window
   * Cost: $0.0011-$0.0044 per 1K tokens
   * Strong capabilities with dedicated reasoning mode
   * Good balance of performance and cost within OpenAI lineup

3. **GPT-3.5 Turbo**
   * 16K token context window
   * Cost: $0.0005-$0.0015 per 1K tokens
   * Most cost-effective OpenAI option
   * Good for simpler RAG applications
   * Suitable when budget constraints exist but you need OpenAI quality

## Which Models to pick 
## Recommended Resources

- [Llama 3 Technical Paper](https://ai.meta.com/research/publications/llama-3-a-more-capable-and-aligned-large-language-model-family/)
- [Mistral AI Technical Reports](https://mistral.ai/news/)
- [DeepSeek R1 Technical Report](https://arxiv.org/abs/2312.08673)
- [Mixtral MoE Paper](https://arxiv.org/abs/2401.04088)
- [Microsoft Phi-3 Technical Report](https://arxiv.org/abs/2404.14219)
- [Hugging Face Documentation](https://huggingface.co/docs)
- [Papers With Code LLM Section](https://paperswithcode.com/task/language-modelling)
