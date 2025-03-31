## 1. Project Overview

This project documents my ongoing journey in learning, building, and iterating on Large Language Model (LLM) applications. The initial focus is on developing text-to-text interactions, establishing a solid foundation before potentially expanding to image and sound capabilities in the future. The methodology involves a structured, iterative approach, starting with fundamental techniques and progressing towards more complex implementations.

## 2. Methodology and Approach

### 2.1. Iterative Development Strategy

Building effective LLM applications often requires an iterative process. My approach follows a path of increasing sophistication:

1.  **Prompt Engineering:** Mastering the art of crafting effective prompts to guide LLM behavior for specific tasks. This is the foundational layer.
2.  **Retrieval-Augmented Generation (RAG):** Implementing systems where the LLM's knowledge is augmented with external, retrieved information to provide more accurate, context-specific, and up-to-date responses.
3.  **Fine-tuning:** Adapting pre-trained LLMs to specific domains or tasks by further training them on custom datasets (to be explored later in the project).

While these appear as distinct stages, they are interconnected. Strong prompt engineering is vital for effective RAG and fine-tuning analysis. This project aims to build proficiency across these areas.

### 2.2. Core Requirement: Model Flexibility

A key initial requirement is the ability to easily experiment with and switch between different LLMs. This flexibility is crucial for:

*   Testing various model capabilities against specific tasks.
*   Comparing performance, cost, and output quality.
*   Staying adaptable as new models emerge.

### 2.3. Provider Selection: OpenRouter

