---
name: jasoseo
description: Generate Korean 자기소개서 (자소서) answers using STAR methodology. Use whenever the user needs to write or improve Korean job application essay answers -- 지원동기, 성장과정, 성격 장단점, 직무 경험, 입사 후 포부, 협업/갈등, 문제해결, or any other 자소서 prompt. Triggers during /career-ops apply mode when encountering 자소서 or essay-type form fields. Also use when the user pastes a Korean application question and asks for help drafting an answer, even without saying "자소서" explicitly.
---

# 자소서 Answer Generator (STAR Method)

Generate compelling Korean 자기소개서 answers that weave Situation-Task-Action-Result structure into natural, polished prose. No mechanical STAR headers in the output -- just a well-told story with a clear narrative arc.

## Workflow

### 1. Gather Facts

Read career-ops data for candidate facts. Skip files that don't exist.

| Source | Path | What to extract |
|--------|------|-----------------|
| CV | Best match from `resumes/` | Experience, projects, metrics, skills |
| Profile | `config/profile.yml` | Name, target roles, superpowers, proof points |
| Narrative | `modes/_profile.md` | Exit story, adaptive framing, advantage |
| Proof points | `article-digest.md` | Detailed project metrics (if exists) |

If a JD or company context is in the conversation (from an evaluation or apply session), use it to connect the answer to the specific role.

### 2. Analyze the Question

Detect the question type and constraints:

| Type | Signal phrases | STAR focus |
|------|---------------|------------|
| 지원동기 | "지원 동기", "왜 지원", "입사를 희망하는 이유" | Past experience that led to interest in this company/role. Connect trajectory to their mission. |
| 성장과정 | "성장과정", "본인 소개", "자신을 소개" | Formative experience that shaped professional identity. Show a growth arc. |
| 성격 장단점 | "장단점", "강점과 약점", "본인의 성격" | Strength demonstrated through a concrete episode. Weakness shown with active management. |
| 직무 경험 | "직무 경험", "관련 경험", "역량을 서술" | Most relevant technical project. Heavy on Action and Result with metrics. |
| 입사 후 포부 | "입사 후 포부", "향후 계획", "비전" | Past achievement that naturally extends into what you want to build at this company. |
| 협업/갈등 | "협업", "갈등", "팀워크", "의견 차이" | Team situation where you navigated disagreement or coordinated across functions. |
| 문제해결 | "문제 해결", "어려움을 극복", "도전" | A real obstacle, your diagnosis, your action, and measurable resolution. |

If the question type is ambiguous, state your interpretation and confirm before drafting.

### 3. Character Limit

Character limits (글자수) are critical. If the user hasn't specified one, ask:

> "이 문항의 글자수 제한이 있나요? (예: 500자, 1000자)"

Adapt depth to the limit:

| Limit | Strategy |
|-------|----------|
| ~300자 | One tight episode. 2-3 sentences per STAR element. No preamble. |
| ~500자 | One episode, moderate detail. Brief context, focused action, clear result. |
| ~800자 | One episode with full detail, or two tightly linked episodes. |
| ~1000자+ | Full narrative arc with setup, development, resolution, and reflection. |

### 4. Select Experience

From the gathered facts, pick the experience that:

1. **Best answers the question** -- direct relevance to what's asked
2. **Has the strongest result** -- measurable outcomes beat vague claims
3. **Connects to the target role** -- if a JD is available, pick experiences with keyword overlap
4. **Is recent** -- prefer recent unless an older one is significantly stronger

If the user has already specified which experience to use, respect that choice.

### 5. Draft the Answer

Structure internally with STAR but output flowing Korean prose. The reader should feel a natural story arc, not a fill-in-the-blanks template.

#### Narrative Arc

**Opening (Situation)** -- 1-2 sentences. Set the scene with enough detail that the reader can picture it. When, where, what was the context.

