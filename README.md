# Awesome AI Character Engineering

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated collection of tools, frameworks, specifications, research, datasets and engineering resources for building persistent AI characters and companions.

AI characters are more than prompts.

A production character system may need persona conditioning, long-term memory, short-term conversational context, lore retrieval, character-card schemas, dialogue evaluation, voice synthesis, avatars, multimodal generation and safety systems.

This list focuses on the **engineering behind AI characters** rather than simply listing consumer companion apps.

## Contents

- Character Frameworks & Frontends
- Character Cards & Interchange Formats
- Character Design & Prompt Architecture
- Memory & Long-Term Context
- Lorebooks, RAG & World Models
- Role-Playing Models
- Evaluation & Benchmarks
- Research Papers & Surveys
- Voice & Speech
- Avatars & Embodiment
- Local Inference
- APIs & Model Routing
- Datasets
- Developer Guides & Case Studies
- Production Architecture
- Security, Privacy & Safety
- Related Awesome Lists

---

## Character Frameworks & Frontends

Open-source projects that can be used to build or study character-driven conversational systems.

### SillyTavern

https://github.com/SillyTavern/SillyTavern

Extensible LLM frontend designed around characters, personas, lorebooks, group conversations and role-playing. One of the most useful projects for understanding how mature character-chat interfaces structure prompts and context.

### RisuAI

https://github.com/kwaroran/RisuAI

Open-source AI role-playing frontend supporting character cards, multiple model providers and extensive prompt customization.

### TavernAI

https://github.com/TavernAI/TavernAI

One of the projects that helped popularize persistent character-card-based LLM conversations.

### KoboldAI

https://github.com/KoboldAI/KoboldAI-Client

Local AI text-generation ecosystem commonly used for interactive storytelling and role-playing.

### text-generation-webui

https://github.com/oobabooga/text-generation-webui

Flexible local LLM interface supporting numerous model formats and backends. Frequently used as an inference backend for character-chat systems.

---

## Character Cards & Interchange Formats

A character should ideally be portable rather than trapped inside a single application.

### Character Card V2 Specification

https://github.com/malfoyslastname/character-card-spec-v2

Specification for exchanging character definitions between compatible role-playing applications.

Typical fields include:

```text
name
description
personality
scenario
first_mes
mes_example
system_prompt
alternate_greetings
character_book
tags
creator
```

Understanding character-card formats is useful even if your application eventually uses its own internal schema.

### Character Card Parser

https://github.com/roleplay-studio/character-card

Parser and builder for multiple generations of character-card formats, including PNG-embedded character metadata.

### SillyTavern Character Documentation

https://docs.sillytavern.app/usage/characters/

Documentation covering character definitions and how character information gets incorporated into conversations.

---

## Character Design & Prompt Architecture

Resources covering the less obvious question:

**What information should an AI character actually contain?**

Character systems generally separate information such as:

```text
Identity
Description
Backstory
Personality
Traits
Scenario
Speaking style
Greeting
Example dialogue
Behavior rules
Relationship state
Memories
Lore
```

Keeping these concepts separate makes character behavior easier to update, evaluate and debug.

### Character Design — SillyTavern

https://docs.sillytavern.app/usage/characters/characterdesign/

Practical documentation about defining personalities and constructing character prompts.

### AI Character Creator: The Fields That Make a Character Hold Together

https://yourcrush.ai/blog/ai-character-creator

Practical breakdown of how fields such as description, backstory, greeting, personality traits, speaking style, memories and behavior settings contribute differently to a persistent AI character.

### Original Character Template

https://yourcrush.ai/blog/oc-template

Character-sheet structure for turning a written fictional character into structured information usable by interactive character systems.

---

## Memory & Long-Term Context

Memory is one of the defining technical problems in AI companions.

Simply sending the entire conversation to an LLM becomes increasingly expensive and eventually exceeds the context window.

Production systems commonly combine several techniques:

```text
Recent message window
       ↓
Conversation summarization
       ↓
Pinned / explicit memories
       ↓
Semantic retrieval
       ↓
Entity / relationship state
       ↓
Long-term memory store
```

### Letta

https://github.com/letta-ai/letta

Framework for stateful agents with persistent memory and identity. Originally developed as MemGPT.

Particularly useful for studying architectures where agents actively manage their own memory.

### Mem0

https://github.com/mem0ai/mem0

Memory layer for AI applications designed to extract and retrieve useful information about users and previous interactions.

### Zep

https://github.com/getzep/zep

Memory infrastructure for conversational and agentic applications.

### LangGraph Memory

https://langchain-ai.github.io/langgraph/concepts/memory/

Documentation and patterns for maintaining short-term and long-term state in graph-based LLM applications.

---

## Lorebooks, RAG & World Models

Memories answer:

> What happened between the user and character?

Lore answers:

> What is true about the character's world?

Keeping these separate is extremely useful.

A typical retrieval pipeline might look like:

