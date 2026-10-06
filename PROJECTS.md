# Project Roadmap

This file tracks the three projects I am using to deepen my understanding of recommendation systems, generative recommendation, and AI infrastructure.

## 1. Generative Recommendation System

**Goal:** Build a production-style recommender that starts with strong classical baselines and progressively evolves into a generative recommendation system.

### Milestones

- [ ] Dataset and reproducible evaluation pipeline
- [ ] Popularity / matrix-factorization baselines
- [ ] Two-tower retrieval baseline
- [ ] Sequential recommendation baseline (SASRec-style)
- [ ] Semantic ID construction
- [ ] RQ-VAE / residual quantization experiments
- [ ] TIGER-style generative retrieval
- [ ] Compare random, semantic, and collaborative ID schemes
- [ ] Constrained decoding over valid item IDs
- [ ] Hybrid GenRec + classical retrieval system
- [ ] Online inference service
- [ ] Latency / throughput / GPU benchmark report

### Questions to investigate

- When do Semantic IDs outperform arbitrary item IDs?
- How sensitive is GenRec to codebook size and ID depth?
- What failure modes appear as the catalog changes?
- When does hybrid retrieval outperform pure generative retrieval?
- How should generative recommendation be batched and cached in production?

---

## 2. LLM Serving Lab

**Goal:** Understand modern inference systems by implementing and benchmarking the pieces that production frameworks optimize.

### Milestones

- [ ] Minimal autoregressive inference server
- [ ] Streaming responses
- [ ] Request queue and async execution
- [ ] KV-cache instrumentation
- [ ] Static batching
- [ ] Continuous batching
- [ ] Scheduling and cancellation
- [ ] Prefix caching experiments
- [ ] Load shedding / overload protection
- [ ] Multi-GPU serving
- [ ] Compare against vLLM
- [ ] Ray Serve deployment
- [ ] Benchmark TTFT, TPOT, QPS, p50/p95 latency, and GPU utilization

### Questions to investigate

- Why does continuous batching improve throughput?
- How does sequence length affect KV-cache pressure?
- What scheduling policy gives the best latency/throughput tradeoff?
- When does prefix caching materially help?
- Where do bottlenecks move as concurrency increases?

---

## 3. Personalized AI Feed

**Goal:** Build an end-to-end recommendation product combining retrieval, ranking, generative recommendation, and production ML infrastructure.

### Candidate architecture

```text
content ingestion
      ↓
feature / embedding pipeline
      ↓
candidate generation
 ├─ collaborative retrieval
 ├─ semantic retrieval
 └─ trending retrieval
      ↓
ranking model
      ↓
GenRec / LLM reranking
      ↓
personalized feed
```

### Milestones

- [ ] Content ingestion pipeline
- [ ] User-event schema and simulator
- [ ] Embedding service
- [ ] Candidate retrieval services
- [ ] Ranking model
- [ ] Diversity / freshness reranking
- [ ] GenRec integration
- [ ] Feature / embedding cache
- [ ] Online recommendation API
- [ ] Observability and latency dashboards
- [ ] Offline-to-online evaluation workflow
- [ ] Experiment / A-B testing framework

---

## Portfolio Strategy

The projects are intentionally related:

```text
Recommendation fundamentals
        ↓
Sequential recommendation
        ↓
Semantic IDs + GenRec
        ↓
Transformer inference
        ↓
Serving / batching / GPU systems
        ↓
End-to-end personalized product
```

The goal is to be able to discuss the same body of work from three interview angles: **Recommendation Systems**, **ML Systems**, and **AI Infrastructure**.
