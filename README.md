# Metrolist for Arch

A personal fork of [Metrolist](https://github.com/MetrolistGroup/Metrolist) that builds a desktop package for Arch Linux x86_64, including Omarchy. It removes the Omarchy startup check. The default branch tracks upstream development. Stable packages are built from version branches, starting with [release/14.0.1](https://github.com/xonha/metrolist/tree/release/14.0.1).

## Install or update

Download the `.pkg.tar.zst` file from this fork's [GitHub Releases](https://github.com/xonha/metrolist/releases), then install it with pacman.

```sh
sudo pacman -U ./metrolist-omarchy-bin-14.0.1-1-x86_64.pkg.tar.zst
```

Use the downloaded filename when installing a newer version. If `metrolist-desktop-bin` or `metrolist-git` is installed, pacman will prompt to replace it. Open **Metrolist** from your app launcher after installation.

## Build from source

Install JDK 25 (Temurin) and see the [desktop build documentation](docs/desktop.md) for platform dependencies. Run these commands from this checkout.

```sh
git submodule update --init --recursive
./gradlew :desktopApp:createReleaseDistributable
```

The desktop build is written to `desktopApp/build/compose/binaries/main-release/app/Metrolist`.

## Publish an Arch package

Run [Release Arch package](https://github.com/xonha/metrolist/actions/workflows/arch-release.yml) from the matching version branch, such as `release/14.0.1`. The workflow builds the x86_64 package and publishes it with `SHA256SUMS`. Increment `pkgrel` in the [Arch recipe](packaging/arch/PKGBUILD) for packaging changes within the same upstream version.

## Upstream and license

Metrolist was developed by the [Metrolist team and contributors](https://github.com/MetrolistGroup/Metrolist/graphs/contributors). The Omarchy change follows [TripleU613's compatibility patch](https://github.com/omacom/omarchy-pkgs/pull/3371/files). The project is licensed under the [GNU GPL 3.0](LICENSE).

See the [upstream project](https://github.com/MetrolistGroup/Metrolist) for other platforms, feature documentation, community links, and notices about using the client with YouTube Music.
