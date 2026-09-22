# VJEŠTINE ZA ŽIVOT

> **Znam probati. Znam provjeriti. Znam kada tražiti pomoć.**

A Croatian practical-life-skills publishing project: three coordinated books, their companion resources, and a separately reviewed route to future educational editions.

**Owner:** Repository owner / series producer. **Planning baseline:** 22 September 2026. **Repository guide:** version 1.0, 22 September 2026.

**Current state:** planning, not production. The supplied CSVs are chapter briefs and a proposed roadmap. There are no finished manuscripts, illustrations, implemented build scripts, contracted reviewers or institutional approvals in this starter package. The tooling and folders described below are a proposed implementation. Do not confuse a roadmap row, an asset ID or a generated draft with a completed deliverable.

## 1. What we are building

| Book | Working subtitle | Readers | Planned pages |
|---|---|---|---:|
| B1 | Mali koraci, velike vještine | Primary grades 1-4; co-reading in grades 1-2 | 192 |
| B2 | Mogu više! | Primary grades 5-8; additional scaffolding for grade 5 | 224 |
| B3 | Spremni za samostalan život | High school; distinguish three- and four-year routes | 256 |

Each book has **60 skills in 10 modules, plus 10 integrated missions**. The series progresses from supported everyday practice to planning, decision-making and navigating adult systems. Money, cooking, communication, learning, digital judgment, health, home care, transport and help-seeking recur at increasing levels of complexity.

The books are a set: one proposed 190 x 240 mm trim, coordinated covers and spines, one typography and illustration system, and increasingly mature presentation. Design rules live in [06_series_design_system.csv](06_series_design_system.csv), not in an agent's memory.

The associated product plan includes parent/caregiver guides, teacher guides, worksheets and answer notes, 72-card decks, private skills passports, an account-free companion website, optional quizzes, and later audio, specialist accessible editions, videos, workshops, classroom kits, translations, an app and a boxed set. Physical decks and major digital expansions are conditional investments, not launch requirements.

**Strategy:** design the series together, validate a small sample, publish sequentially, and expand only on evidence. The first production experiment is nine chapter packets and coordinated cover/spine concepts, not all 180 chapters.

## 2. Start here

1. Extract the original planning pack and place its **11 CSVs and README_START_HERE.md at the repository root**. Put this README.md and AGENTS.md beside them. Do not keep the only usable files inside the ZIP or create duplicate working CSV folders.
2. Create a private repository. Keep personal data, participant permissions, signed contracts, credentials and confidential legal advice outside it. A private Git remote is not a suitable place for every kind of confidential record.
3. Preserve the original state in the first commit. Read [AGENTS.md](AGENTS.md) before authorising an agent to edit anything. Read [README_START_HERE.md](README_START_HERE.md) for the original planning assumptions and limitations; treat it as a historical baseline.
4. Run a read-only audit. Verify filenames, row counts, real CSV headers, IDs, references, dependencies and page budgets. Establish the validator before bulk editing. No project-specific validation or rendering command has been implemented yet.
5. Choose a cash/time ceiling and the next eligible task. Filter the roadmap by `Planning_Week_Start <= 4` to see the initial work, but obey dependencies and gates rather than dates alone.
6. Give an agent one bounded task, inspect its diff and evidence, then accept or revise it. Keep a short work log so the next session resumes from files, not remembered chat.

For a new local repository, after inspecting the directory and ensuring only intended planning files are present:

```sh
git init
git status --short
git add README.md AGENTS.md README_START_HERE.md "*.csv"
git diff --cached --stat
git diff --cached
git commit -m "docs: establish life-skills publishing baseline"
git tag plan-2026-09-22
```

Skip `git init` when the repository already exists. These commands do not create a remote repository or upload anything. Configure Git identity if required. Decide line-ending policy before the first commit; the supplied CSVs use UTF-8 BOM and CRLF records. A proposed `.gitattributes` policy is `*.csv -text` to preserve those bytes, with `*.md text eol=lf` and equivalent LF rules for scripts and structured text. Add this configuration during bootstrap; it is not included in this two-file addition. Never run a blanket line-ending normalisation across the baseline.

