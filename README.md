# hut builds

This repository provides ready to use binaries of [hut](https://git.sr.ht/~xenrox/hut), the CLI tool for [sourcehut](https://sr.ht/).

## Available Releases

All releases are available in the [releases](https://github.com/anhkhoakz/hut-build/releases) section.

Supported platforms:

- Linux x86_64
- Linux arm64

The builds are generated from upstream sourcehut release tags.

## Installation

1. Go to the [releases](https://github.com/anhkhoakz/hut-build/releases) page.

2. Download the archive for your platform.

3. Extract the archive with:

   ```bash
   tar -xzf hut-<version>-<platform>.tar.gz
   ```

4. Move the binary to a directory in your `PATH`, e.g.:

   ```bash
   sudo mv hut-*/bin/hut /usr/local/bin/hut
   ```

5. Verify the installation:

   ```bash
   hut --version
   ```

## Download via CLI

Download the latest Linux x86_64 build:

```bash
curl -fsSL "https://api.github.com/repos/anhkhoakz/hut-build/releases/latest" |
  jq -r '.assets[] | select(.name | endswith("linux-x86_64.tar.gz")) | .browser_download_url' |
  xargs curl -fLO
```

Download the latest Linux arm64 build:

```bash
curl -fsSL "https://api.github.com/repos/anhkhoakz/hut-build/releases/latest" |
  jq -r '.assets[] | select(.name | endswith("linux-arm64.tar.gz")) | .browser_download_url' |
  xargs curl -fLO
```

## Build Process

The GitHub Actions workflow:

1. Resolves the latest upstream sourcehut tag.
2. Clones the upstream `hut` repository.
3. Builds `hut` natively on matching GitHub-hosted runners.
4. Packages the binary as a `.tar.gz` archive.
5. Generates a SHA256 checksum file.
6. Publishes the files as GitHub release assets.

## Upstream Project

This repository is only an automated build mirror.

Upstream project: <https://git.sr.ht/~xenrox/hut>

Homepage: <https://sr.ht/~xenrox/hut>

## License

The upstream `hut` project is licensed under the GNU Affero General Public License v3.0 or later.

Release artifacts published by this repository are built from upstream `hut` source code and remain under the upstream license.
