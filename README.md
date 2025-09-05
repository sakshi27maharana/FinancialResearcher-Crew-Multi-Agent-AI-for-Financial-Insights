---

# 💰 FinancialResearcher Crew: Multi-Agent AI for Financial Insights

Welcome to **FinancialResearcher Crew** — a powerful template built on [crewAI](https://crewai.com) that makes setting up **multi-agent AI systems** simple, flexible, and impactful.

With FinancialResearcher Crew, you can orchestrate intelligent agents that collaborate on financial research and analysis — combining their strengths to maximize collective intelligence and deliver deep insights.

---

## 🛠️ Installation

### Requirements

* **Python**: `>=3.10` and `<3.14`
* **Dependency Manager**: [UV](https://docs.astral.sh/uv/)

### Step 1: Install UV

If not already installed, run:

```bash
pip install uv
```

### Step 2: Install Dependencies

Navigate to your project folder and install requirements:

```bash
uv pip install -r requirements.txt
```

Or, lock dependencies and install via the CLI:

```bash
crewai install
```

---

## ⚙️ Customization

Before running the crew, configure it to match your needs:

1. **Set up your API key**

   * Add your `GROQ_API_KEY` to the `.env` file

2. **Configure your crew**

   * `src/financial_researcher/config/agents.yaml` → Define agents
   * `src/financial_researcher/config/tasks.yaml` → Define tasks
   * `src/financial_researcher/crew.py` → Add logic, tools, and custom arguments
   * `src/financial_researcher/main.py` → Customize agent/task inputs

---

## ▶️ Running FinancialResearcher Crew

From the project root, run:

```bash
crewai run
```

This command will:

* Initialize your crew of financial research agents
* Assign them tasks as defined in your configs
* Generate a `report.md` file (default example: research on LLMs)

---

## 📰 Using SerperDevTool for Live Research

The **SerperDevTool** is a predefined tool available in [crewai-tools](https://pypi.org/project/crewai-tools/). It enables agents to **gather the latest news and search results** — making your financial analysis **current and dynamic**.

⚠️ **Note**: SerperDevTool requires an API key from [Serper.dev](https://serper.dev). It is **not free**, and you’ll need to sign up for an API key.

### How to Use SerperDevTool

1. Import the tool:

   ```python
   from crewai_tools import SerperDevTool
   ```

2. Pass the tool to your agent inside the crew definition:

   ```python
   @CrewBase
   class ResearchCrew():
       """Research crew for comprehensive topic analysis and reporting"""

       @agent
       def researcher(self) -> Agent:
           return Agent(
               config=self.agents_config['researcher'],
               verbose=True,
               tools=[SerperDevTool()]  # Enable live news & search capabilities
           )
   ```

3. Add your **SERPER\_API\_KEY** to the `.env` file:

   ```
   SERPER_API_KEY=your_api_key_here
   ```

Once enabled, your **research agents** will be able to:

* Search the web in real-time
* Access the latest financial news and market updates
* Enrich reports with **fresh, relevant insights**

---

## 📊 Example Use Case

Here’s how you might use **FinancialResearcher Crew** in practice:

**Goal:** *Generate a market trends report on AI investments in 2025*

1. Configure an agent as a `financial_analyst` in `agents.yaml`
2. Add a research task in `tasks.yaml` such as:

   ```yaml
   - id: market_research
     description: >
       Research the latest global investments in Artificial Intelligence for 2025,
       analyze market growth, and summarize key investment trends.
     expected_output: >
       A structured report with insights on investment patterns,
       key players, and future outlook.
   ```
3. Run the project:

   ```bash
   crewai run
   ```
4. Output:
   A `report.md` file containing a **comprehensive analysis** of AI investments in 2025, powered by live search (if SerperDevTool is enabled).

---

## 📝 Sample Report Output (Preview)

When you run the crew, a `report.md` file is generated in the root folder.
Here’s a preview of what it might look like:

```markdown
# 📈 Financial Research Report: AI Investments in 2025  

## Executive Summary  
The global AI investment market in 2025 is projected to exceed **$200B**, driven by increased funding in generative AI, autonomous systems, and AI-driven healthcare solutions.  

## Key Insights  
- **Generative AI Startups** attracted the highest funding rounds in Q1 2025.  
- **North America & Asia** lead the global investment landscape.  
- Venture capital firms are shifting focus from infrastructure AI to **applied AI solutions** in finance and healthcare.  

## Future Outlook  
By 2030, AI is expected to contribute over **$15T** to the global economy, with financial services being one of the top 3 sectors driving adoption.  
```

---

## 🤝 Understanding Your Crew

The **FinancialResearcher Crew** is a group of specialized AI agents:

* Each agent has **roles, goals, and tools**
* Tasks are orchestrated through `config/tasks.yaml`
* Capabilities and configurations live in `config/agents.yaml`

Together, they collaborate intelligently to deliver **comprehensive financial research and insights**.

---

✨ Empower your decision-making with the **collective intelligence of AI-driven financial research**.

---
