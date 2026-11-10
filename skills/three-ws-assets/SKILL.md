---
name: three-ws-assets
description: Search the three.ws 3D catalog (CC0 props, rigged characters, motion clips) and download a GLB into a project with a paste-ready snippet. Use when a scene, site or app needs a 3D asset.
---

# three.ws 3D assets CLI

`@three-ws/assets` searches the free, public three.ws catalog and adds assets to the current project. No account, no API key, no payment. Needs Node 18+.

## Commands

Run with `npx @three-ws/assets <command>` (the binary is `three-ws-assets`).

```bash
npx @three-ws/assets search wooden chair --kind object
npx @three-ws/assets show object:painted_wooden_chair_01
npx @three-ws/assets add object:painted_wooden_chair_01
```

### search <terms>

Flags: `--kind object|character|animation`, `--category <c>`, `--tag <t>`, `--limit <1-50>` (default 12), `--offset <n>`, `--json`. Every word of the query must match a title, name, tag or category. Exits 1 when nothing matches.

### show <id>

Prints one item's facts and paste-ready source without downloading. `--framework agent-3d|model-viewer|three|react` selects one snippet, so `show <id> --framework three > model.js` writes a usable file. Ids look like `object:...`, `character:...`, `animation:...`.

### add <id>

Downloads the asset and prints a snippet pointing at the local copy. Flags: `--dir <path>` (default `public/three-ws/` when the project has `public/`, else `three-ws-assets/`), `--framework <f>`, `--thumb`, `--force`, `--json`. Re-runs are idempotent; a file you edited is never overwritten without `--force` (exit 1).

## Choosing a framework

- `model-viewer`: default for props.
- `agent-3d`: default for rigged characters.
- `three`: default for motion clips (`GLTFLoader`, `THREE.AnimationClip.parse`).
- `react`: the same wrapped as a component or hook.

## Licensing

Objects in the library are CC0. Characters and clips carry their own `license` field in `show`, `add` and `--json` output. Read it before shipping.

## Configuration

`THREE_WS_API` (default `https://three.ws`, or `--api <origin>`), `NO_COLOR`, `FORCE_COLOR`.

## Worked example

```bash
npx @three-ws/assets search wave --kind animation --limit 5 --json
npx @three-ws/assets add character:abe --dir src/models --framework agent-3d
```

Or call the endpoint directly: `GET https://three.ws/api/catalog?q=desk+lamp&kind=object`.

## From an MCP client

The plugin's `.mcp.json` registers the keyless studio server `https://three.ws/api/mcp-studio`, which exposes the same catalog as `search_catalog`, `get_catalog_item` and `get_item_source`.
