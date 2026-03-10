# mpv 0.41.0-4 screenshot fix backport

This release backports upstream `mpv` commit `c66204b69ba201cf6611daae7e515442eed4b9cd` onto `v0.41.0`.

## What it fixes

On Wayland systems with hardware-decoded video, `mpv 0.41.0` can fail to take screenshots after FFmpeg 8 era changes exposed a hardware-frame detection bug in the screenshot path.

This build fixes that without changing the public `mpv` or `libmpv` interface.

## Install

```bash
sudo pacman -U ./mpv-1-0.41.0-4-x86_64.pkg.tar.zst
```

## Rollback

```bash
sudo pacman -S mpv
```

## Verify provenance

If this package was built by GitHub Actions in this repository, you can verify the GitHub attestation with:

```bash
gh attestation verify ./mpv-1-0.41.0-4-x86_64.pkg.tar.zst -R OWNER/REPO
```
