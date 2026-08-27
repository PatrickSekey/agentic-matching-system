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


