# README/release presentation visual QA

Date checked: 2026-08-29

This is the final visual-review pass for issue #2. It evaluates the proposed left-aligned package header and bounded `flat-square` badge row before the convention is accepted for representative-repository rollout.

## Method

Representative five-badge and six-badge package headers were rendered in headless Chromium at two viewport sizes and both GitHub-style light and dark palettes:

- desktop: 1280 × 900;
- narrow/mobile: 390 × 844;
- light canvas/text/code surfaces matching GitHub's light presentation;
- dark canvas/text/code surfaces matching GitHub's dark presentation.

The first fixture used five consumer-facing badges — canonical version, build, downloads, runtime, and license — to exercise the preferred density. A second worst-case fixture added a sixth security badge to exercise the documented hard cap. The release/version badge remains representative only; issue #2's release-surface evidence pass found no verified public distribution for the three candidate repositories, so no fake live registry/release badge or link was introduced.

## Results

| Surface | Result | Evidence |
| --- | --- | --- |
| Light, desktop | PASS | Five- and six-badge variants remain on one row; package purpose, install command, and quick start retain the intended vertical scan. No horizontal overflow. |
| Dark, desktop | PASS | Header, body text, code blocks, and five-/six-badge rows remain visually distinct and legible. No horizontal overflow. |
| Light, 390px | PASS | Both density variants wrap naturally to a second line; content width remains 390px with no horizontal overflow. Install and quick-start blocks remain fully visible. |
| Dark, 390px | PASS | Same wrapping behavior as light mode for both density variants; body text and code surfaces remain legible and no horizontal overflow occurs. |

Measured browser geometry for both themes:

- desktop: `scrollWidth = clientWidth = 1280`;
- mobile: `scrollWidth = clientWidth = 390`;
- desktop badge row: all five badges share one row; the six-badge hard-cap fixture also remains on one row;
- mobile five-badge row: four badges remain on the first row and the fifth wraps to a second row without clipping;
- mobile six-badge row: four badges remain on the first row and badges five and six wrap together to the second row without clipping.

## Review decision

**Accept the left-aligned package-header convention.** The layout remains readable at the tested desktop and narrow widths, and bounded badge rows degrade by wrapping rather than creating horizontal scrolling.

The visual acceptance does **not** waive the publication-evidence gate. A repository may adopt the structural hierarchy before it has a public release, but it must not render a canonical release/version badge, claim a canonical install command, or enter the profile `Published packages` index until the exact public distribution surface has been verified.

## Guardrails carried into the standard

- Keep the primary badge row to 3–5 badges normally and 6 maximum.
- Keep the header left aligned.
- Keep `Install` and `Quick start` immediately after the package summary/badges.
- Treat mobile wrapping as expected; never force a no-wrap badge container.
- Badge labels and values must remain readable in both GitHub themes; avoid low-contrast custom badge colors.
- Give badge images useful alt text and link release/version badges to the canonical distribution page.
- Do not hard-code release versions when the canonical registry/release service can provide them.
- Do not populate the profile package index with repository-only or unpublished artifacts.

## Boundary

This QA accepts the presentation contract, not a repo-wide migration. The three experiment repositories remain unchanged until a separate rollout task selects eligible public-release repositories and verifies each target's actual distribution evidence.