# Psychology Paper Reader Skill

An agent-agnostic Skill for evidence-traceable reading of psychology and cognitive-neuroscience papers. It turns a user-provided paper into a selectable structured analysis while keeping a clear boundary between what the paper reports, what is interpreted, and what needs verification.

The Skill responds in the primary language of the user's current request. It retains useful source-language terminology, abbreviations, and academic-writing patterns where helpful. If a mixed-language request has no clear primary language, it follows the most recent complete instruction.

## What it does

The user selects one of five output scopes. When offering this menu, the Skill gives each option a concise function description in the user's primary language:

- `Full Analysis`: all four modules.
- `Chunk 1 — Content Analysis`: paper logic, methods, results, discussion, and relevant visuals.
- `Chunk 2 — Academic Language`: reusable academic phrasing and terminology.
- `Chunk 3 — Citation Traceability`: whether and how the paper supports a specified claim.
- `Chunk 4 — Critical Reading`: paper-grounded appraisal and research directions.

The Skill supports empirical studies and review papers directly, and adapts to theory papers, qualitative/mixed-methods studies, registered reports, theses, abstract collections, and incomplete manuscripts.

| Module | Purpose |
| --- | --- |
| Chunk 1 — Content Analysis | Reconstruct the paper's argument, methods, evidence, results, discussion, and readable figures/tables. |
| Chunk 2 — Academic Language | Extract reusable academic-English patterns and a Chinese-English terminology glossary. |
| Chunk 3 — Citation Traceability | Trace a claim through the paper text, in-text citations, and readable reference list. |
| Chunk 4 — Critical Reading | Map results to claims, identify paper-visible limitations, and develop research directions. |

## Key safeguards

- Important claims should carry the most precise available source locator.
- Except for authorized external research in Chunk 4, analysis comes only from the supplied paper.
- Missing or unreadable material is reported, never silently filled with guesses.
- Readable tables and figures are checked as evidence and explained naturally when they support the requested analysis; users can ask for a dedicated figure or table walkthrough.
- Central result claims are cross-checked against readable text, tables, figures, abstract, and discussion; only conflicts or unclear scale directions that affect the conclusion are surfaced to the user.
- Further innovation requires explicit authorization for external search and the user's research topic.
- CAJ and scanned files are best-effort because readable extraction depends on the agent's local tools and OCR/conversion support.

## Use in an agent

Copy this repository's `SKILL.md` and `references/` folder into the skill/instructions location supported by your AI agent. If that agent uses another format, preserve the content hierarchy:

1. `SKILL.md` frontmatter becomes the name/description metadata.
2. The body becomes the main workflow instruction.
3. Keep `references/` available for conditional loading by paper type and selected Chunk.

Attach a paper, then ask the agent to use this Skill and select an output scope. See [examples/example-prompts.md](examples/example-prompts.md) for copyable prompts.

## Supported files

The workflow is designed for PDF, DOCX, DOC, TXT, Markdown, HTML, EPUB, CAJ, and scanned papers **when the host agent can extract their text**. PDF and DOCX are the primary V1 targets. A readable export, OCR result, or relevant page screenshots may be needed for inaccessible files.

## Extending beyond psychology

The core workflow is intentionally reusable: intake, document-type identification, output selection, evidence tracking, and external-search authorization. To add another discipline, create a discipline profile with its paper genres, terminology, reporting conventions, and critical-reading standards. Do not reuse psychology-specific methodological criteria as field-independent rules.

## Repository structure

```text
.
├── SKILL.md
├── references/
│   ├── empirical-paper.md
│   ├── review-paper.md
│   ├── nonstandard-paper.md
│   └── evidence-and-citations.md
└── examples/
    └── example-prompts.md
```

## License

This project is released under the [MIT License](LICENSE).