Use the conventional filename **AGENTS.md**, including its lowercase extension. Do not maintain another copy called AGENTS.MD; case-sensitive systems and agent discovery can distinguish them.

## 3. The planning files and their authority

Counts below describe the initial baseline, not permanently fixed database constraints.

| File | Rows | Purpose / stable key |
|---|---:|---|
| [01_master_roadmap.csv](01_master_roadmap.csv) | 219 | Tasks, dependencies, gates and progress; `Task_ID` |
| [02_book_1_topics.csv](02_book_1_topics.csv) | 60 | B1 scope and chapter briefs; `Topic_ID` |
| [03_book_2_topics.csv](03_book_2_topics.csv) | 60 | B2 scope and chapter briefs; `Topic_ID` |
| [04_book_3_topics.csv](04_book_3_topics.csv) | 60 | B3 scope and chapter briefs; `Topic_ID` |
| [05_products_and_companions.csv](05_products_and_companions.csv) | 39 | Product scope and release conditions; `Product_ID` |
| [06_series_design_system.csv](06_series_design_system.csv) | 30 | Shared design contract; `Design_ID` |
| [07_curriculum_mapping.csv](07_curriculum_mapping.csv) | 55 | Proposed links to official anchors; `Map_ID` |
| [08_policy_and_approval_tracker.csv](08_policy_and_approval_tracker.csv) | 15 | Policy status, route and review actions; `Policy_ID` |
| [09_risks_and_quality_gates.csv](09_risks_and_quality_gates.csv) | 26 | Risks, controls and evidence; `Risk_ID` |
| [10_sources.csv](10_sources.csv) | 34 | Seed evidence register; `Source_ID` |
| [11_module_missions.csv](11_module_missions.csv) | 30 | Integrated applications; `Mission_ID` |

**Authority by subject:** the roadmap owns task status; topic CSVs own planned chapter scope; the design CSV owns agreed visual rules; manuscript files will own reader-facing wording; claim and review records will own supporting evidence; layout files will own placement; exported PDFs are outputs, never manuscript masters.

IDs are permanent, not page numbers. `B3-028` stays the same when its position or title changes. Planned derivatives include `-W01` (worksheet), `-C01` (card), `-TG` (teacher notes), `-PG` (parent notes) and `-Q01` (optional self-check). `B3-M05-MISSION` identifies a module mission. An ID being listed does not mean its file already exists.

Do not change schema, IDs, safety boundaries, release gates or the shared design casually. Record an approved decision first. Keep planned dates distinct from actual dates. The original status columns with `2026_09_22` in their names are historical snapshots: do not silently write today's policy status under a September 2026 heading.

## 4. Proposed repository structure

Keep the original planning files at root until an explicit migration is approved. Create additional directories only when their first real deliverable is needed.

```text
/
  README.md
  AGENTS.md
  README_START_HERE.md                 # original snapshot
  01_master_roadmap.csv ... 11_module_missions.csv
  docs/
    decisions/                        # dated scope/tooling/design decisions
    work-log.md                       # session outcomes and next task
    tooling.md                        # installed versions and proven commands
    policy-review-log.md               # dated changes after the baseline
    reviews/                          # non-sensitive review evidence
  schemas/                            # versioned CSV/content contracts
  content/
    book-1/chapters/B1-020.md
    book-1/companions/B1-020-W01.md
    book-1/companions/B1-020-C01.md
    book-1/companions/B1-020-TG.md
    book-1/companions/B1-020-PG.md
    book-1/missions/B1-M04-MISSION.md
    book-2/                           # same pattern
    book-3/                           # same pattern
  evidence/
    claims/B1-020.yaml                 # claim-level sources and open questions
    reviews/B1-020.yaml                # review status and exact revision
    assets/                           # rights/provenance metadata, not contracts
  design/
    tokens.json                       # machine-readable approved design rules
    style-guide.md
    references/                       # cleared reference sheets
    templates/                        # editable native layout templates
  assets/
    shared/                           # SVG icons and reusable components
    book-1/                           # SVG / layered art sources and exports
    book-2/
    book-3/
  layouts/
    book-1/                           # native master and import/revision manifest
    book-2/
    book-3/
    companions/                       # Typst or chosen companion renderer
  scripts/                            # validators and proven local automation
  prompts/                            # approved, versioned task/art briefs
  build/                              # ignored intermediate output and previews
  releases/                           # small manifests/checksums, not every PDF
```

