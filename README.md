# aur-workflow

Template repository holding the CI/CD workflows shared by all `aur.*` AUR
package repos: `.github/workflows/*.yaml`, `.github/dependabot.yaml`,
`.gitignore`, and `LICENSE`. It also hosts two live example packages —
`release/` and `git/` — that exercise the pipeline end to end, built from
[`its-me/dummy.releases`](https://github.com/its-me/dummy.releases).

## Using this template

1. Create a new repo from this template, named `aur.<pkgname>`.
2. Base its `ci.yaml`/`publish.yaml` on `ci-release.yaml`/
   `publish-release.yaml` (drop the `path` input and path filters — those
   only exist here because this repo hosts two packages in
   subdirectories). Replace `package` in `publish.yaml`'s
   `environment.url` and `package-name` input with the actual AUR package
   name.
3. Add the package's `PKGBUILD` and `.SRCINFO` at the repo root, plus a
   package-specific `README.md`.
4. Set the `AUR_SSH_KEY` repository secret (Settings → Secrets and
   variables → Actions) — this is not shared automatically across repos
   and must be set individually for every new package repo.

## Workflows

- `ci-release.yaml` / `ci-git.yaml` — run `its-me/action.aur.ci` on
  push/PR, scoped to `release/**` or `git/**` respectively.
- `publish-release.yaml` / `publish-git.yaml` — manually dispatched; run
  `its-me/action.aur.publish` to push `release/` or `git/` to the AUR as
  `package` / `package-git`.
- `update-release.yaml` / `update-git.yaml` — daily (00:30 UTC) and
  manually dispatched; run `its-me/action.aur.update` to check
  `dummy.releases` for a new release/commit, bump the PKGBUILD, and — if
  it changed — automatically publish the update to the AUR.
  `update-git.yaml` additionally runs an `its-me/action.aur.ci` job
  between the update and publish jobs, so a bad bump is caught before
  it's published.
- `zizmor.yaml` — security scanning for the workflows themselves.
- `dependabot.yaml` — keeps `github-actions` pins up to date, with a 7-day
  cooldown and minor/patch bumps ignored (actions are pinned to bare major
  tags, which already float forward).

## License

[MIT](LICENSE)
