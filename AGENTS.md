# Sealos Skills documentation — agent instructions

This repository (`sealos-skills-doc`) is the **single source of truth** for Sealos Skills behavior, pipeline contracts, and user-facing specifications. The implementation lives in [`labring/sealos-skills`](https://github.com/labring/sealos-skills).

## About this project

- Documentation site built on [Mintlify](https://mintlify.com)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- Mintlify MCP: `https://mcp.mintlify.com` (write access, requires OAuth)
- Mintlify docs MCP: `https://www.mintlify.com/docs/mcp` (read-only reference)

## SSOT rules

1. **Specs live here first.** Change `/skills/`, `/pipeline/`, or `/specs/` pages before changing `sealos-skills` implementation.
2. **Chinese is authoritative.** Root-path pages (default `zh-Hans`) are the normative SSOT. The `en/` directory is an English translation and may lag behind Chinese.
3. **Do not duplicate normative content** in `SKILL.md` without a corresponding doc page.
3. **Pages with `{/* TODO */}`** are structural placeholders awaiting content migration from `sealos-skills`.
4. **Cross-link both repos** in PR descriptions when behavior changes.

See [/contributing/ssot-workflow](/contributing/ssot-workflow) for the full change process.

## Terminology

Use terms from [/concepts/terminology](/concepts/terminology) consistently:

- **Skill** — workflow module (`sealos-deploy`, `sealos-database`, etc.)
- **Phase** — numbered deploy pipeline step (Phase 0 = preflight through Phase 6.5)
- **Artifact** — file under `.sealos/` in the target project
- **Deployment source** — Compose, Helm, Kubernetes, implicit, or official template
- **Plugin** — host package that installs skills from root `skills/**`
- **Runtime truth** — Phase 6.5 post-deploy verification

## Page types

| Directory | Type | Sentence limit | Voice |
| --- | --- | --- | --- |
| `get-started/` | Procedural | 20 words | Imperative ("Install the plugin.") |
| `skills/` | Descriptive + spec | 25 words | Simple present |
| `pipeline/` | Descriptive + spec | 25 words | Simple present |
| `specs/` | Normative | 25 words | "Must" for requirements |
| `contributing/` | Procedural | 20 words | Imperative |

## Skill page required sections

Every page under `skills/` must include: Purpose, When to use, Prerequisites, Workflow summary, Artifacts, Example prompts, Safety rules, Implementation status.

## Style

- Second person ("you"), active voice
- Sentence case for headings
- No emoji, no marketing language
- Code blocks must have language tags
- Images require descriptive alt text
- Internal links: root-relative, no file extensions (`/pipeline/phases` not `/pipeline/phases.mdx`)

## Content boundaries

**Document here:**
- User-facing usage and install instructions
- Pipeline phase contracts (inputs, outputs, stop conditions)
- Template format, conversion rules, artifact schemas
- Safety rules and platform support claims

**Do not document here (keep in sealos-skills):**
- Agent execution scripts (`scripts/*.mjs` internals)
- Full conversion rule registries (`rules-registry.yaml`)
- Eval fixture JSON
- Plugin validation script internals

**Index, do not copy:** Large reference files (`sealos-specs.md`, `conversion-mappings.md`) — summarize key constraints and link to the implementation file.

## When editing

1. Read `docs.json` to understand navigation placement
2. Read 2–3 similar pages to match voice
3. Search for existing content before creating new pages
4. Add new pages to `docs.json` navigation
5. Run `mint validate` before committing
