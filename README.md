# <p style="text-align: center">backup-full</p>

<p align="center">
  <a href="https://github.com/RogueOneEcho/backup-full/actions/workflows/ci-on-push.yml"><img alt="CI status" src="https://img.shields.io/github/actions/workflow/status/RogueOneEcho/backup-full/ci-on-push.yml"></a>
  <a href="https://github.com/RogueOneEcho/backup-full/releases"><img alt="Latest release" src="https://img.shields.io/github/v/release/RogueOneEcho/backup-full"></a>
  <a href="LICENSE.md"><img alt="License" src="https://img.shields.io/github/license/RogueOneEcho/backup-full"></a>
</p>

Snapshot chosen paths to Backblaze B2 using restic; all of `/srv` except `/srv/shared` by default.

```bash
docker pull ghcr.io/rogueoneecho/backup-full
```

## Features

- Optional `/app/include`: one absolute path per line; IF not mounted or empty, defaults to `/srv/`; each path MUST exist and NOT be empty
- Optional `/app/exclude`: one absolute pattern per line; IF not mounted, defaults to `/srv/shared`
- Relative lines are rejected, since restic matches relative patterns at any depth
- Empty lists, or a directory from an empty compose config, are treated as empty
- Uploads to Backblaze B2 via restic with encryption and deduplication
- Automatic retention policy: everything within 14 days, 4 weekly, 12 monthly
- Verifies backup integrity after each run
- Logs progress every 10 seconds; override with `RESTIC_PROGRESS_FPS` (updates per second)

## Build

- amd64 and arm64 images available on [GHCR](https://github.com/RogueOneEcho/backup-full/pkgs/container/backup-full)
- Signed with [Cosign](https://github.com/sigstore/cosign) via keyless Sigstore OIDC
- SBOM attestation in CycloneDX format
- Vulnerability scanned with [Grype](https://github.com/anchore/grype)

## Usage

See [docker-compose.yml](docker-compose.yml) for an example.

## Releases and Changes

Releases and a full changelog are available via [GitHub Releases](https://github.com/RogueOneEcho/backup-full/releases).
