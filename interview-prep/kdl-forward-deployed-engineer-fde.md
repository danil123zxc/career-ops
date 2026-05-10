# Interview Intel: 한국딥러닝(KDL) - Forward Deployed Engineer(FDE)

**Report:** N/A - no existing KDL evaluation report found
**Researched:** 2026-05-10
**Posting:** https://www.wanted.co.kr/wd/356521
**Sources:** 0 Glassdoor reviews found, JobPlanet aggregate interview stats, Blind company/posts page, 2 Saramin interview snippets, KDL official site/docs/blog, Wanted live page via Playwright, Demoday, IN THIS WORK, ZDNet Korea, Seoul Economic Daily

## Quick Read

- This is a strong fit for Danil's target archetype: AI Engineer + AI Agent Engineer + Forward Deployed Engineer.
- The interview will likely test three things: real AI engineering depth, customer/problem-solving judgment, and whether Danil can survive KDL's high-density execution culture.
- Lead with production agents, RAG improvement, LLM-as-a-Judge evaluation, FastAPI backends, Docker/CI/CD, and AI-assisted fast prototyping.
- Be careful around VLM/OCR/model-serving depth. KDL explicitly asks for VLM, RAG, inference efficiency, vLLM or Triton, Docker, and production-ready AI. Danil has RAG/eval/backend strength, but direct VLM/OCR and vLLM/Triton proof is thinner.
- The Wanted posting deadline is listed as 2026-05-03, already past as of 2026-05-10. Playwright verification on 2026-05-10 showed the page as `지원마감`, so use this prep if the interview is already scheduled or if the role reopens.

## Process Overview

- **Rounds:** likely 2 interview rounds after resume screening.
- **Format:** document review -> 1st interview for job fit -> 2nd interview for culture fit -> compensation/start-date discussion.
- **Technical task:** possible for development roles. IN THIS WORK says developer roles may include coding tests or technical assignments.
- **Difficulty:** JobPlanet aggregate shows 35 interview reviews and 2.9/5 interview difficulty. One Saramin AI interview review reports "medium" difficulty; another non-AI review reports "easy". Treat the AI/FDE process as medium because the role requires customer-facing AI architecture, VLM/RAG knowledge, model serving, and production deployment.
- **Experience signal:** JobPlanet aggregate shows mixed experience: 46% positive, 34% negative, 20% neutral, with online applications as the dominant route. Use this as process context, not as a prediction for your specific round.
- **Known quirks:** KDL publishes unusually direct hiring signals: they want self-driven growth, problem solvers, high-density execution, technical depth, and business impact.
- **Sources:** Wanted posting, Playwright live verification, Demoday role mirror, IN THIS WORK KDL recruitment interview, Saramin interview snippets, JobPlanet aggregate.

## Role Decode

### What KDL Is Buying

KDL is not hiring a pure ML researcher or pure backend engineer. They are hiring someone who can sit at the boundary of customer problem, AI architecture, PoC delivery, and productization.

The FDE posting describes work across:

- technical sales support and consulting
- customer pain-point analysis
- RFP feasibility analysis and effort estimation
- PoC/demo development
- moving validated PoC features into core product modules
- first-line troubleshooting for OOM and inference latency
- release QA and basic AI model quality checks

### Best Candidate Angle

Use this positioning:

> "저는 AI를 연구만 하는 사람이 아니라, 실제 서비스 안에서 돌아가게 만드는 엔지니어입니다. TripleH에서 production agent platform, RAG 개선, LLM-as-a-Judge 평가, FastAPI API, Docker/CI/CD를 직접 다뤘고, KDL FDE 역할에서는 고객 문제를 빠르게 구조화해서 PoC에서 제품화까지 연결하는 쪽에 바로 기여하고 싶습니다."

In English:

> "I am not only interested in AI models. I build the production systems around them: agent workflows, retrieval quality, evaluation loops, APIs, and deployment. That maps directly to an FDE role where customer problems have to become working AI systems quickly."

## Company Signals

### Product Direction

