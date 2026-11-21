# k-releases

Prebuilt binaries for personal tools. Source repositories are private.

| Tool | Tag format | Status |
|---|---|---|
| `kerdr` | `kerdr-v<upstream version>-<build>` | [kerdr-v0.9.5-1](https://github.com/mkeiji/k-releases/releases/tag/kerdr-v0.9.5-1) |
| `kagent` | `kagent-v<version>` | [kagent-v0.1.15](https://github.com/mkeiji/k-releases/releases/tag/kagent-v0.1.15) |

`kerdr` is a patched build of [Herdr](https://github.com/herdrdev/herdr) with `kagent` support.

## Install kerdr

Requirements: Linux x86-64 with glibc 2.39 or newer.

Ensure `~/.local/bin` is on your `PATH`. The binary currently reports `herdr 0.9.5`.

```sh
tag=kerdr-v0.9.5-1   # replace with the release you want
mkdir -p ~/.local/bin && cd "$(mktemp -d)"
curl -fLO "https://github.com/mkeiji/k-releases/releases/download/${tag}/kerdr-linux-x86_64.tar.gz"
curl -fLO "https://github.com/mkeiji/k-releases/releases/download/${tag}/kerdr-linux-x86_64.tar.gz.sha256"
sha256sum -c kerdr-linux-x86_64.tar.gz.sha256
tar -xzf kerdr-linux-x86_64.tar.gz
install -m 0755 kerdr ~/.local/bin/kerdr
kerdr --version
```

Do not run Herdr's built-in updater on `kerdr`. It can replace this build with upstream Herdr.

## Install kagent

Requirements: Linux x86-64 with glibc (tested with the release build host; Arch Linux under WSL is not yet verified), `curl`, `python3`, GNU coreutils (`sha256sum`) and `fuser` (Arch: `psmisc`). No Node.js, Bun, source checkout or GitHub login is needed. Keep the install on the Linux filesystem. Running KAgent still needs Python 3.11+ and `uv`.

The installer verifies the SHA-256 checksum of the archive before it installs anything. Download the bootstrap and review it before you run it:

```sh
version=0.1.15   # replace with the release you want
bootstrap="kagent-v${version}-linux-x64-install.sh"
curl -q -fSL --proto '=https' --proto-redir '=https' -o "$bootstrap" \
  "https://github.com/mkeiji/k-releases/releases/download/kagent-v${version}/${bootstrap}"
sh "$bootstrap"
kagent --version
```

Ensure `~/.local/bin` is on your `PATH`. Install a newer version by running the newer release's bootstrap. To go back to the previous version or remove kagent, run the same bootstrap with an option:

```sh
sh "$bootstrap" --rollback
sh "$bootstrap" --uninstall
```

Uninstall leaves your sessions and configuration in place.

## Verify downloads

Each release lists a SHA-256 checksum file. Always run `sha256sum -c` before installing.

## Licence

Each tool keeps its own licence. See the licence file inside each release archive.
