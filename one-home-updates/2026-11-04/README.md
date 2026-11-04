# Surf-and-Skate: One Home guest update

Asset readiness, loading recovery and crew/replay controls.

This archive contains the exact tested One Home guest source under `source/`, plus focused patches and hash preconditions. It is not an applied upgrade to this repository's older game, and it does not change its entry point, assets, deployment or workflow. The source files retain their original site-relative routes and asset references: restore them at their `site_path` in an isolated One Home copy to run them, rather than hosting the archive directory directly.

The focused three-way merge into upstream has 9 conflicts. The deployed guest baseline already contains earlier changes absent from upstream. This archive does not choose conflict resolutions or replace the upstream game.

## Application preconditions

Use a separate One Home site copy. Check every `before_sha256` in `manifest.json` at its exact `site_path` before applying anything. Reject mismatches and reconcile them explicitly. Apply only these patches with LF preserved, then check every `after_sha256`. The hashes describe the tested worker version, not this repository's root file.

After any inline script change, reconcile the corresponding existing CSP hash using the before/after script hashes in the manifest. Do not replace a shared site headers file. No headers file is included here.

Review the actual patch filenames first, then use `git -c core.autocrlf=false apply --check <patch>` in the isolated site copy. Apply only after all baseline hashes and checks pass. Repeat the relevant browser checks and coordinated site regression before publication.

## Evidence and limits

The producer tested desktop, portrait and landscape behavior. This delivery independently verified baseline/candidate hashes, script syntax and the changed-file allowlist. Physical phones and mobile Safari were not tested. A port to upstream still needs its own regression tests. No full private site, Passport code, credentials, operator records or personal logs are included.

Upstream base: `838d7d957ba8258b9e188f721763f3362912d1b2`. Recheck the remote head before any later push. Keep this archive on a review branch until its compatibility work and approvals are complete.
