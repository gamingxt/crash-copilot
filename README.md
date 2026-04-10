# 🚨 Crash-Copilot: Autonomous AI Agent
> **AlgoFest 2026 Submission | AI/ML Track**

**An autonomous, local AI debugging agent that intercepts crashes before you see them.** Crash-Copilot wraps your standard execution commands, catches terminal errors instantly, and uses advanced LLM reasoning to generate an interactive HTML report with the root cause and the exact fixed code.

---

## 🏆 Why We Built This for AlgoFest
We built Crash-Copilot to solve the biggest bottleneck in development: parsing terminal spaghetti. 

- **Model Agnostic (BYOM):** We built this architecture to be entirely model-flexible. While our official submission uses **Z.AI's GLM-5.1** for its superior speed and context window, teams can easily swap in OpenAI, Anthropic, or even local open-source models to meet enterprise privacy requirements.
- **Innovation:** Instead of copying and pasting errors into ChatGPT, Crash-Copilot invisibly intercepts the `stderr` stream directly from your machine.
- **Technical Complexity:** Uses custom Regex to hunt down the exact broken file on your hard drive, extracts the context, and hands it to the reasoning engine.
- **Practical Impact:** Features a persistent local chat companion that holds your entire stack trace and local code in its context window for follow-up questions.

---

## ✨ Features

- 🔌 **Bring Your Own Model** — Configurable for GLM-5.1, GPT-4, Claude, or local LLMs.
- 🔍 **Instant AI Diagnosis** — Root cause, fixed code, and bullet-point explanation.
- 📋 **One-Click Copy** — Every code block has a clipboard button for immediate pasting.
- 💬 **Persistent Chat Companion** — Ask follow-up questions with full crash context.
- 🌐 **Auto-HTML UI** — Opens a stunning, styled HTML report directly in your browser.
- 🔒 **Zero Heavy Dependencies** — Uses Python `requests`, no complex framework installations.
- 🌍 **Language Agnostic** — Works with Python, Node.js, Go, Rust, Java, and more.

---

## 🚀 Quick Start (Local Setup)

### 1. Clone into your workspace
```bash
git clone [https://github.com/gamingfirext/crash-copilot.git](https://github.com/gamingfirext/crash-copilot.git)
```

### 2. Configure Your AI Model
```bash
cp crash-copilot/.env.example crash-copilot/.env
```
Edit `crash-copilot/.env` with your preferred AI provider. By default, it is optimized for Z.AI (GLM-5.1):
```env
# Default: Z.AI (GLM-5.1)
GLM_API_KEY=your_actual_api_key_here

# Optional: Swap to other providers if needed
# OPENAI_API_KEY=...
# ANTHROPIC_API_KEY=...
```

### 3. Install Global Command
Make `ccp` a global command on your machine.

**Windows:**
```bash
crash-copilot\install.bat
```
*(Open a new terminal after running)*

**macOS / Linux:**
```bash
chmod +x crash-copilot/install.sh && crash-copilot/install.sh
```

### 4. Run & Test
Wrap any normal run command with `ccp`. To test the AI workflow with a deliberate crash:
```bash
ccp python crash-copilot/script.py
```
If the script crashes, Crash-Copilot catches it, talks to the configured AI model, and opens the fix in your browser.

---

## ⚙️ Configuration

| Variable | Default | Description |
|---|---|---|
| `GLM_API_KEY` | *(required)* | Your Z.AI API key |
| `AI_MODEL` | `GLM-5.1` | The specific model string to use |

The `.env` is automatically discovered from the current directory up to 6 parent levels—no matter where you run `ccp` from.

---

## 👨‍💻 Team
- **Ashik** - Core Logic, AI Integration, & CLI Architecture
