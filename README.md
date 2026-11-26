# SUSFS Guard LKM Modules

For **SenseiSU / KernelSU-Next** in LKM mode — enables SUSFS without rebuilding the kernel.

在 **SenseiSU（LKM 模式）** 下启用 SUSFS 的内核模块，无需重新编译内核。

## 支持的 KMI / Supported KMIs

| KMI | Kernel | Module |
|---|---|---|
| android12-5.10 | 5.10.x | `SUSFS-Guard-android12-5.10.zip` |
| android13-5.10 | 5.10.x | `SUSFS-Guard-android13-5.10.zip` |
| android13-5.15 | 5.15.x | `SUSFS-Guard-android13-5.15.zip` |
| android14-5.15 | 5.15.x | `SUSFS-Guard-android14-5.15.zip` |
| android14-6.1  | 6.1.x  | `SUSFS-Guard-android14-6.1.zip` |
| android15-6.6  | 6.6.x  | `SUSFS-Guard-android15-6.6.zip` |
| android16-6.12 | 6.12.x | `SUSFS-Guard-android16-6.12.zip` |
| android17-6.18 | 6.18.x | `SUSFS-Guard-android17-6.18.zip` |

查自己的 KMI：

```sh
uname -r
# 6.6.89-android15-8-... → android15-6.6
```

## 安装 / Install

1. 下载对应 KMI 的 zip
2. SenseiSU → 模块 → 从本地安装
3. 重启
4. 打开首页确认显示 `SUSFS: LKM 模块`

## 原理 / How it works

```
module zip
├── module.prop           模块信息
├── customize.sh          安装时把 ko 复制到 /data/adb/
├── post-fs-data.sh       开机时 ksud insmod 加载
└── susfs_guard_lkm-<kmi>.ko
```

`ksud` 的加载器会在 vermagic 不匹配时自动改写并重试，所以同一 KMI 的不同小版本也能加载。

## 卸载 / Uninstall

删除模块后重启即可。残留的 `/data/adb/susfs_guard_lkm-*.ko` 可以手动删除。

## 构建来源 / Build source

这些 ko 由 [SenseiSU](https://github.com/kylinmode/SENSEISU) 的 CI 使用 Google DDK 镜像构建：

```yaml
container: ghcr.io/ylarod/ddk-min:<kmi>-20260828
```

## 许可 / License

GPL-2.0（SUSFS 部分版权归 [simonpunk/susfs4ksu](https://gitlab.com/simonpunk/susfs4ksu) 作者所有）
