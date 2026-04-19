# Mode: pdf — ATS-Optimized PDF Generation

## One-page constraint (MANDATORY) — Classic Resume Format

The generated CV MUST always fit on exactly ONE page. Classic resume style prioritizes:

1. **Education**: Institution, degree, location, date, GPA, relevant coursework (2-3 schools max)
2. **Work Experience**: 2-3 most relevant roles. 3-4 bullets per role (impact-focused, measurable results)
3. **University Projects**: Top 3-4 most relevant projects with 1-2 line descriptions
4. **Activities**: Leadership roles, volunteer work, extracurriculars (3-4 activities, 1-2 bullets each)
5. **Additional Section**: Skills, Languages, Certifications, Awards all consolidated into one section

The CV MUST fill the full page with MINIMAL WHITESPACE. Target 95–99% page fill. Every section should be densely packed without appearing cramped.

- **Too long (> 1 page):** CUT content — never shrink fonts or margins. Priority for cuts (lowest value first): certifications > older/less-relevant jobs > project descriptions > education details.
- **Too short (< ~95% of page):** AGGRESSIVELY EXPAND to fill remaining space. Priority for additions (highest value first): add 3rd-4th bullets to top 2 roles (impact-focused, not filler) > add 4th-5th project > expand summary to 3-4 lines with additional context > add detailed education descriptions (thesis, honors, relevant coursework) > restore all trimmed certifications with years > add "Awards" or "Speaking" section if relevant. Never use filler — every added line must be truthful, relevant, and impact-focused.

## Full pipeline

1. Identify the best-matching CV from the `resumes/` folder (e.g. `resumes/ai-engineer-cv.md`). List files in `resumes/` if unclear. Read as source of truth.
2. Ask for the JD if not already in context (text or URL)
3. Extract 15-20 JD keywords
4. Detect JD language (EN default)
5. Detect company location -> paper format (US/Canada: `letter`, else: `a4`)
6. Rewrite Experience bullets by JD relevance (keep 3-4 bullets per role, inject keywords naturally)
7. Select top 2-3 projects most relevant to offer
8. Consolidate education, skills, languages, certifications, awards into structured sections
9. Build contact info row: location, phone, email, LinkedIn, portfolio
10. **Verify 1-page fit**: estimate total content. If too long: drop oldest jobs first, then reduce projects. If too short: expand bullets, add coursework, include GPA/honors.
11. **Generate Markdown and wait for approval** — Write to `output/{company-slug}/{position-slug}/cv-{candidate}-{company-slug}-{YYYY-MM-DD}.md`. Show full Markdown and ask:
    > "Here's the tailored CV (classic one-page format). Does everything look correct? Reply 'yes' to generate PDF."
    - If changes requested: apply to `.md` file on disk, show revised content, ask again.
    - **Do NOT proceed to PDF until user explicitly approves.**
12. **Re-read the `.md` file from disk** — after approval, read fresh from disk as source for HTML generation.
13. Generate HTML from template + tailored content, replacing all {{placeholders}}
14. Write HTML to `/tmp/cv-{candidate}-{company-slug}.html`
15. Run: `node generate-pdf.mjs /tmp/cv-{candidate}-{company-slug}.html output/{company-slug}/{position-slug}/cv-{candidate}-{company-slug}-{YYYY-MM-DD}.pdf --format={letter|a4}`
16. Report PDF path, Markdown path, page count, keyword coverage %
17. **If page count ≠ 1**: go back, adjust content, regenerate. Repeat until exactly 1 page.

**Output directory convention:** `output/{company-slug}/{position-slug}/` where slugs are lowercase-hyphenated (e.g., `output/openai/senior-ml-engineer/`). Both the `.md` and `.pdf` files live in this folder.

## ATS rules (clean parsing)

- Single-column layout (no sidebars, no parallel columns)
- Standard headers: "Professional Summary", "Work Experience", "Education", "Skills", "Certifications", "Projects"
- No text embedded in images/SVGs
- No critical information in PDF headers/footers (ATS often ignores them)
- UTF-8, selectable text (not rasterized)
- No nested tables
- JD keywords distributed across Summary (top 5), the first bullet of each role, and the Skills section

## PDF design (classic resume, professional serif)

