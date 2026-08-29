# Public package README and release presentation experiment

Status: accepted presentation experiment. The layout passed visual QA; live release/version badges and profile package rows remain gated on verified public distribution evidence.

## Finding

The current public repositories provide good representatives for package *shapes*, but the profile should not yet label them as published packages without registry/release evidence. In particular, repository manifests establish package names and versions, while that alone does not prove a public registry release exists. The profile therefore should not add a `Published packages` table until each row has a canonical public distribution URL that can supply its version dynamically.

This keeps the proposed profile index truthful and prevents a manifest version from being presented as a published release.

## Representative repositories

| Repository | Ecosystem shape | Current repository authority | Candidate canonical release surface |
| --- | --- | --- | --- |
| `DSPyTeach` | Python CLI/package | `pyproject.toml`: `dspyteach`, version `0.2.1`, Python 3.10–3.11 | PyPI/TestPyPI only after a public package URL is verified |
| `relayforge` | Python CLI/package | `pyproject.toml`: `relayforge`, version `0.2.0`, Python >=3.11 | PyPI only after a public package URL is verified |
| `gh-repo-manager` | Go binary + GitHub CLI extension | `go.mod`: Go 1.25; README documents local extension install and local multi-platform packaging | GitHub Releases only after an actual release exists |

These three examples cover two packaging ecosystems and three consumer-install shapes without inventing release state.

## Proposed package header contract

Use a compact, left-aligned header by default. It scans better with the install and quick-start sections and avoids a decorative centered block competing with technical content.

```md
# package-name

One sentence explaining the package to a prospective user.

[canonical release/version] [build] [downloads when meaningful] [runtime] [license]

## Install

<canonical install command>

## Quick start

<smallest useful command or example>
```

Primary badge row rules:

- 3–5 badges normally; 6 maximum.
- `flat-square` presentation.
- Leftmost badge is the canonical installable artifact/version and links to its distribution page.
- Prefer release-facing signals over implementation badges.
- Do not duplicate secondary install channels in the badge row; put them under `Install`.
- Never hard-code a version into a badge when the registry/release service can provide it.

## Mockup A — Python CLI (`DSPyTeach`)

```md
# DSPyTeach

Analyze files and prompt libraries into teaching, refactor, and agent-handoff outputs.

[PyPI version] [build] [Python versions] [license]

## Install

uv tool install dspyteach

## Quick start

dspyteach --help
```

Release gate: do not render the PyPI badge or use the install command above as canonical until the public `dspyteach` distribution URL is verified. The repository currently identifies the project/version and a TestPyPI publishing index; that is not sufficient evidence of a production PyPI release.

## Mockup B — Python CLI (`relayforge`)

```md
# RelayForge

Run declarative repository handoff and agent-workflow pipelines with explicit artifacts and provenance.

[PyPI version] [build] [Python >=3.11] [license]

## Install

uv tool install relayforge

## Quick start

relayforge --help
```

Release gate: same rule as DSPyTeach. The repository's `pyproject.toml` proves the package identity and console entry point, not publication to PyPI.

## Mockup C — Go / GitHub CLI extension (`gh-repo-manager`)

```md
# gh-repo-manager

Manage GitHub repositories from a Bubble Tea TUI, standalone or as `gh repo-manager`.

[latest GitHub release] [build] [platforms] [license]

## Install

<canonical gh extension or release install command>

## Quick start

gh repo-manager
```

Release gate: the repository already supports local extension installation and builds precompiled multi-platform artifacts, but release publishing is explicitly separate. Do not show a release badge until a GitHub Release exists.

## Proposed profile index

Once at least one distribution is verified, add this immediately after `selected public work`:

```md
## Published packages

### PyPI

| Package | Version | Description |
| --- | --- | --- |
| [package](canonical-registry-url) | [dynamic version badge] | one-line description |

### GitHub Releases / extensions

| Project | Release | Description |
| --- | --- | --- |
| [project](canonical-release-url) | [dynamic release badge] | one-line description |
```

Only verified installable public artifacts belong here. General repositories remain in `selected public work`.

## Review choice

Accepted convention: **left-aligned package headers**. Centered headers are useful for brand-heavy landing pages, but these repositories are developer tools where the package identity, install command, and first useful invocation should form one fast vertical scan.

## Verification checklist before rollout

- [ ] Every indexed package has a verified public registry/release URL.
- [ ] The leftmost badge derives version data from that canonical release surface.
- [ ] Badge links resolve to the canonical package/release page.
- [ ] Primary badge rows stay at six badges or fewer.
- [ ] Install commands match the verified distribution mechanism.
- [x] Dark/light GitHub-style rendering remains legible in the representative visual-QA fixture.
- [x] Badge rows wrap acceptably at the tested 390px narrow/mobile viewport without horizontal overflow.
- [ ] The profile index contains installable artifacts only, not general repositories.
- [ ] No version is duplicated as manually maintained profile data.
- [x] The presentation experiment is approved; repository-wide rollout remains a separate task.

## Rollout boundary

This experiment intentionally changes no package repository. Release-surface evidence and visual QA are now recorded in `docs/readme-release-surface-verification.md` and `docs/readme-release-visual-qa.md`; the accepted reusable contract is `docs/public-release-readme-standard.md`. A separate rollout task may apply the standard only to repositories whose actual public distribution surfaces are verified. The profile `Published packages` index remains absent until at least one artifact passes that evidence gate.