# Candidate Resume Screening
An automated candidate screening pipeline that ingests concatenated PDF resume batches, extracts individual candidate profiles using layout and header heuristic matching, and evaluates qualifications against a structured rubric.

🏗️ Overview

        
        [ Batch PDFs ] 
              │
              ▼
        ┌────────────────────────────────────────────────────────┐
        │ 1. Ingestion & Boundary Detection                      │
        │    • PyMuPDF (fitz) text extraction                    │
        │    • Regex heuristic matching (Email & Phone headers)  │
        │    • Outputs Pandas DataFrame (file_name, candidate_id)│
        └───────────────────────────┬────────────────────────────┘
                                    │
                                    ▼
        ┌────────────────────────────────────────────────────────┐
        │ 2. Primary Assessment (LLM Screener)                   │
        │    • Formats candidate text + grading rubric           │
        │    • Enforces structured JSON output                   │
        └───────────────────────────┬────────────────────────────┘
                                    │
                                    ▼
        ┌────────────────────────────────────────────────────────┐
        │ 3. LLM-as-a-Judge (Auditor)                            │
        │    • Validates primary scoring against source text     │
        │    • Flags hallucinations & generates decision summary │
        └────────────────────────────────────────────────────────┘


