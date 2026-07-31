# Sealos Skills documentation

Documentation site for [Sealos Skills](https://github.com/labring/sealos-skills) — the plugin-first skill pack for deploying projects to Sealos Cloud from AI agents.

This repository is the **single source of truth** for skill behavior, pipeline contracts, and user-facing specifications. The [`sealos-skills`](https://github.com/labring/sealos-skills) repository implements what this site defines.

## Site structure

| Tab | Sections |
| --- | --- |
| **Documentation** | Get started, Concepts, Skills, Deploy pipeline |
| **Specifications** | Contracts, Contributing |

## Local development

Install the [Mintlify CLI](https://www.npmjs.com/package/mint):

```bash
npm i -g mint
```

Run the dev server from the repository root (where `docs.json` lives):

```bash
mint dev
```

Open `http://localhost:3000`.

Validate before committing:

```bash
mint validate
mint broken-links
```

## Publishing

Changes deploy automatically when pushed to the default branch, via the Mintlify GitHub App connected to this repository.

## AI-assisted editing

```bash
npx skills add https://mintlify.com/docs
```

See `AGENTS.md` for project-specific agent instructions and SSOT workflow rules.

## Repository relationship

```
sealos-skills-doc (this repo)     sealos-skills (implementation)
├── skills/*.mdx          ──defines──▶  skills/*/SKILL.md
├── pipeline/*.mdx        ──defines──▶  skills/sealos-deploy/modules/
├── specs/*.mdx           ──defines──▶  schemas/, references/
└── get-started/install   ──defines──▶  distribution/platforms.json
```

## License

MIT
