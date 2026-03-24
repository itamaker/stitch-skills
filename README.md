# stitch-skills

Standalone agent skill for Google Stitch workflows.

This repository is structured for the open `skills` installer ecosystem and contains a single skill: `stitch`.

## Install

```bash
# List skills in this repository
npx skills add itamaker/stitch-skills --list

# Install the skill
npx skills add itamaker/stitch-skills --skill stitch
```

## Repository Layout

```text
skills/
  stitch/
    SKILL.md
    agents/
    assets/
    references/
    scripts/
```

## Usage Examples

- `Use $stitch to list my Stitch projects.`
- `Use $stitch to create a Stitch project and generate a login screen.`
- `Use $stitch to download the HTML for a Stitch screen into ./tmp/screen.html.`
- `Use $stitch to save my Stitch auth and defaults into ./.stitch.json.`
- `Use $stitch to write committed @google/stitch-sdk code for this app.`

## License

[MIT](./LICENSE)
