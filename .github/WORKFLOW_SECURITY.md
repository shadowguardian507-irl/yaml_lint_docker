# GitHub Actions publishing hardening

This repository publishes Docker Hub images from GitHub Actions instead of
Docker Hub automated builds.

## Required repository settings

- Add repository variable `DOCKERHUB_IMAGE`, for example
  `shadowguardian507/yaml_lint_docker`.
- Add environment secret `DOCKERHUB_USERNAME`.
- Add environment secret `DOCKERHUB_TOKEN` using a Docker Hub access token with
  write access only to the target repository where possible.
- Configure the `dockerhub-production` environment with required reviewer
  protection before enabling fully unattended pushes.
- Protect the `master` branch and require review for changes under
  `.github/workflows/`.

## Hardening choices

- The workflow does not run on pull requests.
- The workflow does not use `pull_request_target`.
- The workflow does not use `actions/cache` or Docker's GitHub Actions cache
  backend.
- Docker builds run with `--pull` and `--no-cache`.
- Docker Hub login happens only after the local image build and smoke test pass.
- `amd64` and `arm64` images are built on native GitHub-hosted runners instead
  of using QEMU/binfmt emulation.
- The only reusable action is `actions/checkout`, pinned to a full commit SHA.
- `GITHUB_TOKEN` is restricted to `contents: read`.