- KDL positions itself around Document AI and Vision-LLM document understanding, not old OCR. The official site lists DEEP OCR, DEEP Parser, DEEP Erase, DEEP Index, DEEP Clear, DEEP View, and DEEP SignCheck as modules inside DEEP Agent.
- The official DEEP Agent page frames the product as a VLM-based workflow automation platform for PDFs, images, and Word files, with layout understanding, structure extraction, validation logic, workflow AI, schema mapping, review/analytics, and downstream API integration.
- The official site says DEEP Agent is meant to ingest varied document formats and organize them for downstream work, and says 80+ customers use KDL for document automation.
- ZDNet reported in January 2026 that KDL closed a 12B KRW Series A, had 80+ customers and 10B KRW cumulative revenue, and planned to move from document automation into workflow automation and AI-agent products.
- ZDNet reported in April 2026 that KDL launched a financial document AI product for loan review, KYC, AML, document classification, extraction, verification, and system entry.
- ZDNet reported KDL's Deep Parser demo at Gyeonggi Province, including HWP/PDF structuring for administrative documents and reported item-recognition and extraction accuracy metrics.
- Seoul Economic Daily's English article describes KDL's differentiation as VLM-based OCR that reads layout and context, not just characters.
- KDL's own finance case study emphasizes on-prem/air-gapped deployment, PII masking, audit trails, and measurable business impact. This is highly relevant to FDE conversations because customer constraints are not only model accuracy; they include security, compliance, workflow fit, and integration.

### Vocabulary To Use

- Document AI
- Vision-LLM / VLM
- document structure understanding
- workflow automation
- AI agent with verification rules
- structured extraction
- KYC / AML / financial document processing
- HWP/PDF parsing
- inference latency
- OOM troubleshooting
- PoC to production
- customer pain point -> technical architecture -> measurable business impact

### Things To Avoid

- Do not sound like "I want to learn VLM from scratch here." Say you have adjacent RAG/eval/agent experience and are actively closing the VLM/model-serving gap.
- Do not over-index on generic LLM enthusiasm. KDL screens for practical AI that makes money and solves business problems.
- Do not present AI-assisted coding as a shortcut. Frame it as a way to prototype fast while preserving tests, code review, and quality gates.
- Do not claim direct OCR/VLM production work unless you have it. Say "RAG/evaluation/backend production experience is my base; VLM/document AI is the domain I prepared for this role."
- Do not ask only about work-life balance early. Their public hiring material emphasizes high-density growth; ask about execution rhythm, ownership, and how teams prevent quality loss at speed.
- Do not ignore culture intensity. Blind has employee discussion/review signals describing fast growth and a strong execution rhythm, but also warning that people who need stable routine may find the pace hard.

## Round-by-Round Breakdown

### Round 1: Job Fit / Technical Fit

- **Duration:** unknown, likely 45-60 min.
- **Conducted by:** practical interviewers or team lead; one Saramin AI review says 2 interviewers.
- **What they evaluate:** AI domain knowledge, ability to solve current project problems, production engineering judgment, communication with non-experts.
- **Reported questions:** Saramin AI review mentions career-detail questions, a hypothetical KDL project problem, and VLM principle questions.
- **How to prepare:** build a crisp 90-second walkthrough of TripleH's agent platform, then prepare 4 technical deep dives: RAG quality, LLM-as-Judge, production API/service design, and VLM/OCR fundamentals.

### Round 2: Culture Fit / Organization Fit

- **Duration:** unknown, likely 45-60 min.
- **Conducted by:** leadership or management.
- **What they evaluate:** self-driven growth, intensity, ownership, communication style, why KDL.
- **Reported structure:** Demoday lists 2nd interview as "organization fit"; IN THIS WORK calls it culture fit with executives.
- **How to prepare:** answer "why KDL" with product-specific reasons: VLM document understanding, workflow automation, financial/public-sector use cases, and the FDE role's customer-to-production ownership.

### Possible Technical Assignment / Coding Test

