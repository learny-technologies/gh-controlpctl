# gh-controlpctl

`gh-controlpctl` is a [GitHub CLI extension](https://cli.github.com/manual/gh_extension) that installs the private Learny `controlpctl` release on a developer Mac.

It contains neither Control Plane source code nor release artifacts. The extension uses the authenticated GitHub CLI session already stored in macOS Keychain; it never asks for, prints, or persists a GitHub token.

## Install

Authenticate once, install the extension, then install `controlpctl`:

```bash
gh auth login
gh extension install learny-technologies/gh-controlpctl
gh controlpctl install
```

The extension requires Python 3.12 or newer. On a standard developer Mac:

```bash
brew install python@3.12
```

It installs the CLI in an isolated virtual environment under `~/.local/share/controlpctl/versions/` and creates `~/.local/bin/controlpctl`. Ensure that `~/.local/bin` is in your `PATH`:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
exec zsh
```

Then sign in to Control Plane:

```bash
controlpctl auth login
```

## Update

```bash
gh controlpctl update
gh extension upgrade controlpctl
```

`gh controlpctl update` obtains the latest non-draft private release, verifies its published SHA-256 checksum, and switches only the `controlpctl` symlink after the installation succeeds.

## Commands

```bash
gh controlpctl install
gh controlpctl update
gh controlpctl status
```

Your GitHub account must have access to the private `learny-technologies/control-plane-workspace` repository. This extension is a bootstrapper only; `controlpctl` credentials continue to live solely in the macOS Keychain.