**Storage policy:** commit Markdown, CSV, JSON/YAML, SVG, scripts, rights metadata and decisions in ordinary Git. Use Git LFS or a separately versioned asset store for large `.af`, `.kra`, `.psd`, TIFF, audio and video sources. Git LFS stores pointers in Git; the actual objects also need backup and restore testing [T15]. Keep temporary renders, caches, model weights, API credentials and participant records out of Git. An ignored directory is not a security boundary.

Store official source snapshots only when retention and redistribution are permitted. Otherwise retain the URL, title, publisher, date, exact section and a short evidence note; sensitive or restricted originals stay in controlled storage referenced by an opaque record ID. Keep font names, versions, licences and installation instructions, not redistributed font binaries.

## 5. Work through the plan without losing control

### The first working sequence

| Stage | Existing tasks to start from | Exit evidence |
|---|---|---|
| Project control | STR-01; then STR-02 and STR-06 | Agreed promise, exclusions, audience and spending limit |
| Evidence and governance | CUR-01; LEG-01 and dependent LEG tasks | Dated source register, legal questions and safe working routes |
| Design and feasibility | DSN-01, DSN-02, DSN-03, DSN-06 | Set-wide art direction, chapter templates and comparable print quotes |
| Capacity and investment | STR-05, STR-07, STR-08, STR-09, STR-10 | Reviewer capacity, unit economics and a funded prototype decision |
| Representative prototype | PIL-01 and its prerequisites | Nine chapter packets, companion samples and coordinated covers |
| Review before children | PIL-02, LEG-04, LEG-06, PIL-04 | Required professional review, permissions and safeguarding evidence |
| Test, revise, decide | PIL-05 through PIL-10, following the graph | Documented findings and Book 1 go/no-go decision |

The nine prototype topics are **B1-016/020/032, B2-017/019/044 and B3-002/013/047**. Begin with one end-to-end packet, such as B1-020, to prove the workflow before scaling to nine. A low-risk technical layout test is not permission for child-facing testing.

The roadmap's proposed launches are June 2027, February 2028 and October 2028. They assume parallel contracted capacity. Rebaseline transparently if resources change; do not compress review to preserve a date. Grants and unsigned institutional orders remain zero in the base financial case.

### One task at a time

Read the task, dependencies and acceptance criteria. Identify the permitted files. Draft the deliverable; log sources and unresolved questions. Run the relevant checks. Obtain required human review. Record evidence and status, then commit a coherent change.

Use task states `NOT STARTED`, `IN PROGRESS`, `BLOCKED`, `REVIEW`, `DONE`. The original longer value `NOT STARTED - proposed plan` is the initial not-started state; do not bulk-normalise it unnecessarily. A proposed schema extension may add `Assigned_To`, `Actual_Start`, `Actual_End`, `Evidence_Paths`, `Blocker` and `Last_Updated`; approve and document the extension before adding columns. Until then, record those details in the work log using the task ID.

`DONE` means the specific task's acceptance criteria are satisfied. Completing an authoring task does not mean the content is safe for children, print-ready or officially approved. Agents can record their work and prepare reviews; they cannot impersonate a qualified reviewer or approve an owner's funding gate.

### One chapter packet

Store reader-facing text in Croatian Markdown, with compact front matter such as:

```yaml
---
topic_id: B1-020
language: hr-HR
content_revision: 0.1.0
workflow_state: draft
---
```

Read planned page count, grade band, supervision and mapping from the topic CSV instead of maintaining conflicting copies. Proposed chapter sections are **Situacija / Što trebam / Koraci / Zastani i provjeri / Isprobaj / Što sada znaš?**

