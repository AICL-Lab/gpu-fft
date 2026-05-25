# Contributing to WebGPU FFT Library

This repository is in a **low-maintenance cleanup phase**. Favor focused fixes, deletions, and consistency work over feature expansion.

## Getting Started

```bash
git clone https://github.com/YOUR_USERNAME/gpu-fft.git
cd gpu-fft
npm install
```

## Development Workflow

1. Keep the change small and single-purpose.
2. Update tests for behavior changes and bug fixes.
3. Update `README.md`, `docs/`, and root `CHANGELOG.md` when public behavior or user-facing wording changes.
4. Do not add repo-local AI workflow frameworks, skill packs, or extra governance layers.

## Code and Documentation Rules

- Use TypeScript with strict typing; avoid `any`.
- Keep files focused and reuse existing helpers before adding new ones.
- Keep WGSL source in `src/shaders/sources.ts`; do not reintroduce standalone shader copies.
- `createSpectrumAnalyzer()` and `createImageFilter()` are CPU-only utilities.
- The only project changelog is the root `CHANGELOG.md`.

## Validation

Run the canonical validation chain before submitting:

```bash
npm run lint
npm run format:check
npm run typecheck
npm test
```

Run these when relevant:

```bash
npm run build
npm run smoke:package
npm run docs:build
```

## Commit Messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```text
type(scope): description
```

Examples:

```text
refactor(docs): remove duplicated changelog page
fix(filter): keep image filter CPU-only
docs(readme): align contribution workflow
```

## Pull Requests

- Explain the change and why it exists.
- Call out public API, docs, workflow, or packaging impact.
- Ensure CI passes.

## Code of Conduct

This project follows the [Code of Conduct](CODE_OF_CONDUCT.md).
