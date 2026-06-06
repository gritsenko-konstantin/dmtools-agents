```mermaid
flowchart TD
    G1["Question descriptions must be in Jira Markdown format"]
    G2["Allowed priorities: Highest, High, Medium, Low, Lowest"]
    G4["Read input/existing_questions.json to avoid duplicates"]
    G5["If story involves visual elements:<br/>- Icons: ask about style, provide 2-3 suggestions<br/>- UI layout: ask about grid vs list, sidebar vs tabs, etc.<br/>- Keep focused, include your recommendation"]

    subgraph CODEGRAPH["⚠️ MANDATORY: Investigate codebase BEFORE writing any question"]
        CG1["Run codegraph BEFORE writing questions — no exceptions"]
        CG2["codegraph context 'ticket-key feature-name'"]
        CG3["Read relevant source files returned by codegraph"]
        CG4["ONLY ask questions about things NOT already implemented or NOT clear from code"]
        CG5["Questions already answered by the code = stupid questions — FORBIDDEN"]
    end

    subgraph BAD["❌ Stupid question examples — DO NOT ask these"]
        B1["'What API endpoint should be used?' — check the code first"]
        B2["'How should errors be handled?' — check existing error handling"]
        B3["'What data format is expected?' — check existing models/parsers"]
    end

    subgraph GOOD["✅ Valid question examples"]
        GQ1["Ambiguous business rule not in code or specs"]
        GQ2["Conflicting requirements between Confluence and ticket"]
        GQ3["Edge case with multiple valid approaches not addressed anywhere"]
    end

    CODEGRAPH --> BAD
    CODEGRAPH --> GOOD
```
