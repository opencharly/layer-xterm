# AGENTS.md — layer-xterm

Standalone candy repo for the `xterm` layer — the classic X terminal emulator
that triggers on-demand XWayland on labwc. The candy lives in `charly.yml` at the
repo root: the per-distro packages, the `check:` assertions, and the embedded
`skill:` entity projected into the marketplace corpus as `/charly-selkies:xterm`.

Canonical files:

- `charly.yml` — the `xterm:` candy entity and the `xterm-skill:` skill entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-selkies:xterm` — the owning skill. Why xterm is in `selkies-desktop`
  (the on-demand XWayland trigger) and the `wl:` verb integration. Load before
  editing or troubleshooting the layer.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, per-distro `distro:` arms, package/repo
  sections, service declarations). Load before editing any entity field or plan
  step.

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- The candy's `plan:` `check:` steps are the functional evidence — the binary at
  `/usr/bin/xterm` and the registered package.
- `xterm` ships the same package name on arch and fedora; keep both arms in sync.

## Modify this repo

- Edit the `xterm:` candy entity AND the `xterm-skill:` skill entity in
  `charly.yml` together. The skill is the projected usage source, so a behaviour
  change not mirrored in the skill leaves the corpus stale.
- New behaviour claims belong in the `plan:` as an observable `check:` step, and
  in the skill body.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge on
  PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the PR
  body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
