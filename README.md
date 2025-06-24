# RAG Diagnostic AI: Practical Healthcare Assistant

Welcome! This project is a real-world demonstration of how advanced AI can assist both patients and healthcare professionals in understanding symptoms, getting recommendations, and learning the reasoning behind AI-powered diagnoses. Built with a focus on robustness, privacy, and maintainability, this system is ready for both research and production use.

---

## Project Overview
- **Purpose:**
  - Provide an interactive, multi-turn healthcare assistant that can ask follow-up questions, give likely diagnoses, and explain its reasoning in plain language.
  - Showcase a production-grade OpenAI API key rotation system for reliability and quota management.
- **Who is this for?**
  - **Non-technical users:** Try out the AI assistant in your browser, no coding required.
  - **Technical users:** Study or extend the codebase for research, production, or further development.

---

## How It Works (Simple Terms)
1. **You describe your symptoms** in the chat interface.
2. **The AI asks smart follow-up questions** to clarify your condition.
3. **After a few questions,** the AI gives a likely diagnosis and a recommendation (e.g., see a doctor, try home remedies).
4. **You also get an explanation** in plain English about why the AI reached its conclusion.
5. **All AI responses are powered by OpenAI’s GPT models** (if enabled), with automatic key rotation to avoid downtime.

---

## Key Features & Architecture
- **Multi-Agent Design:**
  - `DiagnosticAgent`: Handles symptom analysis and follow-ups.
  - `RecommendationAgent`: Gives actionable advice.
  - `ExplanationAgent`: Explains the reasoning behind diagnoses and recommendations.
  - `AgentOrchestrator`: Coordinates the conversation.
- **OpenAI API Key Rotation:**
  - Store multiple keys in a `.env` file (never in code!).
  - The system randomly rotates keys for each request, ensuring reliability and quota balancing.
- **Streamlit UI:**
  - Clean, tabbed interface for Profile, Chat, and Diagnosis.
  - Responsive design for desktop and mobile.
  - All critical actions (e.g., "Submit Symptom") use a professional gradient style for clarity and accessibility.
- **Privacy:**
  - No user data is stored or sent anywhere except to OpenAI for LLM-powered responses.
  - `.env` is never committed to version control.

---

## Quick Start: For Anyone

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/rag_diagnostic_ai.git
cd rag_diagnostic_ai
```

### 2. Install Requirements
```bash
pip install -r requirements.txt
```

### 3. Set Up OpenAI API Keys
- **Copy `.env.example` to `.env`:**
  ```bash
  cp .env.example .env
  ```
- **Edit `.env` and add your real OpenAI API keys:**
  ```
  OPENAI_API_KEYS=sk-...yourkey1...,sk-...yourkey2...
  ```
  (Comma-separated, no spaces. You can use one or more keys.)

### 4. Run the App
```bash
streamlit run app.py
```
- Open the link in your browser (usually http://localhost:8501).
- Start chatting!

---

## For Technical Users: Architecture & Extending
- **All OpenAI calls go through `utils/openai_client.py`** for key rotation and maintainability.
- **Add new agents or logic** by extending the `agents/` directory and updating the orchestrator.
- **Environment variables** are loaded automatically via `python-dotenv`.
- **Testing:**
  - Run `pytest` to check core logic.
  - For real OpenAI integration, run agent scripts directly (e.g., `python -m agents.explanation_agent`).

---

## Troubleshooting & FAQ
- **No response from AI?**
  - Check your `.env` file and make sure your keys are valid and not exhausted.
- **UI looks strange?**
  - Make sure you’re using a modern browser and have not edited `styles.css`.
- **Quota errors?**
  - Add more OpenAI keys to `.env` for better rotation.
- **Want to see which key is used?**
  - Add a print statement in `utils/openai_keys.py` in `get_random_openai_key()`.

---

## Security & Privacy
- **Never commit `.env` to git!**
- **Share `.env.example` only** (it contains placeholders, not real keys).
- **All user data is ephemeral and local.**

---

## Acknowledgements
- Built and maintained by a senior research assistant for demonstration and practical use.
- Powered by OpenAI’s GPT models for natural language understanding.

---

**Questions? Want to contribute?**
- Open an issue or pull request, or contact the maintainer.

Enjoy exploring the future of AI-powered healthcare!
