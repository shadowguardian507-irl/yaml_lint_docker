# yaml lint docker
Docker containers for linting yaml files

This is simply a minimal linux docker container with yamllint installed

## Versions

- `centos10` - current CentOS Stream 10 image.
- `centos8` - deprecated CentOS 8 image retained for legacy builds.

## Publishing

Images are built and pushed by GitHub Actions from the `master` branch. See
`.github/WORKFLOW_SECURITY.md` for the required Docker Hub secrets and workflow
hardening notes.

The workflow derives Docker Hub tags from the CentOS base image tag in the
Dockerfile. For the current `quay.io/centos/centos:stream10` base, it publishes:

- `centos-stream10-<epoch>` manifest for `amd64` and `arm64`
- `centos-stream10-latest` manifest for `amd64` and `arm64`
- `centos-stream10-<epoch>-amd64`
- `centos-stream10-<epoch>-arm64`
- `centos-stream10-latest-amd64`
- `centos-stream10-latest-arm64`
