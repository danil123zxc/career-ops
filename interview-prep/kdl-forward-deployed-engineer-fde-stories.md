# KDL FDE Interview Stories

**Role:** 한국딥러닝(KDL) - Forward Deployed Engineer(FDE)
**Use with:** `interview-prep/kdl-forward-deployed-engineer-fde.md`
**Grounding:** `resumes/ai-engineer-cv.md`, `config/profile.yml`, `modes/_profile.md`, `interview-prep/story-bank.md`

## Truth Guardrails

- Do not claim direct production OCR/VLM work unless asked hypothetically. Say your base is production agents, RAG, evaluation, APIs, Docker/CI, and quality systems.
- Do not present JobHunt AI as an enterprise customer project. Present it as fast PoC/product-building evidence.
- Do not overstate customer-facing/RFP ownership. Say you have the engineering side of FDE and are prepared to apply it to customer discovery.
- When asked about KDL's domain, bridge honestly: "제가 직접 OCR 제품을 운영한 경험은 아니지만, 문서 AI에서도 필요한 RAG/evaluation/API/deployment 품질 체계는 제가 다뤄본 영역입니다."

## Story 1 - Production Agent Platform

**Use for:** production-ready AI, ownership, backend/API design, agent architecture, "what have you built?"

### 30-Second Korean Version

TripleH에서 사용자가 autonomous AI agent를 만들고 실행할 수 있는 cloud-native agent platform을 개발했습니다. 저는 agent 설정, 실행, lifecycle 관리를 위한 FastAPI endpoint와 service layer를 구현했고, PostgreSQL/SQLAlchemy 기반 schema도 설계했습니다. 단순 demo가 아니라 운영 가능한 구조가 필요했기 때문에 CI/CD, Docker, 테스트까지 같이 신경 썼고, 결과적으로 6개 이상의 agent workflow를 안정적으로 운영할 수 있는 기반을 만들었습니다. KDL의 FDE 역할에서도 PoC를 만든 뒤 제품화 가능한 구조로 옮기는 일이 중요하다고 봐서, 이 경험이 직접 연결된다고 생각합니다.

### 90-Second Korean Version

TripleH에서 가장 중요한 경험은 autonomous AI agent platform을 production 환경에서 만들고 운영한 것입니다. 단순히 LLM을 호출하는 수준이 아니라, 사용자가 agent를 생성하고, 설정하고, 실행하고, 결과를 관리할 수 있는 lifecycle이 필요했습니다.

제가 맡은 부분은 FastAPI 기반의 agent lifecycle endpoint, service layer, PostgreSQL/SQLAlchemy schema 설계였습니다. 특히 agent filesystem record가 100K+ 규모까지 커질 수 있었기 때문에 API 구조와 DB query 성능을 같이 고려해야 했습니다. 또한 agent workflow는 prompt나 모델만 잘 된다고 안정적인 게 아니어서, pytest 기반 테스트와 CI/CD, Docker 기반 배포 흐름도 같이 챙겼습니다.

결과적으로 6개 이상의 autonomous agent를 운영 가능한 형태로 만들었고, agent configuration과 execution을 관리하는 기반을 구축했습니다. 여기서 배운 점은 AI product는 demo가 아니라 lifecycle, observability, test, deployment가 있어야 실제로 쓸 수 있다는 것입니다. KDL의 FDE도 고객 PoC를 product module로 이식해야 하는 역할이라서, 저는 이 경험을 기반으로 빠른 demo와 production 품질 사이를 연결할 수 있다고 생각합니다.

### KDL Bridge

KDL의 Document AI에서도 extraction model 자체만큼 중요한 것이 document schema, validation, human review, downstream integration이라고 봅니다. 제가 agent platform에서 배운 production 구조화 경험을 그쪽에 적용하고 싶습니다.

### Likely Follow-Ups

- "Agent lifecycle에서 가장 어려웠던 부분은?"
- "API/DB 설계를 어떻게 나눴나요?"
- "운영 가능한 AI와 데모의 차이는 무엇이라고 보나요?"

