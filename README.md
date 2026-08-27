# 🤖 Agentic Profile Matching System

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![LangGraph](https://img.shields.io/badge/LangGraph-0.0.20+-green.svg)](https://github.com/langchain-ai/langgraph)
[![OpenRouter](https://img.shields.io/badge/OpenRouter-API-orange.svg)](https://openrouter.ai/)
[![Gradio](https://img.shields.io/badge/Gradio-4.0+-purple.svg)](https://gradio.app/)

> **An intelligent agentic workflow for automated candidate screening and matching using LangGraph**

## 📋 Project Overview

The **Agentic Profile Matching System** is a sophisticated multi-agent workflow built with LangGraph that automates the entire candidate screening process. It uses a team of specialized AI agents to parse job descriptions, search resumes, rank candidates, and generate comprehensive match reports - all with human-in-the-loop feedback capabilities.

### 🎯 Key Features

- **🏗️ Multi-Agent Architecture**: 7 specialized agents working in sequence
- **💬 Conversational Interface**: Natural language queries for hiring managers
- **📊 Multi-Round Screening**: Top 10 → Deep Analysis → Final Recommendations
- **🔍 Explainable AI**: Detailed match reports with strengths and gaps
- **🔄 Iterative Refinement**: Adjust requirements and re-rank candidates
- **🎯 Tool Integration**: Resume search, comparison, interview question generation

## 📁 Assignment Requirements

This project fulfills all requirements for the **Agentic Profile Matching** assignment:

### ✅ Part A: Agent Architecture (40%)

| Requirement | Implementation |
|-------------|----------------|
| **Agent State Design** | Comprehensive `State` TypedDict with conversation history, job requirements, candidate shortlist, and reasoning |
| **Agent Workflow** | Complete LangGraph with START → Parse JD → Extract Requirements → Search Resumes → Rank Candidates → Generate Report → Human Feedback → END |
| **File System Tools** | Full integration with Colab file system |
| **RAG Search Tool** | Candidate resume search and filtering |
| **Custom Tools** | `extract_requirements()`, `compare_candidates()`, `generate_interview_questions()` |

### ✅ Part B: Interactive Features (30%)

| Requirement | Implementation |
|-------------|----------------|
| **Conversational Interface** | Gradio UI with natural language query support |
| **Natural Language Queries** | "Compare the top 3 candidates", "Why did Alice rank higher?", "Generate interview questions" |
| **Iterative Refinement** | Human feedback loop for requirement adjustment |

### ✅ Part C: Advanced Capabilities (30%)

| Requirement | Implementation |
|-------------|----------------|
| **Multi-Round Screening** | Initial screen (top 10), deep analysis (top 10), final recommendations (top 5) |
| **Explainability** | Detailed match reports with strengths, gaps, and match scores |
| **Improvement Suggestions** | Gap analysis for borderline candidates |

## 🏗️ System Architecture

### State Machine Diagram

```mermaid
flowchart TD
    START([START]) --> P1

    subgraph P1["Phase 1: Requirements"]
        A1["Parse Job Description"] --> A2["Extract Skills"]
        A2 --> A3["Extract Experience"]
        A3 --> A4["Requirements Complete"]
    end

    P1 --> P2

    subgraph P2["Phase 2: Candidate Search"]
        B1["Search Resumes"] --> B2["Filter Experience"]
        B2 --> B3["Filter Skills"]
        B3 --> B4["Candidates Found"]
    end

    P2 --> P3

    subgraph P3["Phase 3: Ranking"]
        C1["Score Required Skills"] --> C2["Score Preferred Skills"]
        C2 --> C3["Score Experience"]
        C3 --> C4["Calculate Total Score"]
        C4 --> C5["Generate Ranking"]
        C5 --> C6["Top 10 Candidates"]
    end

    P3 --> P4

    subgraph P4["Phase 4: Reporting"]
        D1["Generate Report"] --> D2["Highlight Strengths"]
        D2 --> D3["Identify Gaps"]
        D3 --> D4["Create Recommendations"]
    end

    P4 --> P5

    subgraph P5["Phase 5: Human Feedback Loop"]
        E1["Process Query"] --> E2{"Query Type"}
        
        E2 -->|Compare| E3["Compare Candidates"]
        E2 -->|Why / Explain| E4["Explain Rankings"]
        E2 -->|Interview| E5["Generate Questions"]
        E2 -->|Strengths / Gaps| E6["Show Profile"]
        
        E3 --> E7["Return Result"]
        E4 --> E7
        E5 --> E7
        E6 --> E7
        
        E7 --> E1
        E7 --> E8["Complete"]
    end

    P5 --> P6

    subgraph P6["Phase 6: Final Decision"]
        F1["Evaluate Top 5"] --> F2{"Score Check"}
        
        F2 -->|">= 80%"| F3["HIRE"]
        F2 -->|"60-79%"| F4["CONSIDER"]
        F2 -->|"< 60%"| F5["REJECT"]
    end

    P6 --> END([END])

    %% Styling
    style START fill:#90EE90,stroke:#333,stroke-width:2px
    style END fill:#90EE90,stroke:#333,stroke-width:2px

    style P1 fill:#E6F3FF,stroke:#4A90E2,stroke-width:2px
    style P2 fill:#E6F3FF,stroke:#4A90E2,stroke-width:2px
    style P3 fill:#E6F3FF,stroke:#4A90E2,stroke-width:2px
    style P4 fill:#E6F3FF,stroke:#4A90E2,stroke-width:2px

    style P5 fill:#FFF3CD,stroke:#D6A700,stroke-width:2px
    style P6 fill:#F8D7DA,stroke:#C0392B,stroke-width:2px

    style F3 fill:#90EE90,stroke:#333,stroke-width:2px
    style F4 fill:#FFF3CD,stroke:#333,stroke-width:2px
    style F5 fill:#F8D7DA,stroke:#333,stroke-width:2px
```
🛠️ Technology Stack
LangGraph - Agentic workflow orchestration

LangChain - LLM framework and tools

OpenRouter - Unified LLM API access

Gradio - Interactive UI interface

Python 3.8+ - Core programming language

🚀 Getting Started
Installation
bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/agentic-profile-matching.git
cd agentic-profile-matching

# Install dependencies
pip install -r requirements.txt
Running the System
Option 1: Gradio UI (Recommended)
bash
python matching_agent.py
Option 2: CLI Mode
bash
python matching_agent.py --cli
Option 3: Google Colab
Open the notebook in Colab and run all cells in order.

Configuration
Set up OpenRouter API Key:

Sign up at OpenRouter

Get your API key

The system will prompt you for it

Customize Sample Data:

Edit the create_sample_candidates() function

Add your own candidate resumes
