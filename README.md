# SUSFS Guard LKM Modules

给 **SenseiSU / KernelSU-Next（LKM 模式）** 用的 SUSFS 内核模块，按 KMI 分包，直接当普通模块刷入。

## 下载

到 **Releases** 页面下载对应你内核版本的压缩包：

| 内核 | 文件 |
|---|---|
| 5.10 (Android 12/13) | `SUSFS-Guard-android12-5.10.zip` / `android13-5.10.zip` |
| 5.15 (Android 13/14) | `SUSFS-Guard-android13-5.15.zip` / `android14-5.15.zip` |
| 6.1 (Android 14) | `SUSFS-Guard-android14-6.1.zip` |
| 6.6 (Android 15) | `SUSFS-Guard-android15-6.6.zip` |
| 6.12 (Android 16) | `SUSFS-Guard-android16-6.12.zip` |
| 6.18 (Android 17) | `SUSFS-Guard-android17-6.18.zip` |

不确定自己的 KMI？在管理器首页能看到内核版本，例如 `6.6.89-android15-...` → 选 **android15-6.6**。

## 安装

1. 管理器 → 模块 → 从本地安装
2. 选对应 zip
3. 重启
4. 首页显示 `SUSFS: LKM 模块` 即成功

## 说明

- 本仓库只放模块的发布产物，源码与构建在内核仓库：<https://github.com/kylinmode/SENSEISU>
- 模块只是 SUSFS 的 LKM 载体，真正的 SUSFS 逻辑在 `susfs_guard_lkm.ko` 内
- 与 KSU-Next 系（含 SenseiSU）通用，驱动签名需匹配对应管理器
