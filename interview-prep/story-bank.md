# Story Bank — Master STAR+R Stories

This file accumulates your best interview stories over time. Each evaluation (Block F) adds new stories here. Instead of memorizing 100 answers, maintain 5-10 deep stories that you can bend to answer almost any behavioral question.

## How it works

1. Every time `/career-ops offer` generates Block F (Interview Plan), new STAR+R stories get appended here
2. Before your next interview, review this file — your stories are already organized by theme
3. The "Big Three" questions can be answered with stories from this bank:
   - "Tell me about yourself" → combine 2-3 stories into a narrative
   - "Tell me about your most impactful project" → pick your highest-impact story
   - "Tell me about a conflict you resolved" → find a story with a Reflection

## Stories

<!-- Stories will be added here as you evaluate offers -->
<!-- Format:
### [Theme] Story Title
**Source:** Report #NNN — Company — Role
**S (Situation):** ...
**T (Task):** ...
**A (Action):** ...
**R (Result):** ...
**Reflection:** What I learned / what I'd do differently
**Best for questions about:** [list of question types this story answers]
-->

### Agentic AI - Production Agent Platform
**Source:** Report #013 - IBM Korea - Client Engineering - AI Engineer  
**S (Situation):** TripleH needed a cloud-native platform where users could create, customize, and run autonomous AI agents.  
**T (Task):** Build agent lifecycle capabilities that were reliable enough for production use.  
**A (Action):** Built and maintained 6+ autonomous AI agents, engineered FastAPI lifecycle endpoints, added service layers, and supported deployment through CI/CD and containerization.  
**R (Result):** Enabled configurable production agent workflows and infrastructure-agnostic deployment.  
**Reflection:** Enterprise AI PoCs need reusable architecture and operating discipline, not only impressive demos.  
**Best for questions about:** agent architecture, production AI, ambiguous technical problems, ownership.

### RAG and Evaluation - Improving Retrieval Quality
**Source:** Report #013 - IBM Korea - Client Engineering - AI Engineer  
**S (Situation):** Agent knowledge retrieval quality needed measurable improvement.  
**T (Task):** Improve retrieval without relying only on prompt changes.  
**A (Action):** Tuned chunking strategies, embedding choices, and reranking, then used evaluation signals to compare retrieval behavior.  
**R (Result):** Improved Hit@5 recall by about 10%.  
**Reflection:** Retrieval systems should be evaluated before optimization; otherwise teams mistake anecdotal wins for real quality gains.  
**Best for questions about:** RAG, metrics, model quality, technical tradeoffs.

### AI Quality - LLM-as-a-Judge in CI
**Source:** Report #013 - IBM Korea - Client Engineering - AI Engineer  
**S (Situation):** Manual benchmarking made it hard to catch quality regressions in AI/agent tasks.  
**T (Task):** Make agent task quality more repeatable and less dependent on manual checks.  
**A (Action):** Integrated Terminal-Bench and LLM-as-a-Judge pipelines into GitHub Actions and created custom evaluation criteria for task completion and edge cases.  
**R (Result):** Reduced manual benchmarking time by about 65%.  
**Reflection:** AI quality becomes operationally useful when it runs in the same workflow as software quality checks.  
**Best for questions about:** evaluation, CI/CD, quality systems, automation.
