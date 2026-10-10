# AGENTS.md

Instructions for AI coding agents working in or with `@three-ws/assets`.

## What this is

Find a ready-made 3D prop, rigged character, or motion clip on three.ws and add it to your project with the code that renders it. Free and public: no account, no API key, no payment.

## Use it

```bash
npm install @three-ws/assets
```

Full API reference: [README.md](README.md). Machine-readable summary: [llms.txt](llms.txt). Full text: [llms-full.txt](llms-full.txt).

## Work on it

- Node 20 or newer, ESM only.
- Run the tests with `npm test` before proposing a change.
- Keep runtime dependencies at their current count. Prefer a well-maintained library over new hand-rolled code, and say why in the pull request.
- No mocks, placeholders or TODO comments in committed code.
- Do not use em-dashes or en-dashes in code, comments or docs.

## Source of truth

This repository is exported from https://github.com/nirholas/three.ws/tree/main/packages/assets-cli. Bug reports belong here; larger changes should be proposed against the monorepo path.
