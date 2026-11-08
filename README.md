# k-releases

Prebuilt binaries for personal tools. Source repositories are private.

| Tool | Tag format | Status |
|---|---|---|
| `kerdr` | `kerdr-v<upstream version>-<build>` | [kerdr-v0.9.5-1](https://github.com/mkeiji/k-releases/releases/tag/kerdr-v0.9.5-1) |
| `kagent` | `kagent-v<version>` | First release pending |

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

## Verify downloads

Each release lists a SHA-256 checksum file. Always run `sha256sum -c` before installing.

## Licence

Each tool keeps its own licence. See the licence file inside each release archive.
