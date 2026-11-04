# Lesson 01 specification

## STUDIO-001 · Launch a tested calculator on an existing server

**Status:** Successfully deployed the supplied calculator to my DigitalOcean server. HTTPS, image verification, API tests, and preservation checks passed.
**Next step:** Finalize SPEC.md and LEARNING.md, review deployment evidence, complete the GitHub pull request and CI, then merge to main.
**Instructor implementation:** [issue #9](https://github.com/kaw393939/373_hosting/issues/9).
Create your own issue from the [lesson template](.github/ISSUE_TEMPLATE/studio-calculator.md).

## Agreed result

Launch the supplied published calculator image through your existing Traefik
network and a nonconflicting HTTPS hostname. Preserve unrelated services and
host access. Do not add another proxy/updater or build a substitute image.
The [release selection](studio/calculator-release.json) supplies the expected
commit and multi-platform digest independently of the running website.
An explicitly agreed adoption of a matching existing deployment is recorded
as adoption, not a fresh launch. This bounded lesson does not certify the whole
server baseline or a vulnerability-free image.

- **Public hostname:** `amman-calc.134-209-120-185.sslip.io` (learner agreed).
- **New launch or adopted deployment, and reason:** Successfully completed a new calculator deployment. The prepared launch returned `status: passed`, `provenance: launched`, and `new_launch: true`. Public HTTPS and API checks passed. All four existing containers passed preservation checks.

- **Own issue / feature branch:** [GitHub Issue #1](https://github.com/Singh01113/my-server-studio/issues/1) has been created. Feature branch: `codex/studio-001-calculator`. Pull request, CI, and merge are still pending.
- **Agreed scope or actual access/configuration gap:** Use the supplied pinned image, existing `hosting-web` network and existing Traefik HTTPS. Preserve existing websites, containers and server configuration; do not remove, replace or restart existing services. Doctor confirmed Docker/Compose access without sudo. Laptop Docker Desktop is unavailable, so full E2E remains pending in the eventual PR's CI.

Release sources: the [pinned selection](studio/calculator-release.json) identifies
commit `4600202bad42da0c5ffb11d83ce8364671293d3d`, its
[calculator source](https://github.com/kaw393939/is373_ci_cd/tree/4600202bad42da0c5ffb11d83ce8364671293d3d)
and [publication run](https://github.com/kaw393939/is373_ci_cd/actions/runs/36904255716).
Those supplied links are release references, not evidence that this server has
launched the image or that this learner's CI passed.

Private SSH targets and configuration stay in ignored local state. Share only
reviewed, selected evidence; never commit credentials or raw server output.
## Completed deployment · verified launch

The prepared `python3 studio.py plan` returned `mutates: false`. The following deployment plan was reviewed before the successful `python3 studio.py launch`:

- Send the scoped runtime helper and bundle to the agreed server under the deploy user's `~/.is373-studio/calculator` directory.
- Pull `docker.io/kaw393939/is373_ci_cd@sha256:aec414c990a5de6ed74c9e8dcb105b78f6358c03a8cea70a9d40dcda51c3a8fa` and start one `calculator` service in project `is373-studio-calculator`.
- Join the existing external `hosting-web` network. New calculator labels would route only the agreed hostname through Traefik's existing `websecure` entry point to container port `8000`, without publishing a new host port. Traefik would discover the route dynamically and use its existing resolver to obtain/store a certificate for the new hostname as needed.
- Store deployment files and the runtime report under the scoped deployment directory; existing services would not be removed, replaced or restarted, and existing Traefik configuration files would not be edited. Capture selected existing container identities, start times and restart counts immediately before/after launch to check preservation.
- Verify the deployed release and public HTTPS/API results. Preserve the initial successful sanitized new-launch report before repeat verification.

The deployment was completed successfully using `python3 studio.py launch`. The launch returned `status: passed`, `provenance: launched`, and `new_launch: true`.

The pinned Docker image and expected commit matched. Public HTTPS and API checks passed. All four existing containers passed preservation checks.

Sanitized runtime evidence was exported to [studio/evidence.json](studio/evidence.json). The two full browser E2E tests remain pending in GitHub CI.

## Evidence to keep


| Evidence | Actual result / link |
|---|---|
| Prepared tests | `python3 studio.py check --fast` passed Black, Pylint, and 91 pytest tests. Two browser E2E tests were deselected because local Docker was unavailable. Full E2E remains pending in GitHub CI. |
| Deployment and HTTPS | [Live calculator](https://amman-calc.134-209-120-185.sslip.io) deployed successfully. [studio/evidence.json](studio/evidence.json) confirms `status: passed`, `new_launch: true`, matching image and commit, and trusted public HTTPS. |
| API verification | The deployed calculator returned HTTP 200 with result 42 for 6 × 7. Division by zero returned HTTP 400, and invalid numeric input returned HTTP 422. |
| Existing services preserved | Four existing containers passed preservation checks. Evidence reports `checked_count: 4` and `unchanged: true` for container identity, state, and published ports. |
| My browser observation | I tested 9 × 4 on my own calculator. The Browser Result and API Result both displayed 36, and the page showed "Results match." |
| Learning summary | [LEARNING.md](LEARNING.md) includes the classroom observation and request-path prediction. My deployed-browser observation, check interpretation, and keep/revise decision still need final review and documentation. |
| GitHub issue | [STUDIO-001 Issue #1](https://github.com/Singh01113/my-server-studio/issues/1) was created successfully. |
| Pull request and CI | Pending. The feature branch still needs to be committed, pushed, tested in GitHub CI, and merged into main. |
| Accuracy review | Pending final review of SPEC.md, LEARNING.md, and sanitized evidence before publishing. |

Link the exported `studio/evidence.json`, actual CI and issue/PR when available.
CI does not deploy this server. A fixture, green check, timestamp, closed issue
or AI assertion alone does not establish the full result. `status` reports
recorded evidence and readiness for instructor review; it does not grade,
certify authorship or establish understanding.

## Optional instructor history

The records below are background, not steps to repeat. Their original anchors
remain here so earlier links continue to work.

## HOST-001 · Keep the Traefik dashboard private

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-001--keep-the-traefik-dashboard-private).

## HOST-002 · Controlled host maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-002--controlled-host-maintenance).

## HOST-003 · Companion image security maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-003--companion-image-security-maintenance).
