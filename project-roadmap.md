# 🚀 Project + 📨 Apply Roadmap

> **Part of the 6-month switch plan.** Sibling roadmaps: [🧠 DSA](./readme.md) · [🧩 LLD](./lld-roadmap.md) · [📅 Daily tracker](./daily-tracker.md).
> Project build plan (per-week "Learn first / Build / Done when"): [`PROJECT_PLAN.md`](./PROJECT_PLAN.md).
>
> **Project goal:** ship Loom-lite AI (video recording → transcoding → transcription → embeddings → RAG chat) by Oct 10, on a live cloud URL with observability.
> **Apply goal:** sign an offer by **2026-11-28**.

---

# 🚀 Project Weekly Milestones (Loom-lite AI)

> Calendar mapping for what ships each week. Per-week implementation details in `PROJECT_PLAN.md` Section 5; daily Sat/Sun task lists in `daily-tracker.md` Weekly Goals.

| ✓ | Cal Wk | Dates | Plan Wk | Deliverable | Done when |
|---|--------|-------|---------|-------------|-----------|
| ☐ | 3  | May 26 – Jun 1  | **Wk 1**  | Monorepo foundation | `docker-compose up` → register/login/empty dashboard |
| ☐ | 4  | Jun 2 – 8       | **Wk 2** start | Authentication | Email + Google-OAuth login both work |
| ☐ | 5  | Jun 9 – 15      | **Wk 2** finish | Large-file upload | 500 MB file uploads browser → MinIO |
| ☐ | 6  | Jun 16 – 22     | **Wk 3** | Browser recording + worker skeleton | 30s clip records → uploads → worker logs "received video X" |
| ☐ | 7  | Jun 23 – 29     | **Wk 4** | Transcoding pipeline | Video plays via HLS URL |
| ☐ | 8  | Jun 30 – Jul 6  | **Wk 5** | Playback, sharing, mail scaffold | Public share URL plays + view counter increments |
| ☐ | 9  | Jul 7 – 13      | **Wk 6** start | Whisper transcription | 1-min video gets transcript with clickable timestamps |
| ☐ | 10 | Jul 14 – 20     | **Wk 6** finish + **Wk 7** start | Transcript polish + start summarization | Transcript searchable; summarize job calling Claude Haiku |
| ☐ | 11 | Jul 21 – 27     | **Wk 7** | Summarization + auto-chapters | 10-min video gets TL;DR + 5 chapter markers |
| ☐ | 12 | Jul 28 – Aug 3  | **Wk 7** polish + **Wk 8** start | Embeddings infrastructure | pgvector + chunking + embeddings stored + HNSW index |
| ☐ | 13 | Aug 4 – 10      | **Wk 8** | Semantic search | Search "redis caching" jumps to right video at right moment |
| ☐ | 14 | Aug 11 – 17     | **Wk 9** start | RAG chat | Answers include clickable `[mm:ss]` citations |
| ☐ | 15 | Aug 18 – 24     | **Wk 9** finish | Chat UI polish | Streaming responses, citation seek, "I don't know" handling |
| ☐ | 16 | Aug 25 – 31     | **Wk 10** start | Containers + CI + local K8s | `helm upgrade` works on local k3d cluster |
| ☐ | 17 | Sep 1 – 7       | **Wk 10** finish | Ingress + cert-manager | Local cluster full pipeline end-to-end works |
| ☐ | Buf| Sep 8 – 12      | Catch-up | — | Missed deliverables closed |
| ☐ | 18 | Sep 13 – 19     | **Wk 11** start | KEDA autoscaling + Terraform | KEDA on workers + `terraform plan` clean |
| ☐ | 19 | Sep 20 – 26     | **Wk 11** finish | Cloud deploy + GitHub OIDC | Recording on live URL triggers full pipeline |
| ☐ | 20 | Sep 27 – Oct 3  | **Wk 12** start | Observability | Prometheus + Grafana system-health dashboard live |
| ☐ | 21 | Oct 4 – 10      | **Wk 12** finish | OTel + load test + README — **PROJECT COMPLETE** | All `PROJECT_PLAN.md` §8 Done criteria green |

---

# 📨 Apply Phase (Oct 11 – Nov 28)

> Begins the day Project work ships. Tracks the application + interview crunch into the Nov 28 switch deadline.

| ✓ | Cal Wk | Dates | Goal | Done when |
|---|--------|-------|------|-----------|
| ☐ | 22 | Oct 11 – 17 | Apply phase 1 | Resume + LinkedIn polished, 20+ applications, Pramp/Interviewing.io profile set up |
| ☐ | 23 | Oct 18 – 24 | Apply phase 2 | 40+ total applications, 1 system design mock done, 4 STAR stories drafted |
| ☐ | 24 | Oct 26 – Nov 1 | Interview prep crunch | 3 weakest LLD re-coded, 8–10 STAR stories complete, first mock (DSA + LLD), 10+ new apps |
| ☐ | 25 | Nov 2 – 8 | Active interviewing | Tailored resume per company, 1 timed DSA mock/day, LLD revision before each interview, 4-hr recruiter response SLA |
| ☐ | 26 | Nov 9 – 15 | Active interviewing | Follow-ups, daily LLD revision (~30 min), 1 system design mock this week |
| ☐ | 27 | Nov 16 – 22 | Negotiation prep | Band research done (levels.fyi), 1 mandatory rest day before any onsite, 1 medium/day (no new content) |
| ☐ | 28 | Nov 23 – 28 | Final rounds + offer signing | Final-round prep per company, offers compared if multiple, **Switch deadline: Nov 28** ✅ |