```text
User message
     │
     ├── Recent conversation
     ├── Character identity
     ├── Relevant memories
     ├── Relevant lore entries
     └── Current relationship/world state
                ↓
              LLM
```

### SillyTavern World Info

https://docs.sillytavern.app/usage/core-concepts/worldinfo/

Keyword and contextual retrieval system used to dynamically insert relevant world information into character conversations.

### LlamaIndex

https://github.com/run-llama/llama_index

Data framework for retrieval-augmented LLM applications that can be adapted for world lore, character knowledge and long-form story context.

### LangChain

https://github.com/langchain-ai/langchain

General LLM application framework containing retrieval, memory and orchestration primitives relevant to character systems.

---

## Role-Playing Models

Models and projects specifically intended for role-playing, persona simulation or long-form conversational interaction.

### CharacterGLM

https://github.com/thu-coai/CharacterGLM-6B

Character-oriented conversational language model project from Tsinghua University's conversational AI group.

### CoSER

https://github.com/Neph0s/CoSER

Research project exploring coordinated simulation of established characters using large language models.

### RoleLLM

https://github.com/InteractiveNLP-Team/RoleLLM-public

Research and benchmark work focused on eliciting and evaluating role-playing abilities in language models.

---

## Evaluation & Benchmarks

"Feels like the character" is not a sufficient engineering metric.

Useful character evaluation dimensions include:

- Persona consistency
- Factual consistency
- Speaking-style consistency
- Memory recall
- Relationship continuity
- Contradiction rate
- Repetition
- Initiative
- Emotional appropriateness
- Instruction adherence
- Lore retrieval accuracy

### RoleLLM

https://github.com/InteractiveNLP-Team/RoleLLM-public

Benchmarking framework for evaluating role-playing behavior.

### CharacterEval

Search/resource category for benchmarks designed to evaluate character-level knowledge and behavioral consistency.

### MT-Bench

https://github.com/lm-sys/FastChat

Not character-specific, but useful as inspiration for constructing multi-turn conversational evaluation pipelines.

---

## Research Papers & Surveys

### From Persona to Personalization: A Survey on Role-Playing Language Agents

https://arxiv.org/abs/2404.18231

Survey covering role-playing language agents, persona simulation and personalization.

### RoleLLM: Benchmarking, Eliciting, and Enhancing Role-Playing Abilities of Large Language Models

https://arxiv.org/abs/2310.00746

Research into evaluating and improving the ability of LLMs to imitate assigned roles.

### CoSER: Coordinating LLM-Based Persona Simulation of Established Roles

https://arxiv.org/

Research into simulating established fictional characters and interactions.

### Awesome LLM Role Playing With Persona

https://github.com/Neph0s/awesome-llm-role-playing-with-persona

Large research-oriented collection of papers about character role-playing, persona simulation, personalization and related topics.

---

## Voice & Speech

Voice turns a text character into a multimodal companion.

A typical pipeline is:

```text
User microphone
      ↓
Speech-to-text
      ↓
Character LLM
      ↓
Text response
      ↓
Text-to-speech
      ↓
Audio
```

### Whisper

https://github.com/openai/whisper

Open-source speech-recognition model useful for speech-to-text pipelines.

### OpenVoice

https://github.com/myshell-ai/OpenVoice

Open-source voice cloning system supporting cross-lingual speech generation.

### GPT-SoVITS

https://github.com/RVC-Boss/GPT-SoVITS

Voice conversion and few-shot text-to-speech toolkit popular among character and voice applications.

### Piper

https://github.com/rhasspy/piper

Fast local neural text-to-speech system suitable for privacy-focused or offline companions.

---

## Avatars & Embodiment

Character systems do not necessarily need to stop at text.

Common representations include:

```text
Static portraits
Animated 2D sprites
Live2D
VRM / 3D avatars
Lip-synced avatars
Realtime video avatars
```

### three-vrm

https://github.com/pixiv/three-vrm

Three.js library for loading and controlling VRM avatars in web applications.

### VRM

https://vrm.dev/

Open avatar format commonly used for humanoid 3D characters.

### Live2D Cubism SDK

https://www.live2d.com/en/sdk/about/

SDK ecosystem for animating 2D character illustrations.

---

## Local Inference

Running models locally can reduce inference costs and enable private/offline companion systems.

### llama.cpp

https://github.com/ggerganov/llama.cpp

Highly optimized local inference engine supporting GGUF language models across a wide variety of hardware.

### Ollama

https://github.com/ollama/ollama

Simple local runtime and API for running language models.

### vLLM

https://github.com/vllm-project/vllm

High-throughput inference and serving engine appropriate for larger-scale deployments.

### ExLlamaV2

https://github.com/turboderp/exllamav2

Fast inference library optimized around quantized LLMs.

---

## APIs & Model Routing

Most production character applications eventually need to support more than one model.

Reasons include:

- outages
- model experimentation
- different cost tiers
- role-play quality differences
- context-window requirements
- latency
- moderation requirements

### LiteLLM

https://github.com/BerriAI/litellm

