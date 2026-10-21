<div align="center">

# 🚀 PRoot Multi-Arch Static Releases

**Automated Multi-Architecture (`amd64` / `arm64` / `arm32`) Static Builds of [PRoot](https://github.com/proot-me/proot)**

[![GitHub Release](https://img.shields.io/github/v/release/upleung/proot-releases?style=flat-square&logo=github&label=Latest%20Release&color=2ea44f)](https://github.com/upleung/proot-releases/releases/latest)
[![Build Status](https://img.shields.io/github/actions/workflow/status/upleung/proot-releases/auto-sync-release.yml?style=flat-square&logo=githubactions&label=Multi-Arch%20Build)](https://github.com/upleung/proot-releases/actions)
[![Architectures](https://img.shields.io/badge/Arch-amd64%20%7C%20arm64%20%7C%20arm32-007ec6?style=flat-square&logo=linux)](#)
[![Build Base](https://img.shields.io/badge/Base-Ubuntu%2024.04%20(glibc%20static)-E95420?style=flat-square&logo=ubuntu)](#)
[![License](https://img.shields.io/badge/License-GPL%20v2-blue?style=flat-square)](./COPYING)

<br>

### 🌐 [**🇺🇸 English Documentation**](#-english-documentation) &nbsp;|&nbsp; [**🇨🇳 简体中文文档**](#-简体中文文档)

</div>

---

<a id="-english-documentation"></a>


### 📖 Overview

**PRoot** is a user-space implementation of `chroot`, `mount --bind`, and `binfmt_misc`. It enables users to run any Linux distribution or rootfs inside an unprivileged container or restricted host environment **without root privileges**.

While the upstream [`proot-me/proot`](https://github.com/proot-me/proot) repository only publishes prebuilt binaries for `x86_64` (`amd64`), **`upleung/proot-releases`** automatically syncs with the upstream source code and builds official-grade, standalone static binaries for **`amd64` (`x86_64`)**, **`arm64` (`aarch64`)**, and **`arm32` (`armv7l` / `armhf`)**.

### ✨ Key Features

- 🛠️ **100% Upstream Build Logic**: Strictly follows the official `release.yml` build process on **Ubuntu 24.04 LTS** (`glibc` + `libtalloc` static linking, unstripped with full symbols).
- 📦 **Three Major Architectures**: Covers `x86_64` servers, `aarch64` boards/boxes, and 32-bit `armv7l` devices (such as OneCloud / 玩客云).
- 🔄 **Automated Upstream Sync**: Automatically checks and syncs with `proot-me/proot` on the 1st of every month via GitHub Actions.
- 🔒 **Zero Runtime Dependencies**: Fully static ELF binaries that run seamlessly across Alpine, Debian, Ubuntu, BusyBox, and `noexec`/restricted container environments.

### 📊 Architecture & Binary Matrix

| Arch Alias | Target | Typical Size | Supported Devices & Platforms | Asset Filename |
| :--- | :--- | :---: | :--- | :--- |
| **`amd64`** | `x86_64` | ~1.76 MB | PC, Cloud Servers, Docker/PaaS Containers | `proot-v*-x86_64-static` |
| **`arm64`** | `aarch64` | ~1.60 MB | ARMv8 Servers, Raspberry Pi 4/5, TV Boxes, Termux | `proot-v*-aarch64-static` |
| **`arm32`** | `arm` (`armv7l`) | ~1.20 MB | OneCloud (玩客云), 32-bit ARMv7 / armhf Boards | `proot-v*-arm-static` |

### ⚡ Quick Start & Download

#### 1. Download for `amd64` (`x86_64`)
```bash
curl -fsSL [https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-x86_64-static](https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-x86_64-static) -o proot
chmod +x proot
./proot --version
```

#### 2. Download for `arm64` (`aarch64`)
```bash
curl -fsSL [https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-aarch64-static](https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-aarch64-static) -o proot
chmod +x proot
./proot --version
```

#### 3. Download for `arm32` (`armv7l` / `armhf`)
```bash
curl -fsSL [https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-arm-static](https://github.com/upleung/proot-releases/releases/latest/download/proot-v5.5.0-arm-static) -o proot
chmod +x proot
./proot --version
```

#### 4. Enter a Custom Rootfs (e.g., Debian / Alpine)
```bash
./proot -S ./rootfs /bin/bash
```
