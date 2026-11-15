# AlpineiOS Phosh images

ARM64 postmarketOS v26.06 guest images for AlpineiOS. Each release contains the image manifest, the ARM64 UEFI firmware and the Phosh VM disk.

The guest boots Phosh and installs the applications selected in AlpineiOS from its configured Alpine and postmarketOS repositories. This is an independently prepared VM image for AlpineiOS.

## Rebuild the image

On an Apple silicon Mac with QEMU and Python installed, run:

```sh
bash scripts/prepare_phosh.sh --downloadable work/PhoshRelease
python3 scripts/publish_phosh_image.py work/PhoshRelease work/PhoshAssets
```

The recipe starts from an Alpine ARM64 cloud image and installs the postmarketOS packages. The exact packages in this release are listed in `guest-packages.txt`. Upstream packaging recipes and source references are maintained in [Alpine aports](https://gitlab.alpinelinux.org/alpine/aports/-/tree/3.24-stable) and [postmarketOS pmaports](https://gitlab.postmarketos.org/postmarketOS/pmaports). Firmware is from QEMU's [EDK II firmware build](https://gitlab.com/qemu-project/qemu/-/tree/master/roms/edk2-build.config).

The VM disk packer comes from [WindowsiOS](https://github.com/ammaarreshi/WindowsiOS) and its upstream [Henge](https://github.com/Leviidev/Henge). See [LICENSE](LICENSE) for the preparation tools.
