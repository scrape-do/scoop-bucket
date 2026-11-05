# Scrape.do Scoop bucket

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
scoop update sdo sdo-mcp
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

## Verifying a download

Every `hash` in a manifest is the SHA-256 listed in that release's `checksums.txt`, which is signed with cosign
(keyless, recorded in the Rekor transparency log) by the release workflow, so Scoop refuses an archive that differs
from the signed release. To verify the release files yourself, download `checksums.txt`,
`checksums.txt.cosign.bundle` and the archive from the GitHub Release and follow the steps in the
"Supply-Chain Integrity" section of [sdo-cli's SECURITY.md](https://github.com/scrape-do/sdo-cli/blob/main/SECURITY.md)
or [sdo-mcp's SECURITY.md](https://github.com/scrape-do/sdo-mcp/blob/main/SECURITY.md).

## Reporting problems

Report bugs in `sdo` or `sdo-mcp` in their own repositories. Report security issues privately as described in their
SECURITY.md files, not in a public issue.

## License

[Apache-2.0](LICENSE).