- **Evidence:** IN THIS WORK says development roles may include coding tests or technical/design assignments.
- **Likely format:** small backend/API task, model-serving or inference pipeline design, document-processing PoC, or architecture discussion rather than pure algorithm LeetCode.
- **How to prepare:** rehearse a small FastAPI service design for document upload -> OCR/VLM extraction -> validation -> structured JSON -> review workflow -> downstream API integration.

## 60-Minute Mock Drill

Use this when you only have one focused prep block.

### 0-10 min: Opening Narrative

Practice this in Korean until it is natural:

> 저는 production AI 시스템을 만드는 AI 엔지니어입니다. TripleH에서는 autonomous agent platform, RAG 개선, LLM-as-a-Judge 평가, FastAPI API, Docker/CI/CD를 직접 다뤘고, Ebit에서는 Terminal-Bench와 CI 기반 평가 자동화를 만들었습니다. KDL FDE 역할은 고객 문제를 빠르게 구조화하고, PoC를 만들고, 검증된 기능을 제품화하는 역할이라서 제 agent/RAG/evaluation/backend 경험과 직접 맞닿아 있다고 봅니다.

### 10-25 min: Technical Deep Dive

Pick one story and go deep:

- RAG Hit@5 improvement: baseline -> experiment -> metric -> tradeoff.
- LLM-as-a-Judge in CI: why manual QA was insufficient -> evaluation criteria -> GitHub Actions integration -> 65% manual benchmarking reduction.
- Production agent platform: lifecycle API -> service layer -> deployment -> testing.

For each, end with: "KDL의 문서 AI에서도 같은 방식으로 field-level metric, regression set, human review feedback을 설계할 수 있습니다."

### 25-40 min: KDL-Specific System Design

Answer this out loud:

> 고객사가 대량의 대출 심사 PDF와 스캔본을 자동 처리하고 싶다고 합니다. FDE로서 어떤 시스템을 설계하겠습니까?

Strong structure:

1. Clarify document types, monthly volume, latency, target fields, error tolerance, security, and downstream systems.
2. Propose pipeline: upload -> document classification -> VLM/OCR/parser -> schema/KIE extraction -> validation rules -> human review -> audit log -> ERP/LMS/API integration.
3. Define metrics: field-level precision/recall, human correction rate, processing time, failed-doc rate, P95 latency, cost per document.
4. De-risk: sample set, red-team bad scans/handwriting/tables, on-prem if finance/public sector, rollback and manual fallback.
5. Productize: reusable document schemas, regression dataset, monitoring dashboard, customer feedback loop.

### 40-55 min: Culture Fit

Prepare short answers for:

- 최근 6개월 동안 어떻게 성장했나?
- "시키면 열심히 하겠다"가 아니라 "내가 바꾸겠다"는 태도를 보여준 경험은?
- 빠른 실행 속도와 코드 품질이 충돌할 때 어떻게 판단하나?

Use this stance: "속도는 중요하지만, production AI에서는 evaluation, tests, observability가 없으면 결국 느려집니다. 저는 빠른 PoC와 운영 가능한 품질 사이를 metric과 guardrail로 연결하는 쪽입니다."

### 55-60 min: Questions To Ask

Ask two:

1. FDE가 PoC에서 제품팀 handoff까지 어느 정도 ownership을 가지나요?
2. 현재 KDL 고객 프로젝트에서 가장 어려운 병목은 extraction quality, legacy integration, review workflow, latency, or scope definition 중 어디인가요?

## Likely Questions

### Sourced From KDL Hiring Content

1. **최근 6개월 동안 본인의 성장을 위해 무엇을 했나요?**
   **Strong angle:** DeepLearning.AI course testing, agent work at TripleH, Terminal-Bench/LLM-as-Judge, Codex/Claude Code workflows. Emphasize measurable skill acquisition, not passive learning.

2. **가장 해결하기 어려웠던 기술 문제는 무엇이고 어떻게 돌파했나요?**
   **Strong angle:** RAG Hit@5 improvement or CI-based LLM evaluation. Explain baseline, failure mode, experiment design, result, and what you would do next.

3. **KDL 제품 중 하나를 골라 개선안을 제안한다면?**
   **Strong angle:** Choose DEEP Agent for financial documents. Suggest evaluation dashboards for field-level extraction confidence, reviewer feedback loops, and regression tests by document type.