To achieve model flexibility, I have selected [OpenRouter](https://openrouter.ai) as the primary API provider.

*   **Rationale:** OpenRouter provides a unified API endpoint that allows hot-swapping between a wide variety of models from different providers (OpenAI, Anthropic, Meta, Google, Mistral, etc.). This significantly simplifies the experimentation process.
*   **Alternative:** [Together.ai](https://together.ai) is considered a viable alternative provider.
*   **Note:** While OpenRouter offers excellent flexibility, it has occasionally been known to apply content filtering or censorship to its outputs. This is a factor being monitored, but its model variety currently makes it the most suitable choice for the project's goals.

## 3. Current Status: Phase 1 - Model Exploration & Initial Prompt Engineering

The project is currently in its initial phase, focusing on model exploration via OpenRouter and foundational prompt engineering techniques.

### 3.1. Model Landscape Research (OpenRouter)

A comprehensive survey of models available through OpenRouter (as of early March 2025) has been conducted. This involved compiling detailed information including model families, parameters (where available), context window size, architecture, cost, and open-source status.

*   This extensive list serves as a reference for selecting models for different tasks and understanding the current LLM landscape accessible via the chosen provider.
*   **Reference:** See **Appendix A: Complete OpenRouter AI Model Listing** for the full dataset, cost tier explanations, and key model types identified for study.
*   **Reference:** See **Appendix B: RAG Model Selection Guide (Preliminary)** for factors and initial model recommendations considered for future RAG implementation.

### 3.2. Initial Model Selection for Development

Based on the research and the need for cost-effective development cycles, the following models have been selected for initial prompt engineering experiments:

*   `meta-llama/llama-3.1-8b-instruct:free` (Leveraging OpenRouter's free tier for rapid prototyping)
*   Google's Gemma family models (Specifically exploring Gemma 2/3 variants as noted in experiments below)

### 3.3. Prompt Engineering Exploration

The current focus is on understanding and applying various prompt engineering techniques. This is crucial for controlling and optimizing LLM outputs without modifying the underlying model.

**Techniques Under Review:**

*   Zero-shot Prompting
*   Few-shot Prompting
*   Chain of Thought (CoT) Prompting (Manual and Automatic)
*   Self-Consistency
*   Knowledge Prompting
*   Prompt Chaining
*   Tree of Thought (ToT)
*   Retrieval-Augmented Generation (RAG - as a prompting strategy initially)
*   Automatic Reasoning and Tool-use (ReAct)
*   Structured Prompting Frameworks (e.g., TELER, TASK)

**Initial Experiments & Observations:**

*   **Zero-shot Prompting:** Successfully used for basic instruction following without examples.
    *   *Example Task:* Classify place names.
    *   *Prompt:*
        ```
        Classify the names of places in this paragraph - Text: Shahpur is the place where I grew up, you grew up in Germany or Pataliputra
        ```
    *   *Observed Output (Model Dependent):*
        ```
        Here's the classification of place names in the paragraph:
        1. Shahpur - Place name (likely a town or village...)
        2. Germany - Country name (...)
        3. Pataliputra - Historical place name (...)
        All three are geographical place names...
        ```

*   **Few-shot Prompting:** Providing examples within the prompt to guide the model's output format and reasoning.
    *   *Example Task 1:* Simple classification with examples.
    *   *Prompt:*
        ```
        Shahpur:Place, Germany: Place, Cat: Animal, Table?
        ```
    *   *Observed Output:*
        ```
        Table: Object
        A table is a piece of furniture...
        ```
    *   *Example Task 2:* Reasoning task (Odd/Even Sum). *Reference: [PromptingGuide.ai](https://www.promptingguide.ai/techniques/fewshot)*
    *   *Prompt:*
        ```
        The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
        A: The answer is False.
        The odd numbers in this group add up to an even number: 17, 10, 19, 4, 8, 12, 24.
        A: The answer is True.
        The odd numbers in this group add up to an even number: 16, 11, 14, 4, 8, 13, 24.
        A: The answer is True.
        The odd numbers in this group add up to an even number: 17, 9, 10, 12, 13, 4, 2.
        A: The answer is False.
        The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.
        A:
        ```
    *   *Observation & Model Difference:* This specific few-shot prompt yielded different results depending on the model used, highlighting the importance of model selection and testing even for seemingly simple prompts.
        *   **Gemma 2 27B Output:** `A: The answer is True.` *(Incorrect reasoning based on the provided examples)*
        *   **Gemma 3 27B Output:**
            ```
            Let's analyze the pattern:
            * False: Odd numbers are 9 and 1. 9 + 1 = 10 (even). The answer should be True.
            * True: Odd numbers are 17 and 19. 17 + 19 = 36 (even).
            * True: Odd numbers are 11 and 13. 11 + 13 = 24 (even).
            * False: Odd numbers are 17, 9, and 13. 17 + 9 + 13 = 39 (odd).
            * Previous Answer: Odd numbers are 15, 5, 7, and 1. 15 + 5 + 7 + 1 = 28 (even).

            The pattern seems to be checking if the *sum* of the odd numbers is even...
            Now, let's apply this to the last example:
            The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.
            1. Identify odd numbers: 15, 5, 13, 7, 1
            2. Count odd numbers: There are 5 odd numbers (an odd number of odd numbers).
            3. Sum odd numbers: 15 + 5 + 13 + 7 + 1 = 41 (odd)
            Therefore, the statement is false.
            A: The answer is False.
            ```
        *   *Insight:* This demonstrates that newer/different models (like Gemma 3 vs Gemma 2) can exhibit improved reasoning or instruction following capabilities, reinforcing the need for model flexibility and experimentation.

## 4. Roadmap and Next Steps

1.  **Continue Prompt Engineering:** Further explore and experiment with advanced techniques like CoT, Self-Consistency, and structured prompting frameworks across selected models. Document findings and best practices.
2.  **Develop RAG Prototype:** Begin implementing a basic RAG system using one of the value-focused models identified (e.g., Gemini 2.0 Flash, Claude 3.5 Haiku, or potentially GPT-4o/o1-mini depending on complexity needs and budget).
3.  **Iterate and Evaluate:** Systematically evaluate the performance of different models and prompting strategies for specific tasks (initially text classification, summarization, Q&A).
4.  **Explore Fine-tuning (Future):** Investigate fine-tuning smaller, open-source models (like Llama 3 variants) on specific datasets once a solid understanding of prompting and RAG is established.
5.  **Expand Modalities (Long-term):** Consider incorporating image and sound capabilities as the project progresses and foundational text-based skills are solidified.

## 5. Recommended Resources

The following resources are being used for reference and further learning:

*   [Llama 3 Technical Paper](https://ai.meta.com/research/publications/llama-3-a-more-capable-and-aligned-large-language-model-family/)
*   [Mistral AI Technical Reports](https://mistral.ai/news/)
*   [DeepSeek R1 Technical Report](https://arxiv.org/abs/2312.08673)
*   [Mixtral MoE Paper](https://arxiv.org/abs/2401.04088)
*   [Microsoft Phi-3 Technical Report](https://arxiv.org/abs/2404.14219)
*   [Hugging Face Documentation](https://huggingface.co/docs)
*   [Papers With Code LLM Section](https://paperswithcode.com/task/language-modelling)
*   [PromptingGuide.ai](https://www.promptingguide.ai/)

---

## Appendix A: Complete OpenRouter AI Model Listing (as of March 1st, 2025)

*This comprehensive reference guide includes AI models available via OpenRouter, organized by provider. It aids in selecting models for study and experimentation.*

**Table of Contents**
- [OpenAI Models](#openai-models-appendix)
- [Anthropic Models](#anthropic-models-appendix)
- [Meta (Llama) Models](#meta-llama-models-appendix)
- [Google Models](#google-models-appendix)
- [Mistral AI Models](#mistral-ai-models-appendix)
- [DeepSeek Models](#deepseek-models-appendix)
- [Cohere Models](#cohere-models-appendix)
- [Qwen Models](#qwen-models-appendix)
- [Microsoft Models](#microsoft-models-appendix)
- [Community and Merged Models](#community-and-merged-models-appendix)
- [Specialized/Niche Models](#specializedniche-models-appendix)
- [Cost Tier Explanation (per 1K tokens)](#cost-tier-explanation-appendix)
- [Learning LLM Building: Key Model Types To Study](#key-model-types-appendix)

---

### OpenAI Models (Appendix)

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

### Anthropic Models (Appendix)

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

### Meta (Llama) Models (Appendix)

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

### Google Models (Appendix)

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

### Mistral AI Models (Appendix)

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

### DeepSeek Models (Appendix)

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

### Cohere Models (Appendix)

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

### Qwen Models (Appendix)

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

### Microsoft Models (Appendix)

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

### Community and Merged Models (Appendix)

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

### Specialized/Niche Models (Appendix)

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

### Cost Tier Explanation (Appendix - per 1K tokens)

*   **Free**: No cost to use
*   **Very Low**: < $0.001 (less than $0.001 per 1K tokens)
*   **Low**: $0.001-$0.01 (between $0.001 and $0.01 per 1K tokens)
*   **Medium**: $0.01-$0.1 (between $0.01 and $0.1 per 1K tokens)
*   **High**: > $0.1 (more than $0.1 per 1K tokens)
    *Note: Costs often vary between input (prompt) and output (completion) tokens. Ranges reflect this where applicable.*

---

### Key Model Types To Study (Appendix - Learning LLM Building)

*   **Base Models**: Foundational architectures (Llama 3/3.1/3.2, Mistral, Qwen2, etc.) provide understanding of core transformer designs.
*   **MoE Models**: Mixture of Experts (DeepSeek R1, Mixtral 8x7B/8x22B) demonstrate parameter-efficient scaling techniques.
*   **Alternative Architectures**: Mamba (state space models), Jamba (SSM-Transformer hybrid) show emerging non-transformer or hybrid approaches.
*   **Parameter Efficient Models**: Small but powerful models (Phi-3, Ministral, Gemma) highlight capabilities achievable with fewer parameters.
*   **Open Source Frontier Models**: Large-scale open models (Llama 3.1 405B, Mixtral 8x22B, DeepSeek R1) represent the cutting edge of accessible model architectures.

---

## Appendix B: RAG Model Selection Guide (Preliminary)

*This section outlines factors and top contenders identified for future Retrieval-Augmented Generation (RAG) implementations, including considerations for OpenAI models.*

### Essential Factors for RAG Success

1.  **Context Window Size:** Larger windows allow more retrieved documents to be included, potentially improving answer quality and relevance.
2.  **Information Synthesis:** The model's ability to effectively combine information from multiple retrieved sources into a coherent, accurate answer.
3.  **Factual Accuracy / Faithfulness:** The model's tendency to accurately represent the information contained within the provided context (retrieved documents) and avoid hallucination.
4.  **Cost Efficiency:** The balance between performance and cost, crucial for deploying applications at scale.
5.  **Speed (Latency):** Response time, particularly important for interactive RAG applications.

### Refined Model Recommendations (Preliminary Shortlist)

*These models represent strong candidates based on initial research for various RAG use cases.*

**Best Overall RAG Models:**

1.  **Gemini Pro 1.5:** Largest context window (2M tokens), strong synthesis. Ideal when maximum context is paramount. (Cost: Low)
2.  **Claude 3.5 Sonnet:** Large context (200K tokens), excellent synthesis, reasoning, and faithfulness. A top contender for quality. (Cost: Low)

**Best Value for Production:**

1.  **Gemini 2.0 Flash:** Very large context (1M tokens) at extremely low cost. Excellent balance for production systems. (Cost: Very Low)
2.  **Claude 3.5 Haiku:** Large context (200K tokens), faster than Sonnet, good reasoning. Suitable for interactive RAG. (Cost: Very Low)

**Most Cost-Effective:**

1.  **Mistral Small:** Sufficient context (32K tokens) at extremely low cost. Best for highly cost-sensitive deployments with standard RAG needs. (Cost: Very Low)

**For Development/Testing:**

1.  **Llama 3.1 8B Instruct (free):** Good context (131K tokens) with a free tier available on OpenRouter. Ideal for rapid prototyping without cost barriers.

**Where OpenAI Models Fit:**

1.  **GPT-4o:** Good context (128K tokens), top-tier reasoning, instruction following, and structured output generation. Premium OpenAI option for complex RAG. (Cost: Low)
2.  **o1-mini:** Good context (128K tokens), strong capabilities, especially reasoning-focused tasks. Good performance/cost balance within OpenAI. (Cost: Low)
3.  **GPT-3.5 Turbo:** Smaller context (16K tokens), but the most cost-effective OpenAI option. Suitable for simpler RAG tasks under budget constraints. (Cost: Very Low/Low)