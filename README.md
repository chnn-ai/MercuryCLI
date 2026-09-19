# MercuryCLI

This repository distributes verified Mercury runtimes for research environments. Mercury's application source is maintained separately in a private repository.

## Installation

Mercury's companion installs the matching runtime when you connect an SSH environment in **New Lab → Remote**. It checks the package version, size and SHA-256 digest before installation. Your host needs SSH access and standard system utilities; it does not need global Node.js, npm or a Mercury source checkout.

Packages support Linux with glibc and macOS, on x64 and arm64. They are published under [Releases](https://github.com/chnn-ai/MercuryCLI/releases), with a `remote-runtimes.json` manifest for each version. Windows and Alpine/musl are not remote runtime targets.

## What a package contains

- Mercury's compiled application and required production dependencies.
- A private Node.js executable and its license notices.
- Runtime launchers, version metadata and application assets.

Packages contain no provider API keys, account credentials, chats, research files, local settings or private source checkout. Compiled JavaScript can be inspected by someone who downloads the package or controls the host.

## Storage and model access

The runtime uses the selected directory directly: agent edits affect its original files. Runtime metadata, conversations and memory are stored under `~/.mercury` by default.

When Mercury's account gateway is available, the signed-in account authorizes an environment during setup. Model prompts pass through Mercury to the selected provider; Mercury's provider keys remain on its servers. Settings provides environment usage and access revocation. Workspace contents are not bulk uploaded by installing a runtime.

The remote service listens on host loopback and is reached through an authenticated SSH tunnel. Install it under the OS account whose file access the agent should have.

## Release integrity

Release versions are immutable. Each manifest records the supported platform, archive URL, size and SHA-256 digest. Packages are built and tested on their native platforms, including a fresh start with the bundled Node executable and an empty private data directory.

This repository contains release packages and distribution documentation only. An empty Releases page means no verified package has been published yet.
