# OrangeFox Recovery device tree for the Samsung Galaxy Note10+ 5G (d2x)

| Device | Samsung Galaxy Note10+ 5G |
| :-- | :-- |
| Codename | d2x |
| Models | SM-N976B, SM-N976N |
| SoC | Exynos 9825 |

Common tree: [android_device_samsung_exynos9820-common](https://github.com/Exynos982x-OrangeFox/android_device_samsung_exynos9820-common)

## Kernel

The prebuilt `Image` and `dtbo.img` are extracted from the official LineageOS 23.2 `recovery.img` of
2026-10-25 (sha256 `234f878677f9447a6d9613f79ef0cbe4f4965387594e48698f13fdfdefc46f2e`), built from
[android_kernel_samsung_exynos9820](https://github.com/LineageOS/android_kernel_samsung_exynos9820/tree/a412cfaf86b980ce35cae96a35f678c8ea551575)
with `exynos9820-d2x_defconfig`.

## Building

```sh
git clone https://gitlab.com/OrangeFox/sync.git
cd sync
./orangefox_sync.sh --branch 12.1 --path ~/fox_12.1

cd ~/fox_12.1
git clone -b fox_12.1 https://github.com/Exynos982x-OrangeFox/android_device_samsung_d2x device/samsung/d2x
git clone -b fox_12.1 https://github.com/Exynos982x-OrangeFox/android_device_samsung_exynos9820-common device/samsung/exynos9820-common

export FOX_BUILD_DEVICE=d2x
source build/envsetup.sh
lunch twrp_d2x-eng
mka adbd recoveryimage
```

The recovery image is written to `out/target/product/d2x/`, along with an Odin-flashable `.tar`.
