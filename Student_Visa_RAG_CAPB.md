# Mini-Project #3: Real-World RAG Implementation
## RAG Agent for Student Visa & Study Abroad Procedures

## 1. Project Context & Use Case

### 1.1 Problem / Context
International students face confusing steps when they apply to study abroad. F-1 visa procedures, I-20 rules, SEVIS payments, DS-160 instructions, and interview requirements are spread across many government and university pages. Students ask the same questions over and over, and most of them do not know which source is reliable.

The goal of this project is to build a small RAG agent that answers common questions about the F-1 student visa process using official sources from the U.S. Department of State, SEVP, and university international student offices. The system shares factual, high-level steps and links to the original sources. It does not give legal advice or predict outcomes.

### 1.2 Primary Use Case
Q&A over policies and manuals.

### 1.3 Users / Audience
- Prospective international students
- Parents
- High school counselors
- University advisors

### 1.4 Success Criteria

```yaml
context:
  domain: "Student visa and study abroad procedures (F-1)"
  use_case: "Q&A over official policy and application steps"
  users: ["international students", "parents", "school counselors"]
  success:
    - "≥80% correct answers on evaluation set"
    - "100% of answers have at least one citation"
    - "≤4s average latency"
    - "No answers provide personalized legal advice"
```

## 2. Data & Constraints

### 2.1 Corpus Details
Sources include:
- U.S. Department of State F-1 visa pages
- SEVP student pages
- USCIS student pages
- International student pages from selected colleges
- NGO study guides

Formats: HTML, PDF  
Size: 20–40 documents

### 2.2 Constraints

```yaml
data_constraints:
  sources:
    - "Official U.S. F-1 visa pages"
    - "SEVP and USCIS student pages"
    - "University international student office guides"
  formats: ["html", "pdf"]
  size: "20–40 docs"
  local_only: false
  cost_limit: "low cost or free credits"
  latency_target: 4
  security: "no private data, public sources only"
```

Additional constraints:
- Must support non-technical users  
- Must avoid legal advice  
- Must warn users to confirm details with official sources  
- Policies change often  

## 3. RAG Architecture (MVP)

### 3.1 Pipeline
Ingestion → Chunking → Embedding → Vector Store → Retrieval → LLM Generation → Safety Layer

### 3.2 Design Choices

```yaml
architecture_mvp:
  steps: ["ingest", "chunk", "embed", "store", "retrieve", "generate", "postprocess"]
  chunking: "heading-based, 256–512 tokens with small overlap"
  embeddings: "OpenAI text-embedding-3-small"
  vector_db: "Chroma"
  retrieval: "vector-only top_k=5"
  llm: "GPT-4.1 mini"
  citations: true
  safety_layer: true
  rationale: "Simple pipeline with enough accuracy for structured visa documents"
```

## 4. Component Alternatives (Mini-Bakeoff)

```yaml
component_selection:
  vector_db:
    options: ["FAISS", "Chroma"]
    selected: "Chroma"
    reason: "simple local setup"
  embeddings:
    options: ["OpenAI", "BGE-small"]
    selected: "OpenAI"
    reason: "strong multilingual accuracy"
  retrieval:
    options: ["vector-only", "hybrid"]
    selected: "vector-only"
    reason: "good enough for structured text"
  llm:
    options: ["GPT-4.1 mini", "local 7B"]
    selected: "GPT-4.1 mini"
    reason: "better policy reasoning"
  reranker:
    selected: "None"
    reason: "time limit"
```

## 5. Evaluation Plan & Results (Has not been conducted yet)

### 5.1 Test Set
15 questions covering:
- Visa steps  
- Required documents  
- Timing  
- SEVIS and DS-160  
- Travel rules  
- Denial scenarios  

### 5.2 Results

```yaml
evaluation:
  questions: 15
  baseline:
    approach: "vector-only"
    correct: TBD
    partially_correct: TBD
    incorrect_or_unsafe: TBD
    with_citations: TBD
    avg_latency: TBD
  notes: "TBD"
```

## 6. Risks, Edge Cases & Future Work

### Edge Cases
- Long government PDFs  
- Policy changes  
- Country-specific differences  
- Students with past visa issues  

### Risks
- Possible hallucinations  
- Outdated data  
- Misinterpretation as legal advice  

### Future Work

```yaml
improvements:
  - "add hybrid retrieval"
  - "add reranker"
  - "add classifier for legal-risk questions"
  - "schedule reindexing each semester"
  - "output structured checklists for common visa steps"
```

## 7. References
- U.S. Department of State F-1 Visa pages  
- SEVP “Study in the States”  
- USCIS Student Guide  
- Awesome RAG GitHub lists  
- Chroma documentation