For each packet, produce the core text, offline activity, observable check, accessible alternative, art brief, worksheet/card content, parent and teacher notes, claim evidence and review record. Each companion names the core revision it derives from. Teacher notes contain curriculum codes; child pages do not become administrative documents.

Claim records should state the exact claim, source ID/URL and section, applicability, date checked, verification status and reviewer role. A source in the seed register is a lead, not proof that every operational claim in the chapter is correct. Review evidence identifies the specific content/art revision and records unresolved findings. Any substantive safety change makes dependent reviews stale.

### A normal weekly rhythm

Choose a small dependency-ready batch; keep authorship, specialist review and design visible as separate work. At the end of the batch, inspect changed pages at actual size, update risks and evidence, review spending and decide the next task. Use separate branches or worktrees for parallel agents, with one integration owner for shared CSVs and templates. Do not create a large autonomous writing factory before the first complete packet works.

## 6. Local-first production stack

These are recommendations checked against official product documentation on 22 September 2026, not installed integrations. Prices, feature availability and terms must be rechecked before purchase or production use. **Local files do not imply local AI inference.** Cloud assistants can receive prompts, documents or tool results even when the desktop application and repository are local.

| Layer | Recommended starting choice | What stays local / important limit |
|---|---|---|
| Repository work | VS Code with Codex CLI/IDE, or Claude Code | Plain-text source, diffs and scripts; verify that AGENTS.md actually loads [T01-T03] |
| Illustrated trade-book layout | Affinity desktop | Editable `.af` documents, templates and placed assets; current app supports local saving, book output and print PDF presets [T04-T06] |
| AI-assisted layout | Affinity's official Claude Desktop connector and JavaScript scripting | Local MCP server and reusable scripts; beta capabilities need a small proof before dependence [T07-T09] |
| Reusable vector art | Inkscape | Native SVG, suitable for local editing and scripted exports; inspect generated paths visually [T10] |
| Generated vector candidates | Recraft, on an appropriately licensed commercial plan | Download SVGs and provenance immediately; free-plan assets are not for commercial use under current terms [T11-T12] |
| Rich illustrations | OpenAI image generation/editing API; Affinity or Krita for cleanup | Save image outputs, prompts and source references; raster generation does not supply editable SVG layers [T13-T14] |
| Repeated companion layouts | Typst; Pandoc where Markdown conversion is useful | Text-based templates and local builds; custom adapters must be implemented, and PDF/X is not in Typst's documented supported standards [T16-T18] |
| Later local generation | ComfyUI | Version workflows and API-format JSON, with models separately managed; hardware, custom-node security and model licences add maintenance [T19-T20] |

**My proposed default:** Affinity for the visually rich trade books; Markdown and SVG as durable content/art sources; Typst for repetitive cards, worksheets and guide prototypes when volume justifies a renderer. Keep one active layout master per product. Do not maintain two independently edited book layouts and promise automatic round-tripping.

Affinity's September 2026 automation documentation is especially relevant: agents can help author reusable JavaScript, and the official Claude Desktop connection operates through a local MCP server [T07-T09]. The documented connector is not proof that Codex or every terminal agent can drive it without further integration. Start with a copy of one spread and test text replacement, an illustration swap, saving/reopening, preview export and undo. Use least-privilege file access; keep network access and paid AI features off unless a task needs them. Do not confuse the creative application at `affinity.studio` with the unrelated Affinity CRM.

A designer already working in Adobe InDesign can use it instead; Adobe documents JavaScript-based UXP scripts [T21]. Specify editable source delivery and script/source ownership in the contract. Do not buy several layout ecosystems before selecting the person and workflow responsible for production.

### Keep manuscript and layout in sync

Make wording changes in Markdown first. Import or apply them to the native layout, recording the exact source revision in a layout manifest. Use stable named frames/layers such as `B1-020.situation` and `B1-020.stop`. An agent should not blindly reflow a whole book to fix one paragraph. Record any late layout copy edit back in Markdown before release. Scripts should update intended objects idempotently, preserve unrelated manual work and fail when IDs are missing or duplicated.

