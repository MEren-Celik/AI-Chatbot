# 🤖 Pasha — AI Teaching Assistant

A generative AI chatbot built as a customizable teaching assistant, powered by Google's Gemini (Gemma 3 27B) and served through a Gradio web interface. Users can dynamically adjust Pasha's personality — from warm and encouraging to strict and academic — and toggle whether the assistant challenges or accepts student responses.

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-UI-orange?logo=gradio)
![Gemini](https://img.shields.io/badge/Google-Gemini_API-4285F4?logo=google&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

---

## Overview

Pasha is an AI teaching assistant designed to adapt to different learning preferences. The core idea is that the same LLM can behave very differently depending on how its **system prompt** is constructed — and Pasha puts that control directly in the user's hands.

### Key Features

- **Adjustable Tone Slider** — Slide between three teaching styles:
  - 🟢 *Friendly* (0–33): Casual, encouraging, uses positive reinforcement
  - 🟡 *Balanced* (34–65): Patient, uses guiding questions and real-world examples
  - 🔴 *Academic* (66–100): Formal, precise terminology, holds students to high standards

- **Skepticism Toggle** — Switch between two response attitudes:
  - *Obedient*: Accepts student statements and builds on them
  - *Skeptical*: Challenges claims, asks for evidence, promotes critical thinking

- **Custom Gradio UI** — Styled interface with branded navy/red theme, SVG logo, and example prompts

- **Conversation Memory** — Maintains full chat history within a session for contextual follow-ups

---

## How It Works

The chatbot dynamically generates a system prompt based on the user's slider and radio button selections. This system prompt is prepended to the conversation history on every API call, meaning the assistant's personality can be changed mid-conversation.

```
User adjusts controls → System prompt is rebuilt → Full message history + new prompt sent to Gemini → Response streamed back
```

### Architecture

```
┌──────────────┐     ┌───────────────────┐     ┌──────────────┐
│  Gradio UI   │────▶│  System Prompt    │────▶│  Gemini API  │
│  (Controls)  │     │  Generator        │     │  (Gemma 3)   │
│  - Tone      │     │  - Tone mapping   │     │              │
│  - Skepticism│     │  - Attitude logic │     │              │
└──────────────┘     └───────────────────┘     └──────────────┘
```

---

## Getting Started

### Prerequisites

- Python 3.10+
- A [Google Gemini API key](https://ai.google.dev/)

### Installation

```bash
# Clone the repository
git clone https://github.com/MEren-Celik/AI-Chatbot.git
cd AI-Chatbot

# Install dependencies
pip install litellm gradio

# Set your API key
export GEMINI_API_KEY="your-api-key-here"
```

### Run

Open `Chat_Bot.ipynb` in Jupyter or Google Colab and run all cells. The Gradio interface will launch with a shareable public link.

---

## Example Interactions

| Tone | Skepticism | User Prompt | Pasha's Approach |
|------|-----------|-------------|-----------------|
| Friendly | Obedient | "What is a neural network?" | Warm explanation with analogies and encouragement |
| Academic | Skeptical | "I think gradient descent always finds the global minimum" | Formal correction, asks for proof, introduces counterexamples |
| Balanced | Obedient | "Can you help me understand recursion?" | Step-by-step walkthrough with real-world examples |

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| LLM | Google Gemma 3 27B (via Gemini API) |
| API Wrapper | LiteLLM |
| Frontend | Gradio (Blocks API) |
| Language | Python |

---

## Project Context

Built as part of the London Business School analytics programme, exploring how system prompt engineering can shape LLM behavior for educational applications.

---

## License

This project is licensed under the MIT License.