## Story 2 - RAG Quality Improvement

**Use for:** technical depth, metrics, RAG, model quality, "hardest technical problem"

### 30-Second Korean Version

TripleH에서 agent의 knowledge retrieval 품질이 충분히 안정적이지 않은 문제가 있었습니다. 단순히 prompt를 바꾸는 방식으로는 한계가 있어서 chunking strategy, embedding 선택, reranking을 조정하고 evaluation signal로 비교했습니다. 그 결과 Hit@5 recall을 약 10% 개선했습니다. 이 경험에서 배운 점은 AI 품질은 느낌으로 개선하면 안 되고, baseline과 metric을 먼저 세워야 한다는 것입니다.

### 90-Second Korean Version

TripleH에서 agent가 knowledge를 검색해 답변하는 RAG pipeline을 개선한 경험이 있습니다. 처음에는 retrieval 품질이 일정하지 않아서, 어떤 경우에는 필요한 context가 top results에 들어오지 않는 문제가 있었습니다. 단순 prompt 수정으로 해결하려 하면 문제 원인이 retrieval인지 generation인지 분리되지 않았습니다.

그래서 먼저 retrieval 품질을 독립적으로 봤습니다. chunking 단위를 조정하고, embedding 선택을 비교하고, reranking을 넣었을 때 top-k 안에 필요한 정보가 들어오는지 확인했습니다. 특히 Hit@5 recall을 기준으로 비교해서, anecdotal한 "좋아 보인다"가 아니라 실제 metric으로 개선 여부를 봤습니다.

결과적으로 Hit@5 recall을 약 10% 개선했습니다. 제 reflection은 명확합니다. AI 시스템에서는 모델을 바꾸기 전에 평가 구조가 있어야 합니다. 그렇지 않으면 팀이 실제 품질이 아니라 몇 개의 좋은 예시만 보고 판단하게 됩니다. KDL의 문서 AI도 field extraction, table parsing, document type별 정확도를 다룰 때 같은 원칙이 중요하다고 봅니다.

### KDL Bridge

KDL 제품에서는 document-level accuracy보다 field-level precision/recall, human correction rate, failed document rate 같은 metric이 중요할 것 같습니다. 저는 RAG에서 했던 것처럼 품질을 분해하고 측정하는 방식으로 기여할 수 있습니다.

### Likely Follow-Ups

- "Hit@5를 왜 봤나요?"
- "Chunking과 reranking 중 무엇이 더 효과적이었나요?"
- "Document AI에서도 비슷한 evaluation을 어떻게 만들 건가요?"

## Story 3 - LLM-as-a-Judge in CI

**Use for:** AI quality, release QA, evaluation systems, automation, reducing manual work

### 30-Second Korean Version

Ebit에서 AI agent task를 매번 수동으로 benchmark하는 병목이 있었습니다. 저는 Terminal-Bench와 LLM-as-a-Judge 평가를 GitHub Actions에 통합해서, code compilation, server setup, model training 같은 terminal task를 commit마다 자동 평가할 수 있게 만들었습니다. custom evaluation criteria도 만들었고, 결과적으로 manual benchmarking 시간을 약 65% 줄였습니다. 이 경험은 KDL의 release QA나 AI 결과 품질 검증과 직접 연결된다고 봅니다.

### 90-Second Korean Version

Ebit에서 했던 일 중 KDL과 가장 연결되는 경험은 AI agent 평가 자동화입니다. 당시 문제는 agent가 terminal task를 제대로 수행하는지 확인하는 과정이 너무 수동적이었다는 점입니다. 사람이 매번 결과를 보고 판단하면 시간이 많이 들고, commit마다 같은 기준으로 regression을 잡기도 어려웠습니다.

저는 Terminal-Bench와 Harbor framework를 GitHub Actions에 연결했고, LLM-as-a-Judge pipeline을 추가해서 code compilation, server setup, model training 같은 실제 terminal task를 자동 평가하도록 만들었습니다. 단순 pass/fail이 아니라 task completion quality와 edge case handling을 보기 위한 custom criteria도 만들었습니다.