4. **동료와 기술적 견해 차이가 있을 때 어떻게 조율하나요?**
   **Strong angle:** Use code review and evaluation data. "I try to turn opinion conflict into measurable criteria: latency, accuracy, maintainability, test coverage, user impact."

5. **업무와 삶 중 무엇이 우선인가요?**
   **Strong angle:** Do not fake martyrdom. Say you can work intensely when mission and ownership are clear, but long-term output requires focus, feedback loops, and quality discipline.

### Sourced From Saramin Interview Snippets

1. **경력 사항을 상세히 설명해 주세요.**
   Prepare a chronological story: DeepLearning.AI QA -> Ebit benchmarking and code review -> TripleH production AI agents -> why KDL FDE.

2. **현재 KDL 프로젝트에서 이런 문제가 있다면 어떻게 해결하겠습니까?**
   Use a structured response: clarify constraints -> define success metric -> propose MVP/PoC -> identify risk -> test -> productize.

3. **VLM 원리 또는 AI 도메인 지식 질문.**
   Prepare: how VLM combines visual tokens/layout with text understanding; why layout matters in tables, merged cells, forms, invoices; failure modes such as handwriting, scan quality, ambiguous fields, hallucinated extraction.

4. **회사를 얼마나 알고 있나요? 무엇을 해보고 싶나요?**
   Answer with specific products: Deep Parser, Deep Agent for Finance, workflow automation beyond OCR.

### Inferred From JD

1. **[inferred from JD] 고객이 "문서 자동화가 필요하다"고만 말할 때, 어떻게 요구사항을 구체화할 건가요?**
   Answer with discovery questions: document types, volume, error tolerance, downstream systems, compliance, human review needs, latency/cost constraints, success metric.

2. **[inferred from JD] RFP를 보고 구현 가능성과 공수를 어떻게 산정하나요?**
   Answer: split known/unknown, build assumption table, identify integration points, data availability, model quality risk, deployment environment, acceptance tests, and phased scope.

3. **[inferred from JD] OOM 또는 추론 속도 저하가 발생하면 어떻게 대응하나요?**
   Answer: reproduce with input shape/batch/model/version, inspect GPU memory, reduce batch/context/resolution, quantization or smaller model, caching, async queue, vLLM/Triton serving config, monitoring.

4. **[inferred from JD] PoC 데모를 프로덕트 핵심 모듈로 이식할 때 무엇을 바꾸나요?**
   Answer: error handling, observability, tests, auth/permissions, data schema, evaluation suite, latency budget, deployment, rollback, documentation.

5. **[inferred from JD] AI 모델 결과의 품질 검증을 어떻게 설계하나요?**
   Answer from Danil's strength: golden datasets, field-level metrics, LLM-as-Judge with human review, regression tests, failure taxonomy, dashboarding.

## Story Bank Mapping

| # | Likely topic | Best story | Fit | Gap |
|---|---|---|---|---|
| 1 | Production-ready AI system | Agentic AI - Production Agent Platform | strong | none |
| 2 | RAG/data pipeline and retrieval quality | RAG and Evaluation - Improving Retrieval Quality | strong | none |
| 3 | AI quality/release QA | AI Quality - LLM-as-a-Judge in CI | strong | none |
| 4 | Customer-facing discovery/RFP estimation | Agent platform + JobHunt AI framing | partial | Need a tighter customer/problem-discovery story |
| 5 | VLM/OCR/document understanding | RAG story as adjacent AI quality work | partial | Need VLM/OCR concept prep; do not claim direct production VLM |
| 6 | Model serving with vLLM/Triton, OOM, latency | Docker/CI/CD and API experience | partial | Need targeted serving troubleshooting prep |
| 7 | Fast PoC/demo delivery | JobHunt AI hackathon project | strong | none |
| 8 | Conflict/technical disagreement | Code review at Ebit | strong | Add one concrete disagreement example if available |

### Missing Story To Draft

Draft one STAR+R story around "turning ambiguous user/customer needs into a working AI system." Use either:

- TripleH agent platform: unclear agent lifecycle requirements -> define API/service boundaries -> ship lifecycle endpoints -> deploy and iterate.
- JobHunt AI: ambiguous hackathon problem -> design resume optimization workflow -> ship full-stack prototype quickly.

## Technical Prep Checklist

- [ ] VLM/OCR fundamentals: visual tokens, layout parsing, table/form understanding, OCR vs document understanding.
- [ ] KDL products: DEEP OCR, DEEP Parser, DEEP Agent, DEEP Agent for Finance, Deep Parser public-sector demo.
- [ ] Document AI architecture: upload -> parse -> extract -> validate -> human review -> downstream system integration.
- [ ] RAG for document systems: chunking, metadata, table-aware retrieval, reranking, evaluation.
- [ ] Model serving basics: vLLM, Triton, Docker, GPU memory, batch size, latency vs throughput, quantization.
- [ ] OOM troubleshooting: reproduce, profile, reduce batch/resolution/context, cache, queue, monitor.
- [ ] AI quality: golden set, field-level precision/recall, human review loop, LLM-as-Judge, regression gates.
- [ ] RFP/effort estimation: assumptions, risk table, phased delivery, acceptance criteria, integration dependencies.
- [ ] Korean technical explanation: explain RAG, VLM, evaluation, and model serving in business Korean.
- [ ] Product improvement pitch: prepare one concrete improvement idea for DEEP Agent for Finance.

## Answer Bank

### Tell Me About Yourself

저는 production AI 시스템을 만드는 AI 엔지니어입니다. TripleH에서는 autonomous agent platform에서 agent lifecycle API, RAG 개선, LLM-as-a-Judge 평가, CI/CD와 Docker 기반 배포를 다뤘습니다. 이전에는 Ebit에서 Terminal-Bench와 LLM 평가를 CI에 넣어서 수동 벤치마킹 시간을 줄였고, DeepLearning.AI에서는 LangChain, CrewAI, Neo4j 같은 AI/ML 교육 플랫폼을 테스트했습니다. KDL의 FDE 역할은 고객의 문서/업무 문제를 이해하고, PoC를 빠르게 만들고, 검증된 기능을 제품화하는 역할이라서 제가 쌓아온 agent, RAG, 평가, backend 경험을 가장 직접적으로 쓸 수 있는 포지션이라고 봅니다.

### Why KDL?

KDL에 관심이 가는 이유는 단순 OCR이 아니라 문서의 구조와 맥락을 이해해서 실제 업무 자동화까지 연결하려는 방향 때문입니다. 특히 금융 문서, 공공 HWP/PDF, KYC/AML 같은 영역은 모델 성능만으로는 부족하고, 검증, 사람의 리뷰, 시스템 연계까지 설계해야 합니다. 저는 RAG 품질 개선, LLM-as-a-Judge 평가, FastAPI 기반 서비스 설계 경험이 있어서 KDL의 Document AI와 workflow automation 방향에 실질적으로 기여할 수 있다고 생각합니다.

### Hardest Technical Problem

Use the RAG story:

- **Situation:** agent knowledge retrieval needed measurable improvement.
- **Task:** improve quality without relying only on prompt tweaks.
- **Action:** tuned chunking, embeddings, reranking; compared retrieval behavior using evaluation signals.
- **Result:** Hit@5 improved by about 10%.
- **Reflection:** quality work needs measurable baselines; otherwise teams optimize anecdotes.

Tie to KDL:

> KDL's document extraction and workflow automation will need the same discipline: document-type test sets, field-level accuracy, regression checks, and human review feedback.

### Product Improvement Pitch

For DEEP Agent for Finance:

1. Add document-type-specific evaluation dashboards: loan review, KYC, AML, invoices.
2. Track confidence and human correction by field, not only document-level success.
3. Build a feedback loop where reviewer corrections become regression cases.
4. Provide integration adapters for CRM/EDMS/RPA with audit logs.
5. Expose "why this field was extracted" evidence snippets for compliance-heavy customers.

