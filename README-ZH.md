<div align="center">

# 🚀 PRoot 多架构静态编译发行版

**基于 [PRoot](https://github.com/proot-me/proot) 官方源码自动同步的 `amd64` / `arm64` / `arm32` 纯静态编译版本**

[![GitHub Release](https://img.shields.io/github/v/release/upleung/proot-releases?style=flat-square&logo=github&label=最新发布&color=2ea44f)](https://github.com/upleung/proot-releases/releases/latest)
[![Build Status](https://img.shields.io/github/actions/workflow/status/upleung/proot-releases/auto-sync-release.yml?style=flat-square&logo=githubactions&label=自动化构建)](https://github.com/upleung/proot-releases/actions)
[![Architectures](https://img.shields.io/badge/架构-amd64%20%7C%20arm64%20%7C%20arm32-007ec6?style=flat-square&logo=linux)](#)
[![Build Base](https://img.shields.io/badge/编译环境-Ubuntu%2024.04%20(glibc%20静态)-E95420?style=flat-square&logo=ubuntu)](#)
[![License](https://img.shields.io/badge/开源协议-GPL%20v2-blue?style=flat-square)](./COPYING)

</div>

---

## 📖 项目简介

**PRoot** 是 `chroot`、`mount --bind` 和 `binfmt_misc` 的用户空间实现。它允许用户在**无需 Root 权限**的情况下，在受限的 Docker 容器、云虚拟主机或嵌入式设备中直接挂载并运行完整的 Linux 发行版（如 Debian、Ubuntu、Alpine）。

由于上游官方仓库 [`proot-me/proot`](https://github.com/proot-me/proot) 默认仅编译并提供 `amd64` (`x86_64`) 单一架构的二进制文件，本仓库通过 GitHub Actions 定期自动同步上游最新源码，严格按照官方 `release.yml` 原版编译流程（Ubuntu 24.04 `glibc` 静态链接、保留完整符号表不 `strip`），同时构建并发布 **`amd64`**、**`arm64`** 和 **`arm32`** 三大主流架构的纯静态单文件版本。

## ✨ 核心特性

- 🛠️ **100% 官方原版构建逻辑**：完全对齐上游 `release.yml` 构建流程，基于 **Ubuntu 24.04 LTS (`glibc`)** 静态编译，保留完整符号表（`amd64` 原版约 1.76 MB）。
- 📦 **三架构全覆盖**：同时提供 `x86_64`、`aarch64` (`arm64`) 以及 `arm` (`armv7l` / `arm32`) 静态二进制文件。
- 🔄 **全自动定时同步**：每月 1 号自动检测并同步上游 `proot-me/proot` 最新源码，自动生成规范化版本标签并发布至 Releases。
- 🔒 **零外部依赖，开箱即用**：单文件纯静态编译，直接下载赋予执行权限即可在各类无 Root 容器、精简系统或玩客云等设备上运行。

## 📊 架构与编译产物对照表

| 架构简称 | 标准架构名 | 文件体积 | 适用设备与平台 | 编译产物文件名 |
| :--- | :--- | :---: | :--- | :--- |
| **`amd64`** | `x86_64` | ~1.76 MB | PC / 云服务器 / 各类 PaaS 云容器 (Intel / AMD 64位) | `proot-v*-x86_64-static` |
| **`arm64`** | `aarch64` | ~1.60 MB | ARMv8 服务器、外贸电视盒子、树莓派 4/5、手机 Termux | `proot-v*-aarch64-static` |
| **`arm32`** | `arm` (`armv7l`) | ~1.20 MB | 玩客云 (OneCloud) 等 32位 ARMv7 / armhf 嵌入式设备 | `proot-v*-arm-static` |

## ⚡ 快速下载与使用

### 1. 下载对应架构二进制文件
```bash
# amd64 (x86_64)
curl -fsSL [https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-x86_64-static](https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-x86_64-static) -o proot

# arm64 (aarch64)
curl -fsSL [https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-aarch64-static](https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-aarch64-static) -o proot

# arm32 (armv7l / 玩客云)
curl -fsSL [https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-arm-static](https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-arm-static) -o proot

```

### 2. 赋予执行权限并验证版本

```bash
chmod +x proot
./proot --version

```

### 3. 启动进入 Rootfs 容器环境

```bash
# 无需 root 权限，直接以模拟 root 身份进入目录
./proot -S ./debian-rootfs /bin/bash

```

## 📄 开源协议 (License)

本项目遵循上游的 [GNU General Public License v2.0 (GPL-2.0)](https://www.google.com/search?q=./COPYING) 开源协议。