결과적으로 manual benchmarking 시간이 약 65% 줄었고, commit마다 품질을 확인할 수 있는 구조가 생겼습니다. 제가 배운 점은 AI quality도 software quality처럼 개발 workflow 안에 들어와야 한다는 것입니다. KDL에서 release QA나 문서 추출 결과 검증을 한다면, golden set, regression test, human review feedback, field-level metric을 CI나 internal dashboard에 연결하는 방식으로 접근하고 싶습니다.

### KDL Bridge

KDL의 FDE는 PoC만 만드는 것이 아니라 검증된 기능을 product module로 옮기는 역할입니다. 그때 evaluation suite와 regression guardrail이 있어야 고객 demo가 운영 기능으로 바뀔 수 있습니다.

### Likely Follow-Ups

- "LLM-as-a-Judge 기준은 어떻게 만들었나요?"
- "자동 평가가 틀릴 수 있는데 어떻게 보완했나요?"
- "문서 AI 품질 검증에는 어떤 metric을 쓰겠습니까?"

## Story 4 - Fast PoC: JobHunt AI

**Use for:** fast prototyping, ambiguous problem solving, vibe coding, demo delivery, product thinking

### 30-Second Korean Version

Trae Hackathon에서 JobHunt AI라는 resume optimization tool을 만들었습니다. 문제는 지원자가 JD마다 이력서를 어떻게 맞춰야 하는지 시간이 많이 걸린다는 것이었고, 저는 FastAPI backend, LangChain/LangGraph workflow, Gemini 기반 resume processing, Next.js frontend, Supabase auth/data layer를 연결해서 빠르게 end-to-end prototype을 만들었습니다. 이 경험은 제한된 시간 안에 문제를 정의하고 작동하는 demo를 만드는 FDE 역량을 보여준다고 생각합니다.

### 90-Second Korean Version

JobHunt AI는 제가 빠른 PoC와 product thinking을 보여줄 때 쓰는 이야기입니다. Hackathon에서 시작한 프로젝트였고, 문제는 명확했습니다. 지원자가 각 JD에 맞춰 resume를 분석하고 keyword를 반영하는 과정이 반복적이고 시간이 많이 든다는 점이었습니다.

저는 이것을 단순 resume editor가 아니라 AI workflow 문제로 봤습니다. FastAPI backend에서 JD 분석, keyword extraction, resume tailoring workflow를 만들고, LangChain/LangGraph로 agentic orchestration을 구성했습니다. Gemini를 이용해 resume content를 처리했고, frontend는 Next.js/TypeScript로 만들고 Supabase authentication과 data layer를 연결했습니다. Vercel 배포와 CORS/HTTPS 설정도 처리했습니다.

이 프로젝트의 의미는 기술 스택을 많이 썼다는 것이 아니라, 제한된 시간 안에 문제 정의부터 working product까지 연결했다는 점입니다. KDL FDE도 고객의 pain point를 듣고 빠르게 PoC를 만든 뒤, 가능한 부분을 제품화해야 하는 역할입니다. 저는 이런 속도감 있는 build 경험이 있고, 동시에 production으로 옮길 때는 evaluation, API design, test, deployment quality를 챙겨야 한다는 점도 알고 있습니다.

### KDL Bridge

KDL에서 고객 문서 자동화 PoC를 만든다면, 먼저 document type과 target fields를 좁히고, MVP extraction flow를 만든 뒤, validation/human review/downstream API까지 최소한으로 연결해서 business value를 빠르게 보여주는 방식으로 접근하겠습니다.

### Likely Follow-Ups

- "시간이 부족할 때 무엇을 먼저 만들었나요?"
- "LangGraph를 왜 썼나요?"
- "PoC를 production으로 바꿀 때 무엇을 추가해야 하나요?"

## Story 5 - Code Quality and Technical Disagreement

**Use for:** conflict, code review, engineering standards, communication, quality under speed

### 30-Second Korean Version

