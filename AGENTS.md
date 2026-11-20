# AGENTS.md

Notes for coding agents working in this repository. [README.md](README.md) covers what
the images do and how to use them; [CONTRIBUTING.md](CONTRIBUTING.md) the development
setup.

## Versioning

SemVer with the pinned Salt release as build metadata: `vX.Y.Z+up<SALT_VERSION>`, e.g.
`v1.1.0+up3006.0`, published as images `X.Y.Z`, `X.Y`, `latest` and the Salt version
(`3006.0`, `3006`), per the
[versioning standard](https://github.com/mbologna/.github/blob/main/VERSIONING.md).

- Never create, move or delete tags, and never edit a version to cut a release:
  auto-release tags from the commit types (`feat` minor; `fix`, `perf`, `revert` patch;
  `!` or a `BREAKING CHANGE:` footer major) and adds the metadata from
  `ARG SALT_VERSION` in `Dockerfile-master`.
- `ARG SALT_VERSION` must be the same in both Dockerfiles (the Salt pin check fails
  otherwise). Renovate can't move it; bump both when Leap ships a new Salt. Commit a new
  Salt patch release as `chore(deps):`, a minor as `feat(deps):` and a major (3006 to
  3007, say) as `feat(deps)!:`, so the release bumps by the upstream's impact.
- Release notes live on the GitHub Releases page; `CHANGELOG.md` only points there.