- **Font**: Georgia serif (or Times New Roman fallback) — classic, professional, ATS-friendly
- **Header**: name centered 24px bold, contact row centered below (10px, no bullets, pipe separators)
- **Section headers**: 11px bold uppercase, 2px black bottom border (full width), 3px padding below
- **Body text**: 11px, line-height 1.5, generous readable spacing
- **Company/institution names**: bold (11px), left-aligned
- **Dates/locations**: 11px, right-aligned, flush to margin
- **Bullets**: 3-4 per job, 1-2 lines each, impact-focused with metrics
- **Margins**: 0.5in all sides
- **Spacing**: 8px between major sections, 2px between related items
- **Background**: pure white
- **Colors**: black text only. Links: no underline, black. No colored tags or accents.
- **No gradients, no sidebars, single column, classic resume look**

## Section order (classic resume format, maximum 1 page)

1. **Header** (centered name, contact row: location, phone, email, LinkedIn, portfolio)
2. **Education** (reverse chronological, 2-3 schools, include GPA/honors/coursework)
3. **Work Experience** (reverse chronological, 2-3 most relevant roles, 3-4 bullets each, impact-focused with metrics)
4. **Projects** (optional, 3-4 most relevant, 1-2 line descriptions, include achievements)
5. **Activities** (optional, leadership/volunteer roles, 1-2 bullets each)
6. **Additional** (consolidated section: Technical Skills, Languages, Certifications & Training, Awards)

**Page-fill strategy:**
- Use Georgia serif font for classic professional look
- Tight spacing (11px body, 1.5 line-height)
- 0.5in margins on all sides
- Full-width section header underlines
- Right-aligned dates/periods for all entries
- If content is too long: drop oldest/least-relevant jobs first, then reduce project count
- If content is too short: expand bullet counts, add relevant coursework details, include honors/GPA

## Keyword injection strategy (ethical, truth-based)

For classic resume format, inject JD keywords into work experience bullets naturally:

Examples:
- JD says "RAG pipelines" and CV says "LLM workflows" → rewrite to "Designed RAG pipeline for document retrieval, improving query accuracy by 40%"
- JD says "lead cross-functional teams" and CV says "worked with engineers" → rewrite to "Led cross-functional team of 5 engineers and product managers on API redesign"
- JD says "AWS" and CV says "cloud infrastructure" → rewrite to "Built infrastructure on AWS, reducing deployment time from 2h to 15m"

**NEVER fabricate skills.** Only reframe real experience using JD vocabulary. Focus on metrics and measurable impact in every bullet.

## HTML template

Use the template at `cv-template.html`. Replace the `{{...}}` placeholders with tailored content:

| Placeholder | Content |
|-------------|---------|
| `{{LANG}}` | `en` or `es` |
| `{{PAGE_WIDTH}}` | `8.5in` (letter) or `210mm` (A4) |
| `{{NAME}}` | (from profile.yml) |
| `{{CONTACT_INFO}}` | Contact row: location, phone, email, LinkedIn, portfolio (pipe-separated) |
| `{{SECTION_EDUCATION}}` | Education |
| `{{EDUCATION}}` | Education HTML (degree, institution, location, date, GPA, coursework) |
| `{{SECTION_EXPERIENCE}}` | Work Experience |
| `{{EXPERIENCE}}` | HTML for each job (company, title, dates, location, 3-4 bullets) |
| `{{SECTION_PROJECTS}}` | Projects (optional) |
| `{{PROJECTS}}` | HTML for 3-4 most relevant projects |
| `{{SECTION_ACTIVITIES}}` | Activities (optional, extracurriculars, volunteer work) |
| `{{ACTIVITIES}}` | HTML for leadership/volunteer roles |
| `{{SECTION_ADDITIONAL}}` | Additional |
| `{{ADDITIONAL}}` | Skills, Languages, Certifications, Awards (all in one section) |
| `{{#IF_PROJECTS}}...{{/IF_PROJECTS}}` | Conditional: only render Projects section if projects exist |
| `{{#IF_ACTIVITIES}}...{{/IF_ACTIVITIES}}` | Conditional: only render Activities section if activities exist |

## Canva CV Generation (optional)

If `config/profile.yml` has `canva_resume_design_id` set, offer the user a choice before generating:
- **"HTML/PDF (fast, ATS-optimized)"** — existing flow above
- **"Canva CV (visual, design-preserving)"** — new flow below

