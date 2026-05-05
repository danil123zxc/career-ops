# Graph Report - career-ops  (2026-05-05)

## Corpus Check
- 17 files · ~538,193 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 135 nodes · 223 edges · 11 communities detected
- Extraction: 85% EXTRACTED · 15% INFERRED · 0% AMBIGUOUS · INFERRED: 33 edges (avg confidence: 0.8)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Community 0|Community 0]]
- [[_COMMUNITY_Community 1|Community 1]]
- [[_COMMUNITY_Community 2|Community 2]]
- [[_COMMUNITY_Community 3|Community 3]]
- [[_COMMUNITY_Community 4|Community 4]]
- [[_COMMUNITY_Community 5|Community 5]]
- [[_COMMUNITY_Community 6|Community 6]]
- [[_COMMUNITY_Community 7|Community 7]]
- [[_COMMUNITY_Community 8|Community 8]]
- [[_COMMUNITY_Community 9|Community 9]]
- [[_COMMUNITY_Community 10|Community 10]]

## God Nodes (most connected - your core abstractions)
1. `PipelineModel` - 29 edges
2. `main()` - 12 edges
3. `ViewerModel` - 10 edges
4. `normalizeStatus()` - 7 edges
5. `apply()` - 7 edges
6. `error()` - 6 edges
7. `git()` - 6 edges
8. `main()` - 5 edges
9. `generatePDF()` - 4 edges
10. `readFile()` - 4 edges

## Surprising Connections (you probably didn't know these)
- `generatePDF()` --calls--> `error()`  [INFERRED]
  generate-pdf.mjs → verify-pipeline.mjs
- `run()` --calls--> `main()`  [INFERRED]
  test-all.mjs → dashboard/main.go
- `main()` --calls--> `error()`  [INFERRED]
  check-liveness.mjs → verify-pipeline.mjs
- `error()` --calls--> `NewViewerModel()`  [INFERRED]
  verify-pipeline.mjs → dashboard/internal/ui/screens/viewer.go
- `generatePDF()` --calls--> `readFile()`  [INFERRED]
  generate-pdf.mjs → test-all.mjs

## Communities

### Community 0 - "Community 0"
Cohesion: 0.18
Nodes (3): normalizeStatus(), statusLabel(), PipelineModel

### Community 1 - "Community 1"
Cohesion: 0.12
Nodes (8): newCatppuccinMocha(), appModel, viewState, main(), NewPipelineModel(), run(), NewTheme(), Theme

### Community 2 - "Community 2"
Cohesion: 0.15
Nodes (7): checkUrl(), main(), generatePDF(), normalizeTextForATS(), ViewerClosedMsg, readFile(), NewViewerModel()

### Community 3 - "Community 3"
Cohesion: 0.29
Nodes (12): checkAutoDir(), checkCv(), checkDependencies(), checkFonts(), checkNodeVersion(), checkPlaywright(), checkPortals(), checkProfile() (+4 more)

### Community 4 - "Community 4"
Cohesion: 0.36
Nodes (10): addPaths(), apply(), check(), compareVersions(), git(), gitStatusEntries(), localVersion(), revertPaths() (+2 more)

### Community 5 - "Community 5"
Cohesion: 0.22
Nodes (3): parseTsvContent(), validateStatus(), warn()

### Community 6 - "Community 6"
Cohesion: 0.27
Nodes (5): analyze(), classifyOutcome(), extractBlockerType(), normalizeStatus(), parseTracker()

### Community 7 - "Community 7"
Cohesion: 0.36
Nodes (1): ViewerModel

### Community 8 - "Community 8"
Cohesion: 0.25
Nodes (7): PipelineClosedMsg, PipelineLoadReportMsg, PipelineOpenReportMsg, PipelineOpenURLMsg, pipelineTab, PipelineUpdateStatusMsg, reportSummary

### Community 9 - "Community 9"
Cohesion: 0.4
Nodes (2): normalizeRole(), roleMatch()

### Community 10 - "Community 10"
Cohesion: 0.67
Nodes (2): CareerApplication, PipelineMetrics

## Knowledge Gaps
- **12 isolated node(s):** `viewState`, `ViewerClosedMsg`, `PipelineClosedMsg`, `PipelineOpenReportMsg`, `PipelineOpenURLMsg` (+7 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **Thin community `Community 7`** (10 nodes): `ViewerModel`, `.bodyHeight()`, `.Init()`, `.renderBody()`, `.renderFooter()`, `.renderHeader()`, `.Resize()`, `.styleLine()`, `.Update()`, `.View()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Community 9`** (6 nodes): `dedup-tracker.mjs`, `normalizeCompany()`, `normalizeRole()`, `parseAppLine()`, `parseScore()`, `roleMatch()`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.
- **Thin community `Community 10`** (3 nodes): `career.go`, `CareerApplication`, `PipelineMetrics`
  Too small to be a meaningful cluster - may be noise or needs more connections extracted.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `NewViewerModel()` connect `Community 2` to `Community 1`, `Community 4`?**
  _High betweenness centrality (0.250) - this node is a cross-community bridge._
- **Why does `error()` connect `Community 4` to `Community 2`, `Community 5`?**
  _High betweenness centrality (0.231) - this node is a cross-community bridge._
- **Why does `PipelineModel` connect `Community 0` to `Community 8`, `Community 1`?**
  _High betweenness centrality (0.156) - this node is a cross-community bridge._
- **Are the 6 inferred relationships involving `normalizeStatus()` (e.g. with `.applyFilterAndSort()` and `.cursorLineEstimate()`) actually correct?**
  _`normalizeStatus()` has 6 INFERRED edges - model-reasoned connections that need verification._
- **What connects `viewState`, `ViewerClosedMsg`, `PipelineClosedMsg` to the rest of the system?**
  _12 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Community 1` be split into smaller, more focused modules?**
  _Cohesion score 0.12 - nodes in this community are weakly interconnected._