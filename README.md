# ⚡ AirGap PromptForge

An ultra-lightweight, offline-first prompt generator engineered to force Large Language Models (LLMs) to build complete, production-ready web applications in strict air-gapped environments.

## 🌟 The Problem & The Impact

When prompting AIs to build complex web apps, developers face two major bottlenecks:
1. **Token Truncation:** The AI stops generating mid-script due to output limits, breaking the codebase and requiring tedious manual stitching.
2. **Dependency Hell in Secure Nets:** AI defaults to using React, Tailwind, and external CDNs. These are entirely useless in secure, air-gapped enterprise networks (e.g., defense, heavy industry, finance) with no internet access.

**The Effect (Why it matters):** AirGap PromptForge completely eliminates these issues. It dynamically calculates code complexity and forces the AI to output the architecture in **strategic, byte-sized chunks (P1, P2, P3...)**. It strictly enforces **Vanilla JS, inline CSS, and inline SVGs**, ensuring the AI generates a standalone, single-file HTML application that runs flawlessly offline without a single external web request.

## ✨ Core Features

- **Air-Gapped Ready (Zero Dependencies):** Generates prompts that strictly forbid external CDNs. 100% offline fallback using system fonts and inline assets.
- **Smart Token-Bypass (Auto-Chunking):** Real-time text analysis automatically recommends the safest output split (1 to 5 parts) to bypass LLM token cutoff limits.
- **Dynamic Context Inference:** Auto-detects if your app needs time-series data tracking, version control, or simple overwrites based on semantic keyword analysis in your requirements.
- **Multi-LLM Optimized:** Contains pre-engineered system instructions uniquely tailored for Claude, ChatGPT, Gemini, Grok, and Google AI Mode.
- **Local History Engine:** Automatically saves your configurations locally using `localStorage` (Max 100 entries) with instant search capabilities.
- **Native I18n:** Built-in UI support for English, Korean, Japanese, Chinese, German, and French.

## 🚀 How to Use

1. **Launch Locally:** Double-click the `index.html` file in any modern browser. No local server or Node.js required.
2. **Define Requirements:** Enter your app's name, purpose, and detailed core logic (numbered lists work best).
3. **Configure Architecture:** Select UI theme (Dark/Light/Industrial), layout options, and Data I/O requirements (JSON, CSV, API sync).
4. **Generate & Copy:** Click `Copy to Clipboard`.
5. **Feed the LLM:** Paste the prompt into your AI of choice. 
6. **Sequential Retrieval:** After the AI generates "Part 1" and pauses, type "Next" or "Continue" to fetch the remaining parts.
7. **Merge & Run:** Combine all generated code blocks (````html`) sequentially into a single `.html` file and run it offline.

## 🛠 Tech Stack

- **100% Vanilla HTML / CSS / JS**
- No Build Step
- No Webpack / Vite
- No External Libraries