If the user has no `canva_resume_design_id`, skip this prompt and use the HTML/PDF flow.

### Canva workflow

#### Step 1 — Duplicate the base design

a. `export-design` the base design (using `canva_resume_design_id`) as PDF → get download URL
b. `import-design-from-url` using that download URL → creates a new editable design (the duplicate)
c. Note the new `design_id` for the duplicate

#### Step 2 — Read the design structure

a. `get-design-content` on the new design → returns all text elements (richtexts) with their content
b. Map text elements to CV sections by content matching:
   - Look for the candidate's name → header section
   - Look for "Summary" or "Professional Summary" → summary section
   - Look for company names from the selected `resumes/` CV file → experience sections
   - Look for degree/school names → education section
   - Look for skill keywords → skills section
c. If mapping fails, show the user what was found and ask for guidance

#### Step 3 — Generate tailored content

Same content generation as the HTML flow (Steps 1-11 above):
- Rewrite Professional Summary with JD keywords + exit narrative
- Reorder experience bullets by JD relevance
- Select top competencies from JD requirements
- Inject keywords naturally (NEVER invent)

**IMPORTANT — Character budget rule:** Each replacement text MUST be approximately the same length as the original text it replaces (within ±15% character count). If tailored content is longer, condense it. The Canva design has fixed-size text boxes — longer text causes overlapping with adjacent elements. Count the characters in each original element from Step 2 and enforce this budget when generating replacements.

#### Step 4 — Apply edits

a. `start-editing-transaction` on the duplicate design
b. `perform-editing-operations` with `find_and_replace_text` for each section:
   - Replace summary text with tailored summary
   - Replace each experience bullet with reordered/rewritten bullets
   - Replace competency/skills text with JD-matched terms
   - Replace project descriptions with top relevant projects
c. **Reflow layout after text replacement:**
   After applying all text replacements, the text boxes auto-resize but neighboring elements stay in place. This causes uneven spacing between work experience sections. Fix this:
   1. Read the updated element positions and dimensions from the `perform-editing-operations` response
   2. For each work experience section (top to bottom), calculate where the bullets text box ends: `end_y = top + height`
   3. The next section's header should start at `end_y + consistent_gap` (use the original gap from the template, typically ~30px)
   4. Use `position_element` to move the next section's date, company name, role title, and bullets elements to maintain even spacing
   5. Repeat for all work experience sections
d. **Verify layout before commit:**
   - `get-design-thumbnail` with the transaction_id and page_index=1
   - Visually inspect the thumbnail for: text overlapping, uneven spacing, text cut off, text too small
   - If issues remain, adjust with `position_element`, `resize_element`, or `format_text`
   - Repeat until layout is clean
d. Show the user the final preview and ask for approval
e. `commit-editing-transaction` to save (ONLY after user approval)

#### Step 5 — Export and download PDF

a. `export-design` the duplicate as PDF (format: a4 or letter based on JD location)
b. **IMMEDIATELY** download the PDF using Bash:
   ```bash
   mkdir -p "output/{company-slug}/{position-slug}/"
   curl -sL -o "output/{company-slug}/{position-slug}/cv-{candidate}-{company-slug}-canva-{YYYY-MM-DD}.pdf" "{download_url}"
   ```
   The export URL is a pre-signed S3 link that expires in ~2 hours. Download it right away.
c. Verify the download:
   ```bash
   file "output/{company-slug}/{position-slug}/cv-{candidate}-{company-slug}-canva-{YYYY-MM-DD}.pdf"
   ```
   Must show "PDF document". If it shows XML or HTML, the URL expired — re-export and retry.
d. Report: PDF path, Markdown path, file size, Canva design URL (for manual tweaking)

#### Error handling

- If `import-design-from-url` fails → fall back to HTML/PDF pipeline with message
- If text elements can't be mapped → warn user, show what was found, ask for manual mapping
- If `find_and_replace_text` finds no matches → try broader substring matching
- Always provide the Canva design URL so the user can edit manually if auto-edit fails

## Post-generation

Update the tracker if the offer is already registered: change PDF from ❌ to ✅.
Both output files (`cv-...md` and `cv-...pdf`) will be in `output/{company-slug}/{position-slug}/`.
