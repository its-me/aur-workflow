# aur-workflow

Template repository holding the CI/CD workflows shared by all `aur.*` AUR
package repos: `.github/workflows/ci.yaml`, `publish.yaml`, `zizmor.yaml`,
`.github/dependabot.yaml`, `.gitignore`, and `LICENSE`.

## Using this template

1. Create a new repo from this template, named `aur.<pkgname>`.
2. In `.github/workflows/publish.yaml`, replace `CHANGEME` in the
   `environment.url` with the actual AUR package name.
3. Add the package's `PKGBUILD` and `.SRCINFO`, plus a package-specific
   `README.md`.
4. Set the `AUR_SSH_KEY` repository secret (Settings → Secrets and
   variables → Actions) — this is not shared automatically across repos
   and must be set individually for every new package repo.

## Workflows

- `ci.yaml` — runs `its-me/action.aur.ci` on every push/PR.
- `publish.yaml` — manually dispatched; runs `its-me/action.aur.publish` to
  push the package to the AUR.
- `zizmor.yaml` — security scanning for the workflows themselves.
- `dependabot.yaml` — keeps `github-actions` pins up to date, with a 7-day
  cooldown and minor/patch bumps ignored (actions are pinned to bare major
  tags, which already float forward).

## License

[MIT](LICENSE)
