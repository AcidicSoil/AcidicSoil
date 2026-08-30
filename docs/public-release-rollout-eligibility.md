# Public release rollout eligibility

Status: current evidence register for issue #7.

This register records whether a repository has enough public-distribution evidence to receive the accepted release-facing README treatment. It is deliberately conservative: a manifest, tag, local build, similarly named package, or registry user is not publication evidence.

## Verified rollout

| Repository | Canonical public distribution | Result |
| --- | --- | --- |
| `AcidicSoil/DSPyTeach` | PyPI `dspyteach` | Eligible and rolled out. The profile package row and DSPyTeach README now use the canonical PyPI release surface; TestPyPI and retired `AcidicSoil/dspy-file` links are not primary release identity. |

## Checked but not eligible

| Repository | Evidence checked | Result |
| --- | --- | --- |
| `AcidicSoil/gh-repo-manager` | GitHub Releases collection | No releases currently published; do not add a release badge or profile package row. |
| `AcidicSoil/exprgen` | GitHub Releases collection | No releases currently published; do not infer publication from repository metadata. |
| `AcidicSoil/skill-scout` | GitHub Releases collection | No releases currently published; keep it in normal repository presentation. |
| `AcidicSoil/chatgpt_codex_remote_plugins_cache` | GitHub Releases collection | No releases currently published; cache/repository existence is not a public distribution. |
| `AcidicSoil/relayforge` | PyPI search/user surface | No exact `relayforge` distribution was verified. A PyPI user named `relayforge` publishes `carapace-sdk`, whose verified source is a different repository (`relayforge-ai/carapace-protocol`); that is not evidence for `AcidicSoil/relayforge`. |

## Decision rule

A repository moves from **not eligible** to **eligible** only when its exact canonical public distribution URL is verified. At that point:

1. verify the public install/release identity;
2. apply the compact left-aligned README hierarchy from `public-release-readme-standard.md`;
3. verify badge targets and install commands;
4. allow normal badge wrapping rather than forcing one-line mobile layout;
5. add a profile `Published packages` row only when the artifact is actually installable/public.

This register is evidence, not a release backlog. Repositories do not need to publish artifacts merely to qualify for profile presentation.