# Arch/CachyOS package backport

This directory packages `mpv 0.41.0` with the upstream screenshot fix from commit `c66204b69ba201cf6611daae7e515442eed4b9cd`.

The package intentionally stays a drop-in replacement for the repo `mpv` package:

- `pkgname=mpv`
- `epoch=1`
- `pkgver=0.41.0`
- `pkgrel=4`
- `arch=('x86_64')`

## Files

- `PKGBUILD`: Arch package recipe based on the current Arch Linux `mpv` package.
- `0001-screenshot-correctly-detect-hardware-frame.patch`: one-line backport of the upstream fix.
- `upstream-mpv-release-key.asc`: upstream key used to verify the signed `v0.41.0` tag.
- `RELEASE_NOTES.md`: release body used by the GitHub release workflow.

## Local build

From this directory:

```bash
gpg --import upstream-mpv-release-key.asc
makepkg -s --cleanbuild
```

This should produce a package named like:

```bash
mpv-1:0.41.0-4-x86_64.pkg.tar.zst
```

Install it with:

```bash
sudo pacman -U ./mpv-1:0.41.0-4-x86_64.pkg.tar.zst
```

Rollback with:

```bash
sudo pacman -S mpv
```

## GitHub release workflow

The workflow at `.github/workflows/release-arch-package.yml` builds the package in a clean Arch container, uploads the package and recipe assets, publishes them to GitHub Releases, and generates a GitHub artifact attestation for the built package.