**Transition to challenge (Task)** -- 1-2 sentences. What was the problem or goal? Why did it matter? Flow naturally from the situation -- don't start a new paragraph for each element.

**Core (Action)** -- 40-50% of total length. This is the heart. Describe YOUR specific actions step by step. First person. Name the tools, describe the approach, explain your reasoning. In team projects, clearly distinguish your individual contribution from the team's work.

**Landing (Result)** -- 1-2 sentences. Lead with measurable outcomes (numbers, percentages, before/after). Then what you learned or how it shaped your perspective. If a JD is available, connect the takeaway to the role.

#### Korean Writing Conventions

**Tone:** 존댓말 (formal polite) throughout. Sentences end with ~습니다/~입니다. But keep it human and genuine -- avoid press-release stiffness.

**Be specific, not generic:**
- Weak: "다양한 경험을 통해 성장했습니다"
- Strong: "RAG 파이프라인의 Hit@5 재현율을 10% 향상시키며 검색 품질 최적화의 실무 감각을 키웠습니다"

**Avoid cliche openers:**
- "저는 어릴 때부터 ~에 관심이 많았습니다" (unless genuinely essential)
- "열정적이고 도전적인 성격의 소유자입니다"
- "급변하는 시대에..."
- "4차 산업혁명 시대를 맞이하여..."

**Start with a concrete moment or fact instead:**
- "2026년 3월, 7인 규모의 국제 팀에서 AI 에이전트 플랫폼을 구축하며..."
- "프로덕션 환경에서 6개의 자율 에이전트를 배포하고 운영하면서..."

**Action verbs over passive descriptions:**
- Use: 설계했습니다, 구축했습니다, 개선했습니다, 주도했습니다, 분석했습니다, 도입했습니다
- Avoid: ~하게 되었습니다, ~할 수 있었습니다, ~하는 경험을 하였습니다 (too passive, too roundabout)

**Numbers and metrics:**
- Always include when available from CV/profile data
- Use natural phrasing: "약 20%", "10만건 이상", "15개의 API 엔드포인트"
- Never inflate or invent metrics -- use only what the source data supports

**Connect to company (when JD is available):**
- Reference the company's product, mission, or tech stack naturally in the answer
- Show why your experience maps to their needs
- A natural connection beats a forced mention -- don't shoehorn it in

**Differentiation:**
- Highlight what makes you different from other applicants
- Unique combinations (multilingual + AI engineering, international team experience, etc.)
- Specific tools/approaches rather than generic capabilities

### 6. Verify and Present

1. Count characters (글자수) including spaces
2. If over the limit: trim adjectives and filler first, then compress the situation section
3. If under the limit by more than 10%: expand the action section with more detail, or deepen the result with reflection
4. Present the answer with the character count: `(현재 {N}자 / {LIMIT}자)`
5. Ask: "수정할 부분이 있으면 말씀해 주세요."

### 7. Iterate

Common revision requests:
- Tone adjustment (more/less formal, more confident, more humble)
- Swap to a different experience
- Tighter or longer version
- Stronger connection to a specific company
- More technical detail vs. more storytelling

Apply changes, re-verify character count, and present again.

## Integration with career-ops

**During `/career-ops apply` mode:**
- JD and company context are already loaded -- use them to tailor every answer
- Generate answers for each 자소서 field on the application form
- Present all answers together for review before submission
- Respect each field's individual character limit

**Standalone invocation:**
- Ask for the question and any available context (company, role, JD URL)
- If a recent evaluation report exists in `reports/`, offer to use that company/role context

## Quality Checklist

Before presenting the final answer, verify:

- [ ] STAR elements are all present but woven naturally (no visible headers)
- [ ] 존댓말 is consistent throughout
- [ ] All metrics/facts come from actual CV/profile data (nothing invented)
- [ ] Character count is within the limit
- [ ] No cliche phrases
- [ ] The candidate's individual contribution is clear (not hidden behind "we")
- [ ] If a JD is available, there's a natural connection to the company/role