For Typst, choose a documented conversion path: Markdown through Pandoc and project templates/filters, or a tested content adapter. Native Typst does not automatically understand arbitrary Markdown chapter files. Generated intermediate `.typ` or JSON files belong in `build/`, not as a second text master. The current docs support local PDF output but do not list PDF/X; ask the chosen printer to approve a sample or use a qualified prepress workflow [T16-T18].

## 7. Graphics that can actually be revised

Create a cleared style reference pack before generating lots of images: character sheets, proportions, line weight, palette, perspectives, icon rules and examples for all three age bands. Prefer illustrations without baked-in labels; set Croatian text and numeric labels in the layout or a separately editable text layer.

For every accepted image keep the editable SVG or layered source where available, a preview, the art brief, creator/provider/model information, generation date, prompt and inputs, rights basis, restrictions, source revision and required technical-review record. Store cloud output bytes, not just a temporary URL or a provider-side style ID.

**Use vector art for reusable instructional objects and diagrams.** Use raster illustrations for scenes where a vector workflow is not practical. Putting a PNG inside an SVG does not make its objects editable. Inkscape can edit SVG paths; Krita retains layered work in KRA, which should be treated as a binary asset rather than a text-merge target [T10, T14].

Recraft's current rules distinguish assets made on free and paid plans, and upgrading later does not retroactively clear free-plan output. Its terms also prohibit using generated assets to train AI models [T12]. Archive the applicable terms and confirm the exact studio/API licence. Do not treat a provider's commercial-use permission as proof of copyright exclusivity or permission to copy protected reference art.

For generative work, prefer targeted edits to approved source images over complete regeneration. Retain masks, reference images and workflow settings when available. Seeds and prompts alone are not a guarantee of identical regeneration. Technical illustrations require subject-matter review even when they look convincing; safety-critical visuals must never be approved on aesthetics alone.

## 8. Education, safety and release gates

The original plan distinguishes thematic relevance, code-level mapping, teacher review, submission, approval/listing, school selection and actual funding. Preserve those distinctions. The 55 seed mapping rows are proposed applications, not 55 approved lessons. Unmapped topics stay unmapped until evidence supports an exact grade/pathway match.

For new education decisions, recheck primary sources from MZOM, AZOO, ASOO, CARNET, Narodne novine and other competent bodies as applicable. Record publication date, effective date, scope, review date and the decision affected. Existing experiments, guidance, enacted rules and unconfirmed future changes must remain separate. Do not carry a deadline or agency route from one material type to another without verification. See files 07, 08 and 10 and the original README for the baseline, not a permanent statement of law.

Supervision tiers are editorial safeguards: **L** low-risk; **A** active responsible-adult supervision; **P** qualified professional/instructor. They are not legal permissions or proof of competence. Professional help-seeking counts as success. Chapter B3-028 is bounded automotive awareness and supervised, model-specific instruction development, not a generic jump-start tutorial.

Before child-facing testing or publication, require the applicable professional safety/factual review, Croatian editing, rights clearance, privacy/safeguarding arrangements and accessible alternatives. First aid uses qualified review and inert/mannequin practice, not manoeuvres on peers. High-risk electrical, gas and vehicle work must stay within its approved boundary. No child is asked to reveal real passwords, household income, trauma or intimate information. Civic activities assess evidence and procedure, never political preferences.

Before print, verify the printer's actual trim, bleed, colour profile, binding/spine dimensions, output specification and proof requirements. A successful PDF export is not a print approval. Check every changed page, correct spreads and page counts, QR destinations, font rendering and image quality at actual size. Never shrink safety text to meet a page target. Keep a separate accessible digital export when the print workflow does not preserve accessibility.

A release manifest should record the Git commit, content/design versions, final file hashes, source refresh, rights and review references, printer proof approval and unresolved noncritical limitations. Human owners approve print orders, public releases and school submissions. Safety corrections reopen every affected book, card, guide, worksheet, quiz, audio and video derivative.

## 9. First agent assignment

Use this before requesting manuscripts or graphics:

