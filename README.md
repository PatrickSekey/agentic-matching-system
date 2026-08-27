# 🤖 Agentic Profile Matching System

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![LangGraph](https://img.shields.io/badge/LangGraph-0.0.20+-green.svg)
![OpenRouter](https://img.shields.io/badge/OpenRouter-API-orange.svg)
![Gradio](https://img.shields.io/badge/Gradio-4.0+-purple.svg)

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
graph TD
    A([START]) --> B[parse_jd_node]
    B --> C[search_resumes_node]
    C --> D[rank_candidates_node]
    D --> E[generate_report_node]
    E --> F[human_feedback_node]
    F --> G[final_recommendation_node]
    G --> H([END])
    
    style A fill:#90EE90
    style H fill:#90EE90
    style F fill:#FFD700
    style B fill:#87CEEB
    style C fill:#87CEEB
    style D fill:#87CEEB
    style E fill:#87CEEB
    style G fill:#FF6B6B

graph TD
    START([START]) --> Phase1[Phase 1: Requirements]
    
    subgraph Phase1[Phase 1: Requirements]
        A1[Parse JD] --> A2[Extract Skills]
        A2 --> A3[Extract Experience]
        A3 --> A4[Requirements Complete]
    end
    
    Phase1 --> Phase2[Phase 2: Candidate Search]
    
    subgraph Phase2[Phase 2: Candidate Search]
        B1[Search Resumes] --> B2[Filter Experience]
        B2 --> B3[Filter Skills]
        B3 --> B4[Candidates Found]
    end
    
    Phase2 --> Phase3[Phase 3: Ranking]
    
    subgraph Phase3[Phase 3: Ranking]
        C1[Score Required Skills] --> C2[Score Preferred Skills]
        C2 --> C3[Score Experience]
        C3 --> C4[Calculate Total Score]
        C4 --> C5[Generate Ranking]
        C5 --> C6[Top 10 Candidates]
    end
    
    Phase3 --> Phase4[Phase 4: Reporting]
    
    subgraph Phase4[Phase 4: Reporting]
        D1[Generate Report] --> D2[Highlight Strengths]
        D2 --> D3[Identify Gaps]
        D3 --> D4[Create Recommendations]
    end
    
    Phase4 --> Phase5[Phase 5: Interaction]
    
    subgraph Phase5[Phase 5: Human Feedback Loop]
        E1[Process Query] --> E2{Query Type}
        E2 -->|compare| E3[Compare Candidates]
        E2 -->|why/explain| E4[Explain Rankings]
        E2 -->|interview| E5[Generate Questions]
        E2 -->|strengths/gaps| E6[Show Profile]
        E3 --> E7[Return Result]
        E4 --> E7
        E5 --> E7
        E6 --> E7
        E7 --> E1[Continue Loop]
        E7 --> E8[Complete]
    end
    
    Phase5 --> Phase6[Phase 6: Final Decision]
    
    subgraph Phase6[Phase 6: Final Decision]
        F1[Evaluate Top 5] --> F2{Score Check}
        F2 -->|>= 80%| F3[HIRE]
        F2 -->|60-79%| F4[CONSIDER]
        F2 -->|< 60%| F5[REJECT]
    end
    
    Phase6 --> END([END])
    
    style START fill:#90EE90
    style END fill:#90EE90
    style Phase1 fill:#E6F3FF
    style Phase2 fill:#E6F3FF
    style Phase3 fill:#E6F3FF
    style Phase4 fill:#E6F3FF
    style Phase5 fill:#FFF3CD
    style Phase6 fill:#F8D7DA


