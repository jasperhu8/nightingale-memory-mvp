# Memory Comparison Plan – Mem0 vs Amigo

### Author: Hongrui Hu  
### Date: Oct 19, 2025  
### Context: Nightingale Memory MVP Prototype (Tasks 2, 3, 5)

---

## 1. Background and Scope
Due to the short project timeline, I focused the comparative study on **two memory frameworks** that are most relevant and well-documented:
- **Mem0** – A hybrid vector + graph memory designed for persistent context recall and efficiency.  
- **Amigo** – A layered architecture (episodic, semantic, declarative) emphasizing structured retrieval and interpretability.

Both models represent distinct approaches to agent memory:  
Mem0 favors **lightweight scalability and token efficiency**,  
while Amigo focuses on **interpretable structure and layered recall**.

---

## 2. Evaluation Focus
Given time constraints, the analysis and testing are focused on **three main dimensions** that are critical for real-time medical conversational AI:

1. **Memory Duration** –  
   How long and effectively the system retains context across multiple sessions or interactions.

2. **Accuracy of Recall** –  
   Whether retrieved memory is relevant, coherent, and factually consistent with prior context.

3. **Training and Runtime Cost** –  
   Proxy indicator: estimated training time or compute intensity required to update and maintain the memory store (relates to deployment cost).

---

## 3. Testing Approach and Pipeline Design

### Step 1: Mock Data Setup
- Create 3–5 short simulated doctor–patient dialogue sessions.  
- Each session includes several exchanges (symptom → diagnosis → follow-up).  
- Save these as structured JSON to ensure consistency across systems.

### Step 2: Memory Insertion
- Feed each conversation sequentially into both memory systems.  
- For Mem0, use vector/graph APIs or local embeddings to simulate persistence.  
- For Amigo, mimic episodic → semantic → declarative consolidation (simplified mock).

### Step 3: Retrieval Test
- Query both systems with context-dependent prompts such as:
  - “What did the patient report about chest pain previously?”
  - “When was the last medication change?”
- Measure whether the retrieved content includes the correct and relevant details.

### Step 4: Metrics Logging
| Metric | Description | Unit |
|--------|--------------|------|
| Memory Retention Span | Number of sessions correctly recalled | sessions |
| Recall Accuracy | % of correctly retrieved facts | % |
| Latency | Average response time per retrieval | ms |
| Training / Update Time | Time to update or insert new memory | ms or s |

---

## 4. Expected Observations

| Dimension | Mem0 | Amigo |
|------------|------|--------|
| Memory Duration | Persistent, efficient recall with hybrid structure | Structured long-term recall via layered consolidation |
| Accuracy | High consistency in retrieval, lower interpretability | Interpretable, topic-based retrieval but slower |
| Training / Cost | Lightweight, API-friendly; low cost | Heavier compute for consolidation, slower updates |

---

## 5. Next Steps
- Integrate the mock comparison pipeline into the MVP’s T2 (Intent) and T3 (Retrieval) modules.  
- Collect latency and accuracy metrics using local test logs.  
- Summarize trade-offs in the final README with key insights for MVP selection.

---

## 6. Notes and Limitations
This plan focuses on conceptual validation and mock tests rather than full-scale implementation, due to limited time.  
Real benchmarks will require access to both frameworks’ APIs and cloud compute for vector persistence and multi-session testing.

---