Ebit에서 하루 평균 8개의 pull request를 리뷰하면서 error handling, logging, input validation 기준을 강하게 봤습니다. 처음에는 리뷰 기준이 사람마다 달라서 속도와 품질이 충돌할 수 있었는데, 저는 반복되는 문제를 checklist로 정리해서 4명의 엔지니어가 공통 기준으로 보게 만들었습니다. 의견 차이가 있을 때는 취향으로 논쟁하기보다 failure mode와 유지보수 리스크를 기준으로 설명하려고 했습니다.

### 90-Second Korean Version

Ebit에서 code review를 많이 했던 경험이 있습니다. 하루 평균 8개 정도의 pull request를 리뷰했고, 특히 error handling, logging, input validation, testability를 많이 봤습니다. AI/automation 코드에서는 happy path만 맞으면 demo는 되지만, 실제 환경에서는 edge case나 bad input에서 품질 문제가 바로 드러납니다.

처음에는 리뷰가 사람마다 다르게 느껴질 수 있는 문제가 있었습니다. 그래서 반복되는 기준을 checklist로 정리했습니다. 예를 들어 입력 검증이 있는지, 실패 시 로그가 추적 가능한지, 예외가 silent하게 넘어가지 않는지, smoke test가 있는지 같은 항목입니다. 이 checklist가 4명의 엔지니어에게 공유되면서 리뷰 기준이 더 일관되게 바뀌었습니다.

제가 여기서 배운 점은 기술적 의견 차이를 개인 취향으로 만들면 설득이 어렵다는 것입니다. 대신 failure mode, 운영 리스크, user impact, test coverage처럼 측정 가능한 기준으로 바꾸면 팀이 더 빠르게 합의할 수 있습니다. KDL처럼 빠르게 PoC와 제품화를 반복하는 조직에서도 속도와 품질을 대립시키기보다 guardrail로 연결하는 접근이 중요하다고 생각합니다.

### KDL Bridge

KDL FDE가 고객 요구에 빠르게 대응하더라도, 검증 없이 product module로 넣으면 나중에 비용이 커집니다. 저는 빠른 실행과 quality checklist를 같이 가져가는 쪽입니다.

### Likely Follow-Ups

- "동료가 리뷰에 동의하지 않으면 어떻게 하나요?"
- "속도와 품질이 충돌하면 무엇을 선택하나요?"
- "체크리스트가 너무 느리게 만들지는 않았나요?"

## Story 6 - DeepLearning.AI QA to AI Engineering

**Use for:** growth, attention to detail, AI learning trajectory, "why are you ready?"

### 30-Second Korean Version

DeepLearning.AI에서 LangChain, CrewAI, Neo4j, AI agent 관련 course와 platform을 alpha testing했습니다. 단순히 사용자처럼 눌러본 것이 아니라 auto-grading, progress tracking, quiz, authentication 같은 production education platform 기능을 검증했고, 30개 이상의 reproducible bug를 문서화하고 일부 notebook/source code fix에도 기여했습니다. 이 경험이 QA 관점에서 AI product quality를 보는 기반이 되었고, 이후 Ebit 평가 자동화와 TripleH AI engineering으로 이어졌습니다.

### 90-Second Korean Version

제 커리어 전환을 설명할 때 DeepLearning.AI 경험이 중요합니다. 저는 AI/ML course와 platform을 alpha testing하면서 LangChain, CrewAI, Neo4j, AI agent 관련 내용을 실제 학습자 경험 관점에서 검증했습니다. 단순히 콘텐츠를 읽는 것이 아니라 auto-grading, progress tracking, quiz, authentication 같은 platform 기능이 제대로 작동하는지 봤습니다.

그 과정에서 30개 이상의 reproducible bug를 찾고 문서화했고, Jupyter notebook이나 platform source code에 대한 targeted fix에도 기여했습니다. 이 경험을 통해 AI product는 모델만 좋아서는 안 되고, user workflow, grading/evaluation, reliability가 같이 맞아야 한다는 것을 배웠습니다.

