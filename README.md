# Minecraft Mirror Bot

This repository contains GitHub Actions workflows for mirroring Minecraft metadata and assets from Mojang's servers.

## Repositories

The mirroring system uses three repositories:

1. [MinecraftMirror/version_manifest_v2](https://github.com/MinecraftMirror/version_manifest_v2) - Mirrors the version manifest
2. [MinecraftMirror/version](https://github.com/MinecraftMirror/version) - Mirrors version JSON files
3. [MinecraftMirror/libraries](https://github.com/MinecraftMirror/libraries) - Mirrors libraries and assets

## Workflow

1. The `mirror-manifest.yml` workflow runs monthly to check for updates to the version manifest.
2. When the manifest changes, it triggers the `mirror-versions.yml` workflow to download version JSONs.
3. When new version JSONs are processed, the `mirror-libraries.yml` workflow downloads any new libraries and assets.

## Directory Structure

The libraries repository maintains the same directory structure as Mojang's servers:

- `org/lwjgl/lwjgl/3.3.3/lwjgl-3.3.3-natives-windows-x86.jar` would be stored at the same path
- Client and server JARs are stored in `minecraft/client-server/`

## Setup Requirements

To use these workflows, you need:

1. Create the three repositories mentioned above
2. Add a repository secret called `GH_PAT` with a GitHub Personal Access Token that has `repo` scope permissions
3. Copy these workflow files into the `.github/workflows` directory of each repository

## Manual Triggering

All workflows can be triggered manually from the GitHub Actions tab if needed.
