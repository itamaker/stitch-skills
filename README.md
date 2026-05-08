# stitch-skills

Standalone agent skill for Google Stitch workflows. Wraps the official [`@google/stitch-sdk`](https://github.com/google-labs-code/stitch-sdk) (v0.1.1) so an agent can drive Stitch projects, screens, variants, and design systems through a single CLI runner — or write committed TypeScript against the SDK when an integration calls for it.

## Install

Standalone (default `skills` CLI):

```bash
npx skills add itamaker/stitch-skills
```

Or via the [`itamaker/skills`](https://github.com/itamaker/skills) Claude Code plugin marketplace:

```text
/plugin marketplace add itamaker/skills
/plugin install stitch-skills@itamaker-skills
```

## What the skill covers

- **Projects & screens** — `list-projects`, `create-project`, `list-screens`, `get-screen`, `generate`, `edit`, `download-html`, `download-image`.
- **Variants** — `variants` with `--variant-count`, `--creative-range`, `--aspects`.
- **Design systems** *(new in v0.2.0)* — `list-design-systems`, `create-design-system`, `update-design-system`, `apply-design-system`. Each design-system command accepts JSON via `--*-file <path>` or `--*-json '{...}'`.
- **Auth** — `STITCH_API_KEY` for direct keys, or `STITCH_ACCESS_TOKEN` + `GOOGLE_CLOUD_PROJECT` for OAuth. `STITCH_HOST` overrides the MCP endpoint.
- **Config** — resolves from `--config`, `STITCH_SKILL_CONFIG`, `.stitch.json`, or `stitch.json`. `save-config` / `--save-config` persists resolved values.
- **Low-level tools** — `list-tools` and `call-tool` expose the underlying Stitch MCP tools (`create_project`, `generate_screen_from_text`, `edit_screens`, `generate_variants`, design-system tools, etc.).
- **Agent integrations** *(documented in `references/mcp-sdk.md`)* — `stitchTools` from `@google/stitch-sdk/ai` (Vercel AI SDK), `stitchAdkTools` from `@google/stitch-sdk/adk` (Google ADK), and `StitchProxy` for hosting an MCP proxy.

## Usage examples

- `Use $stitch to list my Stitch projects.`
- `Use $stitch to create a Stitch project and generate a login screen.`
- `Use $stitch to generate three variants for screen abc and download HTML for the best one.`
- `Use $stitch to extract a design system from our brand and apply it across the existing screens.`
- `Use $stitch to wire Stitch into a Google ADK TypeScript agent.`
- `Use $stitch to download the HTML for a Stitch screen into ./tmp/screen.html.`
- `Use $stitch to save my Stitch auth and defaults into ./.stitch.json.`
- `Use $stitch to write committed @google/stitch-sdk code for this app.`

## Repository Layout

```text
skills/
  stitch/
    SKILL.md              # entry point read by the agent
    agents/               # plugin-style agent metadata
    assets/               # example .stitch.json
    references/           # config schema, SDK surface, prompting, DESIGN.md
    scripts/
      run.sh              # stable wrapper; invokes stitch.mjs
      stitch.mjs          # SDK-backed runner
```

## Versioning

- v0.2.0 — `@google/stitch-sdk@0.1.1` alignment + design-system commands.
- v0.1.0 — initial standalone release.

See [Releases](https://github.com/itamaker/stitch-skills/releases) for full notes.

## License

[MIT](./LICENSE)
