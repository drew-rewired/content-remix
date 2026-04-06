# Changelog

All notable changes to the Content Remix Skill are documented here.

---

## [2.0] — 2026-04-06

### Added
- **Funnel stage detection** — Source asset is scanned for TOFU/MOFU/BOFU signals on input. Detected stage and rationale surfaced in the Gate 1 confirmation summary.
- **Gate 1.5 — Output stage lock** — After source stage is confirmed, a separate gate asks whether the output should match the source stage, reposition to a different stage, or confirm per format. Stage drives CTA weight, vocabulary, and internal link targets.
- **Content Brief mode** — New Gate 1 input type (option 6): write net-new content from a brief without a source asset. If a Content Map report is loaded, gaps are scanned and presented as a numbered list for pre-population. Manual brief intake collects topic (required), target keyword, funnel stage, key points, and reference URLs. If key points are skipped, an outline is generated and confirmed before writing begins.
- **Internal linking waterfall** — Internal links are always attempted. Priority order: Content Map → sitemap crawl (`{domain}/sitemap.xml`) → user-provided page list → homepage nav crawl. Covers both content pages (3–6 links) and company/CTA pages (1–2 links). Applies to all applicable formats and Optimize Original mode.
- **GEO (Generative Engine Optimization)** — Added as a third quality framework alongside EEAT and AEO. Signal checklist: direct extractable answers, named entity references, verifiable factual claims, structured prose, citations present, self-contained sections. Runs as part of the post-generation review for landing pages, blog posts, white papers, and ebooks.
- **YMYL flag** — When the saved domain or content topic is healthcare, finance, or legal, an elevated EEAT standard is triggered: "Every claim must be traceable. Every credential signal must be present. Missing or thin EEAT in YMYL content is a hard quality failure, not a minor gap."
- **Quality Gate** — Internal self-review step that runs after generation and before delivery. Checks: brand voice compliance, claim traceability, filler/vague statements, structure compliance, YMYL flag, Experience vs. Expertise distinction, GEO signal checklist, structured elements per section. Only surfaces to the user if issues require their input.
- **Optimize Original mode** — Same-format optimization: improved structure, stronger EEAT/AEO/GEO signals, internal links added, copy tightened. Triggered when a URL matching the saved config domain is submitted, or selectable as option 12 in Gate 2.
- **AskUserQuestion prompts throughout gates** — Gates with ≤4 options now use the AskUserQuestion tool for clickable selection: brand doc detection, onboarding, return launch, Gate 1.5, Gate 2 (white paper, ebook, email, podcast, presentation, social, research mode, citation approval, pre-run confirmation, and more).
- **Per-section chunk targets** — All output skeletons include a 200–400 word (~300–500 token) target per section. Sections over 600 words without a structured break are flagged as an LLM chunking risk.
- **Structured element requirement** — Every major section in every output skeleton requires at least one structured element: TL;DR block, Q&A block, definition block, numbered/bulleted list, or comparison table.
- **Zero-click framing** — EEAT/AEO/GEO explanation blocks include: "59% of Google searches end without a click. Being cited in an AI answer IS the distribution."
- **User intent label per format** — Gate 2 now surfaces the dominant user intent type (Know / Evaluate / Do) for the selected format. Used to shape output structure.

### Changed
- **12 output formats** — White paper and ebook separated into two distinct options with different skeletons, Gate 3 questions, and structural standards. Optimize Original added as a selectable format.
- **Gate 1 input options** — Added option 6 "Content brief / Content Map gap." Renumbered "Other" to 7.
- **Gate 3 — single email** — Now includes goal question (4 options) and funnel stage question before proceeding to Gate 4. Previously had no scaffolding.
- **Gate 4 — distribution** — Added one-sentence impact explanation: paid outputs tighten CTA language and remove navigation; organic outputs keep navigation and are structured for search.
- **Blog post skeleton** — Added TL;DR block as a required opening element.
- **Behavior Reference table** — Extensively updated with all new rows for Gate 1.5, internal linking waterfall, content brief mode, quality gate, optimize original, YMYL, and GEO.

---

## [1.0] — 2026-04-05

### Added
- Initial release. Pre-run workflow with seven gates (input, output format, subtypes, channel intent, audience, research mode, job name).
- Ten channel-native output formats: blog post, email sequence, LinkedIn posts, social posts, landing page, podcast script, presentation outline, video/explainer script, infographic brief, ad copy variants.
- Memory and learning system (`content-remix-memory.json`): approved outputs logged for voice calibration; edit patterns auto-applied after three occurrences; format preferences surfaced as defaults after three consistent choices.
- Research mode with citation blocks — AskUserQuestion per citation (Approve / Reject / Find a replacement). Nothing woven into output until approved.
- Brand voice extraction from uploaded docs, URLs, or pasted text. Extracts brand voice, audience, and ICP — skips those onboarding steps if source is provided.
- Tabbed HTML output for multi-format jobs. Saved to `content-remix/jobs/{job-name}/output/`.
- Job folder naming and output saving across all runs.
- Version check on every launch — silent if current, one-line notice with update command if newer version is available.
