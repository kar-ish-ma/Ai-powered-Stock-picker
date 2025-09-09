#  AI-Powered Stock Picker

An **AI-driven stock research and selection system** built using [CrewAI](https://github.com/joaomdmoura/crewai).  
This project automates the process of **discovering trending companies, researching their financial health, and recommending the best stock to invest in**, while also sending real-time push notifications.  

It simulates a **financial analyst team** with specialized AI agents that work together like a research desk:
-  **News Analyst** scans headlines for trending companies.  
-  **Financial Researcher** investigates market standing and growth potential.  
-  **Stock Picker** makes the final call and notifies the user.  
-  **Manager Agent** coordinates the entire workflow.  



##  Key Features

-  **Finds trending companies** from the latest financial news in your chosen sector.  
-  **Generates in-depth financial reports** including market position, future outlook, and investment suitability.  
-  **Selects the most promising stock** for investment (avoids duplicate picks).  
-  **Sends push notifications** with final decisions and rationale.  
-  **Smart Memory System**  
  - **Long-Term Memory** – stores knowledge persistently across sessions (SQLite).  
  - **Short-Term Memory** – keeps context using RAG (retrieval-augmented generation).  
  - **Entity Memory** – tracks details about specific companies/entities.  
-  **Configurable via YAML** – Agents, roles, and tasks are fully customizable.  
- **Transparent Outputs** – JSON and Markdown reports generated for each step.  



##  How It Works

The Stock Picker system follows a **multi-step AI workflow**:  

### 1. **Find Trending Companies**
- Agent: `Trending Company Finder`
- Role: Financial news analyst  
- Task: Search the latest news in the selected sector.  
- Output: `output/trending_companies.json` (list of companies + tickers + reasons for trending).  

---

### 2. **Research Trending Companies**
- Agent: `Financial Researcher`  
- Role: Senior financial analyst  
- Task: Analyze each trending company in detail:  
  - Market position  
  - Competitive analysis  
  - Future outlook  
  - Investment potential  
- Output: `output/research_report.json` (comprehensive research report).  



### 3. **Pick Best Company**
- Agent: `Stock Picker`  
- Role: Equity selection expert  
- Task: Review research reports and select the **best stock**.  
- Output:  
  - Sends a **push notification** with 1-sentence rationale.  
  - Generates `output/decision.md` (detailed explanation of decision).  



### 4. **Manager Oversight**
- Agent: `Manager`  
- Role: Oversees the workflow, delegates tasks, ensures smooth execution.  



##  Task Flow Diagram
flowchart TD
    A[Find Trending Companies] --> B[Research Trending Companies]
    B --> C[Pick Best Company]
    C --> D[Push Notification + Final Report]
