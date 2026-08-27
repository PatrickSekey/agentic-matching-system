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