### VLM/OCR Concept Answer

OCR only converts visual characters into text. Document AI needs to understand layout, semantic structure, and context. In a financial form, the same number can be an account number, amount, date, or ID depending on nearby labels and table structure. A VLM can use both visual layout and text tokens to infer these relationships. The hard parts are table structure, merged cells, handwriting, poor scan quality, ambiguous labels, and preventing confident wrong extractions. That is why I would pair model output with field-level confidence, validation rules, human review, and regression tests.

## Questions To Ask Them

1. KDL is moving from document automation toward workflow automation and AI agents. In this FDE role, what is the typical boundary between PoC delivery and product-team handoff?
2. For financial or public-sector document projects, what are the most common failure modes today: extraction accuracy, integration with legacy systems, review workflow, latency, or customer scope definition?
3. How does KDL evaluate document AI quality internally: document-level accuracy, field-level accuracy, human correction rate, latency, or business KPI?
4. When a customer asks for a custom workflow, how do FDEs decide whether to customize, push back, or turn it into a reusable product feature?
5. What does a strong first 90 days look like for this FDE role?

## 3-Day Prep Plan

### Day 1: Company and Product

- Review KDL official site modules: DEEP OCR, DEEP Parser, DEEP Agent, DEEP Agent for Finance.
- Prepare "Why KDL" in Korean.
- Prepare one product improvement pitch for DEEP Agent for Finance.

### Day 2: Technical Depth

- Study VLM/OCR/document-layout concepts.
- Review vLLM/Triton basics and OOM/latency troubleshooting.
- Prepare one system design: document upload -> VLM parsing -> structured extraction -> validation -> human review -> downstream integration.

### Day 3: Stories and Mock Answers

- Rehearse 5 stories: production agent platform, RAG improvement, LLM-as-Judge, JobHunt AI fast prototype, Ebit code review/conflict.
- Practice answering in Korean with technical terms.
- Prepare questions to ask them.

## Sources

- Wanted role posting: https://www.wanted.co.kr/wd/356521
- Demoday role mirror: https://demoday.co.kr/recruits/11887
- KDL official site: https://koreadeep.com/
- KDL DEEP Agent product page: https://www.koreadeep.com/deep-agent
- KDL finance workflow case study: https://www.koreadeep.com/blog/deep-agent-non-typing-workflow
- KDL document AI bottleneck post: https://www.koreadeep.com/blog/korean-deep-learning-document-ai
- IN THIS WORK KDL recruitment interview: https://inthiswork.com/archives/297816
- ZDNet Korea Series A funding article: https://zdnet.co.kr/view/?no=20260108172614
- ZDNet Korea finance document AI launch: https://zdnet.co.kr/view/?no=20260407140744
- ZDNet Korea Gyeonggi Deep Parser demo: https://zdnet.co.kr/view/?no=20251112102913
- Seoul Economic Daily English article: https://en.sedaily.com/technology/2026/03/10/korea-deep-learnings-ocr-outperforms-googles-gemini-in
- JobPlanet interview aggregate: https://www.jobplanet.co.kr/companies/404731/interviews/%ED%95%9C%EA%B5%AD%EB%94%A5%EB%9F%AC%EB%8B%9D
- Blind company/posts page: https://www.teamblind.com/kr/company/%ED%95%9C%EA%B5%AD%EB%94%A5%EB%9F%AC%EB%8B%9D
- Saramin AI interview review snippet: https://www.saramin.co.kr/zf_user/interview-review/detail/idx/62834%2F%ED%95%9C%EA%B5%AD%EB%94%A5%EB%9F%AC%EB%8B%9D%28%EC%A3%BC%29-%EB%A9%B4%EC%A0%91-%ED%9B%84%EA%B8%B0
- Saramin non-AI interview review snippet: https://www.saramin.co.kr/zf_user/interview-review/detail/idx/60342%2F%ED%95%9C%EA%B5%AD%EB%94%A5%EB%9F%AC%EB%8B%9D%28%EC%A3%BC%29-%EB%A9%B4%EC%A0%91-%ED%9B%84%EA%B8%B0
