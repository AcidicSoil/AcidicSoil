# Representative release-surface verification

Date checked: 2026-08-29

This is the evidence pass for the README/release-presentation experiment in issue #2. It checks whether the three representative repositories currently have a canonical public distribution surface that is safe to present as a published package or release.

## Results

| Repository | Candidate surface | Result | Decision |
| --- | --- | --- | --- |
| `DSPyTeach` | PyPI project `dspyteach` | No verified `dspyteach` project page was found in the public PyPI search pass. Search results resolve to the unrelated `dspy` project instead. | Do not add a PyPI/version badge or profile `Published packages` row. Keep repository/development installation documentation authoritative. |
| `relayforge` | PyPI project `relayforge` | No verified `relayforge` distribution was found. PyPI exposes a user named `relayforge` whose published project is `carapace-sdk`; that is not evidence for this repository's package. | Do not add a PyPI/version badge or profile row. |
| `gh-repo-manager` | GitHub Releases | GitHub's repository releases API returned an empty release collection. | Do not add a latest-release badge or profile row. |

## Evidence standard

A repository manifest, console-script entry point, package name, tag, build artifact, local install path, similarly named registry account, or similarly named third-party package is not publication evidence. A row becomes eligible only when the exact project has a public canonical distribution URL that resolves to its real published artifact/release.

For GitHub Releases, the repository's own releases collection is authoritative. For PyPI, the exact project distribution page must exist and identify the intended package; search hits for similarly named projects or user profiles are explicitly rejected.

## Experiment consequence

The release-evidence gate is working as intended: **none of the three representative repositories is currently eligible for the proposed live `Published packages` index.** The profile README should therefore remain unchanged rather than displaying speculative versions or install commands.

This result does not reject the proposed visual convention. It separates two decisions:

1. the left-aligned package/release presentation can continue through visual review; and
2. live package rows and release/version badges remain gated on actual publication evidence.

## Remaining acceptance work

The experiment still needs visual review of the proposed header/badge layout in GitHub dark/light appearance and narrow/mobile wrapping before the convention is accepted for representative-repository rollout. No package repository should be changed merely to satisfy this evidence pass.