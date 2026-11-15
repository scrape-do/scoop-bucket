<!-- SPDX-License-Identifier: Apache-2.0 -->
# Scrape.do Scoop bucket

[![ci](https://github.com/scrape-do/scoop-bucket/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/scrape-do/scoop-bucket/actions/workflows/ci.yml) [![license](https://img.shields.io/github/license/scrape-do/scoop-bucket)](LICENSE)

The official [Scoop](https://scoop.sh) bucket for the Scrape.do command-line tools on Windows (x64 and arm64).

| App | What it installs |
| --- | ---------------- |
| `sdo` | The `sdo` command-line client for the [Scrape.do](https://scrape.do) API, with a bundled MCP server (`sdo mcp serve`). Source: [scrape-do/sdo-cli](https://github.com/scrape-do/sdo-cli). |
| `sdo-mcp` | `sdo-mcp`, the standalone Model Context Protocol server for the Scrape.do API. Source: [scrape-do/sdo-mcp](https://github.com/scrape-do/sdo-mcp). |

## Install

```powershell
scoop bucket add scrape-do https://github.com/scrape-do/scoop-bucket
scoop install scrape-do/sdo
scoop install scrape-do/sdo-mcp
```

## Update

```powershell
scoop update
scoop update sdo
scoop update sdo-mcp
```

## Uninstall

```powershell
scoop uninstall sdo sdo-mcp
scoop bucket rm scrape-do
```

## How the manifests are updated

The manifests install the prebuilt release archives published on GitHub. They are not edited by hand: when a new
version is released, the release workflow of
[sdo-cli](https://github.com/scrape-do/sdo-cli/blob/main/.github/workflows/release.yml) or
[sdo-mcp](https://github.com/scrape-do/sdo-mcp/blob/main/.github/workflows/release.yml) generates the manifest from
that release's `checksums.txt` and commits it here after the GitHub Release exists. Release candidates are not
published to this bucket.

Because the release pipeline writes these files (the commits are by `scrape-do-publisher[bot]` and titled
`sdo X.Y.Z` or `sdo-mcp X.Y.Z`), a hand edit here is overwritten by the next release. A change to a manifest belongs
in its template in `tools/pkgmanifests/main.go` of [sdo-cli](https://github.com/scrape-do/sdo-cli/tree/main/tools/pkgmanifests)
or [sdo-mcp](https://github.com/scrape-do/sdo-mcp/tree/main/tools/pkgmanifests).

## Verifying a download

Every `hash` in a manifest is the SHA-256 listed in that release's `checksums.txt`, which is signed with cosign
(keyless, recorded in the Rekor transparency log) by the release workflow, so Scoop refuses an archive that differs
from the signed release. To verify the release files yourself, download `checksums.txt`,
`checksums.txt.cosign.bundle` and the archive from the GitHub Release and follow the steps in the
[Supply-Chain Integrity](https://github.com/scrape-do/sdo-cli/blob/main/SECURITY.md#supply-chain-integrity) section
of sdo-cli's SECURITY.md, or the [same section](https://github.com/scrape-do/sdo-mcp/blob/main/SECURITY.md#supply-chain-integrity)
of sdo-mcp's.

## Documentation, support and security

- API documentation: https://scrape.do/documentation
- Install, update or hash problems with a manifest: [GitHub Issues](https://github.com/scrape-do/scoop-bucket/issues)
  of this repository. Bugs and feature requests for the tools themselves:
  [sdo-cli issues](https://github.com/scrape-do/sdo-cli/issues) or [sdo-mcp issues](https://github.com/scrape-do/sdo-mcp/issues).
  Account, billing and API questions: support@scrape.do.
- Security issues: report them privately as described in [sdo-cli's SECURITY.md](https://github.com/scrape-do/sdo-cli/blob/main/SECURITY.md)
  or [sdo-mcp's SECURITY.md](https://github.com/scrape-do/sdo-mcp/blob/main/SECURITY.md), not in a public issue. Never
  post an API token in an issue.
- [Apache-2.0](LICENSE)
