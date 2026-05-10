---
name: korean-interview-coach
description: Generate and refine Korean job interview answers and coaching from Career-Ops context. Use when the user asks for 면접 자기소개, 1분 자기소개, 지원동기, 경력 소개, 프로젝트 설명, 기술면접, 행동면접, STAR answers, mock interview prep, Korean interview phrasing, or company/role-specific interview coaching for Korean-market jobs.
---

# Korean Interview Coach

Prepare spoken Korean interview answers that are factual, natural to say aloud, and tailored to the target company or role. Use Career-Ops data first so the user does not have to restate their background.

## Workflow

1. Gather candidate and role facts.
   - Read available source files in this order: `interview-prep/` company files, `interview-prep/story-bank.md`, matching `reports/`, `resumes/`, `config/profile.yml`, `modes/_profile.md`, and `article-digest.md`.
   - Prefer company-specific interview-prep files when the user names a company, role, or report.
   - If a needed fact is missing or uncertain, ask briefly instead of inventing it.
2. Classify the interview task.
   - Self introduction: 자기소개, 1분 자기소개, tell me about yourself.
   - Motivation and fit: 지원동기, 왜 이 회사, why this role.
   - Career or project explanation: 경력 소개, 프로젝트 설명, technical deep dive.
   - Behavioral answer: conflict, teamwork, failure, growth, ownership, pressure.
   - Revision or rehearsal: polish a draft, make it more spoken, mock interview.
3. Load `references/korean-interview-patterns.md` for the relevant answer pattern, timing target, and Korean speaking conventions.
4. Draft the answer.
   - Write the answer itself in Korean 존댓말.
   - Write strategy, coaching notes, and risk checks in English unless the user asks for Korean-only notes.
   - Keep answers speakable, not 자소서 prose. Use short paragraphs and sentences the user can say naturally.
5. Verify before presenting.
   - Check that all metrics, employers, credentials, Korean level, visa/work authorization, and company claims came from source context or the user.
   - If timing matters, estimate whether the answer fits the requested 30/60/90-second window and trim before presenting.

## Output Format

For a single answer, use:

```markdown
## Korean Answer
[spoken Korean answer]

Timing: about N seconds

## Coaching Notes
- [English note about positioning, delivery, or tailoring]

## Key Points
- [fact or proof point used]

## Risk Check
- [anything to verify before saying this in an interview]
```

For multiple likely interview questions, provide a compact answer bank with one section per question. For mock interview mode, ask one question at a time, wait for the user's answer, then give a sharper Korean version and brief coaching.

## Career-Ops Integration

- Reuse existing Career-Ops files and story-bank material. Do not create a parallel interview memory system.
- When a report or interview-prep file contains company-specific positioning, use that over generic profile language.
- During live application work, keep written 자소서 answers in the `jasoseo` skill; use this skill for spoken interview answers and rehearsal.
- Never submit an application or claim the user attended an interview.

## Quality Rules

- Do not invent facts, titles, dates, scores, company details, language fluency, visa status, or metrics.
- Avoid stiff written phrases such as `귀사의 무궁한 발전`, `저는 열정적인 인재입니다`, and `4차 산업혁명 시대`.
- Make the user's individual contribution clear in team stories.
- Prefer concrete proof points, tools, tradeoffs, and outcomes over generic strengths.
- For Korean-market interviews, balance confidence with humility: direct evidence first, modest reflection second.