이후 Ebit에서는 그 QA 관점을 자동화로 발전시켜 Terminal-Bench와 LLM-as-a-Judge를 CI에 넣었고, TripleH에서는 AI agent platform과 RAG/evaluation을 직접 개발하게 됐습니다. 그래서 저는 제 강점이 단순히 "AI를 써봤다"가 아니라, AI product를 품질과 운영 관점에서 보는 데 있다고 생각합니다.

### KDL Bridge

KDL의 Document AI도 고객 입장에서는 모델 성능보다 "업무가 실제로 줄었는지", "오류를 어떻게 검수하는지", "기존 시스템과 안전하게 연결되는지"가 중요합니다. 저는 그 제품 품질 관점을 가지고 FDE 역할을 하고 싶습니다.

### Likely Follow-Ups

- "QA에서 AI engineering으로 어떻게 넘어왔나요?"
- "최근 6개월 동안 무엇을 배웠나요?"
- "AI product quality를 어떻게 정의하나요?"

## Combined Opening Narrative

Use this when they ask "자기소개 부탁드립니다."

### 60-Second Korean Version

저는 production AI 시스템을 만드는 AI 엔지니어입니다. DeepLearning.AI에서는 LangChain, CrewAI, AI agent 관련 course와 platform을 alpha testing하면서 AI product quality를 보는 관점을 쌓았고, Ebit에서는 Terminal-Bench와 LLM-as-a-Judge를 GitHub Actions에 통합해서 manual benchmarking 시간을 약 65% 줄였습니다. 현재 TripleH에서는 autonomous AI agent platform에서 FastAPI 기반 agent lifecycle API, RAG pipeline 개선, LLM-as-a-Judge 평가, PostgreSQL/SQLAlchemy service layer, Docker/CI/CD를 다루고 있습니다.

제가 KDL FDE 역할에 관심 있는 이유는 이 역할이 단순 모델 개발이 아니라 고객의 문서/업무 문제를 이해하고, PoC를 만들고, 검증된 기능을 product module로 연결하는 역할이기 때문입니다. 저는 agent, RAG, evaluation, backend, deployment 경험을 기반으로 KDL의 Document AI와 workflow automation을 실제 고객 가치로 연결하는 엔지니어가 되고 싶습니다.

## Which Story To Use For Which Question

| Interview question | Best story |
|---|---|
| 자기소개 | Combined Opening Narrative |
| 가장 어려웠던 기술 문제 | Story 2 - RAG Quality Improvement |
| production-ready AI 경험 | Story 1 - Production Agent Platform |
| AI 품질 검증 / release QA | Story 3 - LLM-as-a-Judge in CI |
| 빠르게 demo/PoC 만든 경험 | Story 4 - JobHunt AI |
| 동료와 기술 의견 차이 | Story 5 - Code Quality |
| 최근 6개월 성장 | Story 6 + Story 3 + Story 1 |
| 왜 KDL인가 | Combined Opening + KDL Bridge from Story 1 or 3 |
| 고객 문제를 어떻게 구조화할 건가 | Story 4 bridge + document AI system design from main prep |
| VLM/OCR 직접 경험이 약한데 괜찮나 | Truth Guardrails + Story 2/3 bridge |

## One-Liners To Memorize

- "AI product는 demo가 아니라 lifecycle, evaluation, test, deployment까지 있어야 실제로 쓸 수 있다고 생각합니다."
- "저는 prompt만 바꾸는 방식보다 baseline과 metric을 먼저 세우는 방식을 선호합니다."
- "속도와 품질은 반대가 아니라, 좋은 guardrail이 있을 때 같이 갈 수 있다고 봅니다."
- "제가 직접 OCR 제품을 운영한 경험은 아니지만, 문서 AI에서도 필요한 RAG/evaluation/API/deployment 품질 체계는 제가 다뤄본 영역입니다."
- "FDE는 고객 문제를 듣는 역할에서 끝나는 것이 아니라, 작동하는 시스템으로 번역하는 역할이라고 이해하고 있습니다."