Unified interface and proxy for many LLM providers using an OpenAI-compatible API style.

### OpenRouter

https://openrouter.ai/

Model-routing API giving applications access to many hosted language models through a common interface.

---

## Datasets

Useful datasets may contain:

- persona descriptions
- multi-turn conversation
- fictional dialogue
- emotional dialogue
- relationship conversations
- speaker-labelled scripts
- role-playing conversations

### PersonaChat

https://huggingface.co/datasets/bavard/personachat_truecased

Persona-grounded conversational dataset designed around speakers maintaining assigned persona facts.

### DailyDialog

https://huggingface.co/datasets/li2017dailydialog

Human-written multi-turn conversational dataset with dialogue-act and emotion annotations.

---

## Developer Guides & Case Studies

Technical writing that explains practical character-system design.

### SillyTavern Documentation

https://docs.sillytavern.app/

One of the most complete practical references for understanding prompts, characters, personas, lorebooks, RAG and multi-character LLM interfaces.

### AI Character Creator: The Fields That Make a Character Hold Together

https://yourcrush.ai/blog/ai-character-creator

Field-by-field explanation of how a production character creator can represent identity, personality, backstory, greeting, traits, speaking style and memory separately rather than treating the character as a single system prompt.

### Letta Documentation

https://docs.letta.com/

Architecture and developer documentation for building stateful agents with persistent memory.

---

## Production Architecture

One possible architecture for a character platform:

```text
                   ┌─────────────────────┐
                   │       Client        │
                   │ Web / Mobile / Game │
                   └──────────┬──────────┘
                              │
                              ▼
                   ┌─────────────────────┐
                   │     Chat API        │
                   └──────────┬──────────┘
                              │
             ┌────────────────┼────────────────┐
             │                │                │
             ▼                ▼                ▼
      Character Store    Conversation DB   User Persona
             │                │                │
             └────────────────┼────────────────┘
                              │
                              ▼
                    Context Builder
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
          ▼                   ▼                   ▼
    Memory Retrieval     Lore Retrieval     Recent Context
          │                   │                   │
          └───────────────────┼───────────────────┘
                              ▼
                         Prompt Builder
                              │
                              ▼
                         Model Router
                              │
                 ┌────────────┴─────────────┐
                 ▼                          ▼
            Cloud Models                Local Models
                 │                          │
                 └────────────┬─────────────┘
                              ▼
                         Response
                              │
              ┌───────────────┼───────────────┐
              ▼               ▼               ▼
        Memory Update     Moderation       TTS/Image
```

This is not the only architecture, but it illustrates why character applications quickly become more complicated than a normal chatbot.

---

## Security, Privacy & Safety

Persistent characters introduce additional privacy considerations because remembering users is often an intentional product feature.

Developers should consider:

- Which messages are stored?
- What becomes long-term memory?
- Can users inspect stored memories?
- Can memories be edited?
- Can memories be deleted?
- Are embeddings deleted together with the source data?
- How long are conversations retained?
- Which third-party model providers receive messages?
- Can users export their characters?
- Can users export their conversation history?
- How is age-restricted content handled?
- How are public characters moderated?

Memory systems should make these behaviors explicit rather than invisible.

---

## Related Awesome Lists

### Awesome LLM Role Playing With Persona

https://github.com/Neph0s/awesome-llm-role-playing-with-persona

Academic papers and research concerning role-playing and persona-based language models.

### Awesome AI Companions

https://github.com/tomasz-buczek/awesome-ai-companions

Consumer-facing companion applications and related tools.

### Awesome AI Waifu

https://github.com/parallelarc/Awesome-AI-Waifu

Frameworks and applications related to AI waifu and virtual companion systems.

### Awesome ChatGPT

https://github.com/sindresorhus/awesome-chatgpt

Resources surrounding the broader conversational AI ecosystem.

---

## Contributing

Contributions are welcome.

A resource should provide genuine value to developers building or researching persistent AI characters.

### Good additions

- Open-source frameworks.
- Character interchange standards.
- Memory systems.
- Evaluation benchmarks.
- Peer-reviewed research.
- Well-documented technical experiments.
- High-quality engineering articles.
- Speech or avatar infrastructure directly relevant to characters.

### Not accepted

- Thin affiliate articles.
- SEO pages with no technical information.
- Generic "10 best AI girlfriend apps" articles.
- Referral links.
- Abandoned projects without historical significance.
- Sites submitted solely for promotion.

Commercial projects **may** be included when they publish a genuinely useful technical resource, specification, dataset, benchmark or engineering case study.

When proposing something you created or work on, disclose that relationship in the pull request.

Every submission should answer:

> What will a developer learn or be able to build after opening this resource?

---

## Disclosure

Some resources in this repository may be maintained by contributors to this list. Those relationships should be disclosed where applicable.

Inclusion does not imply endorsement.

---

## License

CC0 1.0 Universal.

To the extent possible under law, contributors waive copyright and related rights to this curated list.
