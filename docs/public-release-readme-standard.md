# Public release README standard

Status: accepted presentation standard for future eligible public-release repositories.

This standard captures the result of issue #2. It defines how an installable public artifact should present its release identity, install path, and first useful invocation without turning the README header into a badge wall.

## Package README hierarchy

Use a compact, left-aligned header:

```md
# package-name

One sentence explaining what the package does for a prospective user.

[canonical release/version] [build] [downloads when meaningful] [runtime/platform] [license]

## Install

<canonical install command>

## Quick start

<smallest useful command or example>
```

The package purpose, current published version, build health, and canonical install path should be visible without making the reader hunt through repository-internal detail.

## Badge contract

- Use `flat-square` presentation.
- Use 3–5 primary badges normally; 6 is the hard maximum.
- The leftmost badge identifies the canonical installable artifact/version.
- Link the release/version badge to the exact canonical registry or release page.
- Prefer release-facing signals: version, build, meaningful downloads, runtime/platform compatibility, and license.
- Add coverage or security only when it materially helps a package consumer.
- Do not fill the primary row with repo-internal tooling badges such as pnpm, uv, Cargo workspace, TypeScript, TUI, docs, stars, forks, or issue counts unless one is directly relevant to consuming the artifact.
- Do not force the badge row to remain on one line. Narrow layouts must be allowed to wrap without horizontal scrolling.
- Use useful badge alt text and avoid custom badge colors with poor light/dark readability.

## Publication evidence gate

A package name or version in a repository manifest is not evidence that the artifact is publicly published.

Before showing a canonical release/version badge, canonical public install command, or profile `Published packages` row, verify the exact public distribution surface:

- npm: exact npm package page;
- PyPI: exact PyPI project page;
- crates.io: exact crate page;
- GitHub Releases: the repository's actual releases collection/release page;
- GHCR/container registries: exact published image/package surface;
- extension marketplaces: exact published extension page.

Similarly named projects, user profiles, tags, local build artifacts, console entry points, manifests, or unpublished workflows do not satisfy this gate.

When the registry/release service can supply a version dynamically, do not duplicate that version as manually maintained README/profile text.

## Multiple install channels

Choose one canonical distribution surface for the primary badge row. Put alternative supported install methods under `## Install` instead of adding a badge for every channel.

## Profile README package index

The profile `Published packages` section is an index of **verified installable public artifacts**, not another repository list.

Add a row only after its canonical public distribution is verified. Group rows by actual release surface when useful, for example PyPI, npm, crates.io, or GitHub Releases/extensions. Each row should show only package/release identity, dynamically sourced current version/release, and a concise description.

If no public artifact passes the evidence gate, omit the section rather than publishing an empty or speculative package index. General repositories remain in the profile's normal public-work presentation.

## Visual requirements

The accepted layout was reviewed at 1280px desktop and 390px narrow/mobile widths in both GitHub-style light and dark presentation.

- Left-aligned headers are the default.
- Representative five-badge and six-badge-hard-cap rows must fit a normal desktop width on one row.
- On narrow/mobile widths, badges may wrap to additional lines but must not clip or create horizontal page scrolling.
- Package summary, `Install`, and `Quick start` remain a single vertical scan after wrapping.
- Text, code blocks, and badge labels/values must remain legible in both GitHub themes.

See `docs/readme-release-visual-qa.md` for the experiment evidence.

## Ecosystem adaptation

Keep the hierarchy stable while changing only the canonical release identity for the ecosystem:

| Distribution | Primary release identity | Typical supporting signals |
| --- | --- | --- |
| npm | npm version | build, downloads, Node version, license |
| PyPI | PyPI version | build, downloads, Python versions, license |
| crates.io | crate version | build, downloads, Rust/MSRV, license |
| GitHub Releases | latest release | build, release downloads, platforms, license |
| GHCR/container registry | image version | container build, pulls, runtime signal, license |
| extension marketplace | marketplace version | build, installs/downloads, compatibility, license |

## Rollout boundary

Adopting this document does not authorize speculative package metadata or a bulk README rewrite. Rollout should be a separate task that discovers eligible repositories, verifies their exact public distribution surfaces, applies the smallest README changes needed, and verifies every resulting badge/link/install command before integration.
