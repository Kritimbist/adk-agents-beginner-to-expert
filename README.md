# ADK_Basic

> **Hands-on code and examples for the [ADK Crash Course](https://codelabs.developers.google.com/onramp/instructions) — a beginner-to-expert master class for building multi-agent AI systems using Google's Agent Development Kit (ADK) and Gemini.**

---

# 🤖 ADK Crash Course — From Beginner to Expert

> **A hands-on master class for building sophisticated multi-agent AI systems using Google's Agent Development Kit (ADK)**

[![Google ADK](https://img.shields.io/badge/Google%20ADK-v1.5.0-blue?style=flat-square&logo=google)](https://google.github.io/adk-docs/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-yellow?style=flat-square&logo=python)](https://www.python.org/)
[![Gemini](https://img.shields.io/badge/Powered%20by-Gemini-8B5CF6?style=flat-square&logo=google)](https://deepmind.google/technologies/gemini/)
[![License](https://img.shields.io/badge/License-Apache%202.0-green?style=flat-square)](https://www.apache.org/licenses/LICENSE-2.0)
[![Colab](https://img.shields.io/badge/Open%20in-Colab-F9AB00?style=flat-square&logo=googlecolab)](https://colab.research.google.com/)

---

## 📖 Overview

This repository accompanies the [ADK Crash Course Codelab](https://codelabs.developers.google.com/onramp/instructions) — a comprehensive, hands-on journey into building AI agents that can **reason**, **plan**, and **use tools** to accomplish complex, real-world tasks.

Forget simple chatbots. This course takes you from zero to building fully autonomous multi-agent systems using Google's **Agent Development Kit (ADK)**.

---

## 🎯 What You'll Learn

By completing this course, you will be able to:

- **Build Your First AI Agent** — Go from zero to a functional agent that uses Google Search and generates detailed responses
- **Master Custom Tools** — Connect agents to your own APIs and Python functions (e.g., real-time weather forecasts)
- **Construct Multi-Agent Systems** — Use the *Agent-as-a-Tool* pattern to build teams of specialized AI agents
- **Orchestrate Complex Workflows** — Implement Routers, Sequential Chains, Loops, and Parallel Execution patterns
- **Give Your Agents Memory** — Enable agents to handle follow-up questions and manage multi-step tasks via session management

---

## 📓 Course Notebooks

| Notebook | Topics Covered | Open in Colab |
|----------|----------------|---------------|
| **Colab 1: Tools & Memory** | First Agent, Custom Tools, Agent-as-a-Tool, Memory | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.sandbox.google.com/drive/1zzTZ8t6aYFbsyrWpGAtmirNdA9R-bbWz) |
| **Colab 2: MultiAgents** | Router, Sequential, Loop, Parallel Agents | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.sandbox.google.com/drive/10aC9vrBD8y_UlR9CcmuXuvBBPnkZ8i7M) |

---

## 🗺️ Course Roadmap

```
Session 1 → Your First Agent (Runner)
Session 2 → Custom Tools 🛠️
Session 3 → Agent-as-a-Tool 🧑‍🍳
Session 4 → Agent Memory 🧠
Session 5 → Router Agent 🚏
Session 6 → SequentialAgent ⛓️
Session 7 → LoopAgent 🔁
Session 8 → ParallelAgent ⚡️
```

---

## 📚 Sessions

### Session 1 — Your First Agent with Runner
Build a `day_trip_agent` that generates full-day trip itineraries. Learn the three core components of every ADK interaction:
- **Agent** — The brain: instructions, model, and tools
- **Session** — Conversational memory and history
- **Runner** — The execution engine that processes queries

### Session 2 — Custom Tools 🛠️
Unlock agent potential by connecting to custom Python functions and external APIs. Build a `weather_agent` powered by a real-time National Weather Service tool.

> 💡 **Key Insight:** The ADK automatically parses function docstrings to understand tool behavior — your docstring *is* your tool's contract.

### Session 3 — Agent-as-a-Tool 🧑‍🍳
Build a multi-layered agent system with a full delegation chain:

```
trip_data_concierge_agent (Orchestrator)
├── db_agent          → Fetches hotel data
└── concierge_agent
    └── food_critic_agent → Suggests restaurants
```

### Session 4 — Agent Memory 🧠
Understand why session management is critical. Compare:
- ✅ **With Memory** — Agent handles follow-ups, feedback, and multi-turn plans
- ❌ **Without Memory** — Agent loses context between turns ("amnesia")

> 🔑 **Rule:** One continuous conversation requires one continuous session.

### Session 5 — Router Agent 🚏
Build a master dispatcher agent that analyzes user queries and routes them to the right specialist:
- `foodie_agent` → restaurant & food queries
- `weekend_guide_agent` → events & activities
- `transportation_agent` → directions & travel

### Session 6 — SequentialAgent ⛓️
Execute agents in a predefined order with **shared state**. Output from one agent flows automatically as input to the next — no manual wiring needed.

```
User Query → foodie_agent (output_key="destination") → transportation_agent ({destination}) → Response
```

### Session 7 — LoopAgent 🔁
Build "perfectionist" agents that plan, critique, and refine their own work:

```
planner_agent → [critic_agent → refiner_agent] × N → exit_loop → Final Plan
```
The loop runs until the critic approves the output or `max_iterations` is reached.

### Session 8 — ParallelAgent ⚡️
Run multiple independent agents concurrently, then synthesize their results:

```
                ┌─ museum_finder  ──┐
User Query ──▶  ├─ concert_finder ──┤ ──▶ synthesis_agent ──▶ Response
                └─ restaurant_finder┘
```

---

## 🚀 Local Setup

### Prerequisites

| Requirement | Version |
|-------------|---------|
| Python | 3.8+ |
| google-adk | 1.5.0 (Python 3.9+) / 0.3.0 (Python 3.8) |
| Google AI Studio API Key | [Get one here](https://aistudio.google.com/) |

---

### 🍎 Mac / Linux Setup

**Step 1 — Clone the Repository**
```bash
git clone https://github.com/cuppibla/ADK_Basic.git
cd ADK_Basic
```

**Step 2 — Set Up Virtual Environment**

Option A — Automated (Recommended):
```bash
chmod +x setup_venv.sh
./setup_venv.sh
```

Option B — Manual:
```bash
python3 -m venv .adk_env
source .adk_env/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

**Step 3 — Configure Environment Variables**

> ⚠️ **Don't skip this step!**

```bash
touch agent/.env
open agent/.env
```

Add the following to `agent/.env`:
```env
GOOGLE_GENAI_USE_VERTEXAI=FALSE
GOOGLE_API_KEY=your_actual_api_key_here
```

**Step 4 — Activate & Run**
```bash
source .adk_env/bin/activate
adk web
```

**Step 5 — Open Browser**

Navigate to `http://localhost:8000`, select `agent` from the dropdown, and start chatting!

---

### 🪟 Windows Setup

**Step 1 — Clone the Repository**
```cmd
git clone https://github.com/cuppibla/ADK_Basic.git
cd ADK_Basic
```

**Step 2 — Set Up Virtual Environment**

Option A — Automated (Recommended):
```cmd
setup_venv.bat
```

Option B — Manual (Command Prompt):
```cmd
python -m venv .adk_env
.adk_env\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```

Option B — Manual (PowerShell):
```powershell
python -m venv .adk_env
.adk_env\Scripts\Activate.ps1
pip install --upgrade pip
pip install -r requirements.txt
```

**Step 3 — Configure Environment Variables**

> ⚠️ **Don't skip this step!**

```cmd
type nul > agent\.env
notepad agent\.env
```

Add the following to `agent/.env`:
```env
GOOGLE_GENAI_USE_VERTEXAI=FALSE
GOOGLE_API_KEY=your_actual_api_key_here
```

**Step 4 — Activate & Run**
```cmd
.adk_env\Scripts\activate
adk web
```

**Step 5 — Open Browser**

Navigate to `http://localhost:8000`, select `agent` from the dropdown, and start chatting!

---

## 🔧 Troubleshooting

| Platform | Issue | Fix |
|----------|-------|-----|
| Mac/Linux | `python` not found | Use `python3` instead |
| Mac/Linux | Permission denied on setup script | Run `chmod +x setup_venv.sh` |
| Windows | PowerShell execution policy error | Run `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` |

---

## ☁️ GCP Setup (for Vertex AI)

1. **Enable Billing** — Claim your [$5 free credit](https://goo.gle/adkcodelab) (no credit card needed)
2. **Create a GCP Project** — Go to [Google Cloud Console](https://console.cloud.google.com/) and create a new project
3. **Link Billing Account** — Open the left panel → Billing → link your trial account
4. **Copy Project ID** — Use the project selector dropdown → "All" tab → copy your Project ID

---

## 📁 Project Structure

```
ADK_Basic/
├── agent/
│   ├── .env                  # API keys (⚠️ never commit this)
│   └── ...                   # Agent definitions
├── requirements.txt          # Python dependencies
├── setup_venv.sh             # Mac/Linux setup script
├── setup_venv.bat            # Windows setup script
└── README.md
```

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/cuppibla/ADK_Basic/issues).

---

## 📄 License

This project is licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0).  
Codelab content is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/).

---

## 🙏 Acknowledgements

- [Google Agent Development Kit (ADK)](https://google.github.io/adk-docs/)
- [Google Codelabs](https://codelabs.developers.google.com/)
- [Gemini Models](https://deepmind.google/technologies/gemini/)

---

<p align="center">Made with ❤️ using Google ADK · <a href="https://codelabs.developers.google.com/onramp/instructions">View the full Codelab</a></p>