```text
Read README.md, AGENTS.md, README_START_HERE.md and the actual CSV headers.
Perform a read-only repository audit. Report counts, duplicate IDs, missing
references, task dependency problems, page-budget totals and any conflicting
instructions. Distinguish planned asset IDs from missing release deliverables.
Do not change CSVs or their statuses. Do not browse, install packages, generate
images, incur charges, create commits or contact anyone for this audit.
Propose the smallest bootstrap change: schemas, a Python-standard-library CSV
validator, a work log and safe Git configuration. Document proposed commands
as unimplemented until created and tested. Stop with the audit and a bounded
implementation proposal; do not start writing the books.
```

After accepting that proposal, implement the validator and one chapter packet/template pipeline. Record decisions and actual tested commands in `docs/tooling.md`. Give the layout assistant the applicable chapter, design rules, art and safety requirements explicitly; a graphical desktop assistant does not necessarily discover repository instructions like a coding agent.

## 10. Official tooling references

These references support tool capabilities and limitations above; they do not extend or validate the project's curriculum sources. Checked 22 September 2026. Do not pin the project to a moving `latest` model or tool version without recording the resolved version.

- **T01:** [Codex CLI](https://learn.chatgpt.com/docs/codex/cli).
- **T02:** [Codex AGENTS.md discovery](https://learn.chatgpt.com/docs/agent-configuration/agents-md).
- **T03:** [Claude Code project memory and AGENTS.md conditions](https://code.claude.com/docs/en/memory). Support depends on version/settings; a small CLAUDE.md containing `@AGENTS.md` is a documented compatibility option, not a second copy of the rules.
- **T04:** [Affinity local saving and editable .af format](https://www.affinity.studio/help/get-started-save/).
- **T05:** [Affinity book output](https://www.affinity.studio/help/advanced-outputting-books/).
- **T06:** [Affinity PDF export presets](https://www.affinity.studio/help/sharing-pdf-presets/).
- **T07:** [Affinity AI automation with Claude and local MCP setup](https://www.affinity.studio/help/ai-connector-setup/).
- **T08:** [Affinity running scripts](https://www.affinity.studio/help/running-scripts/) and [scripting permissions](https://www.affinity.studio/help/desktop-settings-scripting/).
- **T09:** [Affinity SDK 3.3 documentation; scripting beta](https://sdk.affinity.studio/33000/).
- **T10:** [Inkscape SVG and command-line export documentation](https://www.inkscape.org/doc/inkscape-man100.html). Check installed-version help before using options from version-specific documentation.
- **T11:** [Recraft vector model and editable SVG output](https://www.recraft.ai/docs/api-reference/models/recraft-v4).
- **T12:** [Recraft ownership and commercial-use conditions](https://www.recraft.ai/docs/trust-and-security/ownership).
- **T13:** [OpenAI image generation/editing guide](https://developers.openai.com/api/docs/guides/image-generation) and [image edit API output formats](https://developers.openai.com/api/reference/python/resources/images/methods/edit).
- **T14:** [Krita working file formats](https://docs.krita.org/en/general_concepts/file_formats.html).
- **T15:** [Git LFS pointer/object storage](https://docs.github.com/repositories/working-with-files/managing-large-files/about-git-large-file-storage).
- **T16:** [Typst overview and local compiler](https://typst.app/docs/).
- **T17:** [Typst PDF export and supported standards](https://typst.app/docs/reference/pdf/).
- **T18:** [Pandoc conversion and PDF engines](https://pandoc.org/MANUAL.html).
- **T19:** [ComfyUI local/cloud CLI and agent-readable JSON](https://docs.comfy.org/comfy-cli/getting-started).
- **T20:** [ComfyUI workflow API format](https://docs.comfy.org/development/api-development/workflow-api-format).
- **T21:** [Adobe InDesign UXP scripting](https://developer.adobe.com/indesign/uxp/scripts/getting-started/).

**Commercial content remains rights-controlled.** Creating a Git repository does not grant reuse rights. Do not apply an open-source licence to manuscripts, illustrations or licensed assets by default; decide tooling and publication licences separately.
