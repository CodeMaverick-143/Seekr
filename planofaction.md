# SentinelSport - Plan of Action

## 1. Project Overview
SentinelSport is an AI-powered sports media protection platform designed to provide automated, affordable, and legally robust anti-piracy solutions. It targets mid-tier sports leagues and broadcasters, offering sub-second detection and rapid response to unauthorized redistributions.

### Core Objectives:
- **Combat Piracy:** Minimize revenue loss via automated detection.
- **Democratic Access:** High-end protection at an affordable price point.
- **Legal Robustness:** C2PA content provenance and blockchain-anchored evidence.
- **Automated Enforcement:** Rapid AI-generated DMCA notices.

---

## 2. Technical Stack
- **Backend:** Python 3.11+, FastAPI
- **Task Queue:** Celery with Redis
- **Database:** PostgreSQL + `pgvector` (for vector embeddings)
- **AI/ML:** PyTorch (OpenCLIP), ImageHash (pHash), FAISS (Vector Search), Claude API (LLM)
- **Provenance:** `c2pa-python` SDK, Web3.py (Polygon/Amoy Testnet)
- **Frontend:** React 18+, Tailwind CSS, Chart.js
- **Deployment:** Docker, Render/Railway, Supabase (DB/Storage), Upstash (Redis), GitHub Actions

---

## 3. 10-Day Build Roadmap

### Phase 1: Infrastructure & Security (Days 1-2)
- [ ] **Day 1: Setup Core Environment**
    - [ ] Initialize FastAPI backend and React frontend.
    - [ ] Configure PostgreSQL with `pgvector` extension.
    - [ ] Setup Docker Compose for localized development (Redis, DB, API).
- [ ] **Day 2: Asset Management & C2PA**
    - [ ] Implement media upload API (Supabase Storage/Cloudflare R2).
    - [ ] Integrate `c2pa-python` for cryptographic content signing.
    - [ ] Develop metadata storage logic for original assets.

### Phase 2: AI Fingerprinting & Matching (Days 3-5)
- [ ] **Day 3: Triple-Layer Fingerprinting**
    - [ ] Implement OpenCLIP (ViT-B/32) for visual embeddings.
    - [ ] Add pHash (Perceptual Hashing) for robust image comparison.
    - [ ] Implement Audio Chromagram generation for video sync.
- [ ] **Day 4: Vector Store & FAISS**
    - [ ] Integrate FAISS for high-speed similarity search.
    - [ ] Implement `pgvector` persistence for long-term storage.
    - [ ] Develop the "Similarity Engine" matching logic with confidence scoring.
- [ ] **Day 5: Real-time Matching API**
    - [ ] Create endpoints for querying similarity.
    - [ ] Implement background processing for bulk-fingerprinting existing assets.

### Phase 3: Crawlers & Blockchain (Days 6-8)
- [ ] **Day 6: Multi-Platform Crawlers**
    - [ ] Implement YouTube crawler (`yt-dlp`).
    - [ ] Implement Twitter/X & TikTok monitoring (`snscrape`).
    - [ ] Implement Telegram bot monitoring (`pyrogram`).
- [ ] **Day 7: Blockchain Anchoring**
    - [ ] Develop Web3.py integration for Polygon (Amoy).
    - [ ] Create smart contract interaction for anchoring media hashes.
    - [ ] Implement "Evidence Vault" logic for legal admissibility.
- [ ] **Day 8: AI DMCA Generator**
    - [ ] Prompt engineering for Claude API to generate platform-specific notices.
    - [ ] Integrate C2PA manifest tampering evidence into notices.
    - [ ] Automate notice drafting based on detected violations.

### Phase 4: Dashboard & Integration (Days 9-10)
- [ ] **Day 9: React Dashboard**
    - [ ] Live "Violation Feed" using WebSockets.
    - [ ] Interactive similarity visualization (original vs. infringing).
    - [ ] Action center for approving/rejecting automated take-downs.
- [ ] **Day 10: Testing & Deployment**
    - [ ] End-to-end integration testing (Crawler -> Matching -> Notice).
    - [ ] Security auditing (API hardening, rate limiting).
    - [ ] Final project documentation and demonstration readiness.

---

## 4. Key Performance Indicators (KPIs)
- **Detection Lag:** < 60 seconds from stream start (simulated).
- **Matching Accuracy:** Target > 90% Precision/Recall on known datasets.
- **Legal Readiness:** 100% C2PA manifest validity on original uploads.
- **User Efficiency:** Reduce DMCA notice time from hours to < 5 minutes.

---

## 5. Risk Mitigation
- **Crawl Blocks:** Use rotating proxies and staggered request patterns.
- **Model Latency:** Optimize PyTorch models for CPU/GPU inference where available.
- **Gas Fees:** Use Polygon L2 for low-cost blockchain anchoring.
- **False Positives:** Implement an "Uncertain" state for scores 70-85% requiring manual review.
