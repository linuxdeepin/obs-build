
该存储库提供`build`工具，以一种安全且可复制的方法来构建二进制包。它可以被单独使用，也可以在[开源构建服务](http://openbuildservice.org) (Open Build Service, OBS)中使用

`obs-build` 的最新软件包可从[openSUSE:Tools downloads](https://software.opensuse.org/download/package?package=obs-build&project=openSUSE%3ATools)获得

[文档可在此处获得](http://opensuse.github.io/obs-build/pbuild.html)


支持的构建环境
============================

不安全
---
- `chroot`
- `LXC`

安全但可重复性有限
---
- `docker`
- `nspawn`

安全且具有完全可重复性
---
- `KVM`
- `XEN`
- `ZVM` (**S390**)

实验支持
---
此外，目前还有以下实验支持

- `UML`
- `PVM` (**PowerPC**)
- [OpenStack](http://openstack.org)
- [Amazon EC2](http://ec2.amazon.com)

硬件仿真有以下几种方式：
---
- `qemu`,它在 `KVM` 中运行一个`QEMU`系统模拟器, 这个可以也被认为是安全和可重现的。
- 通过封装脚本, "模拟器"VM 可用于运行使用任何其他模拟器。
- 使用`QEMU` 进行用户空间模拟也是可能的，这将提供更高的速度，但需要在基础发行版中进行准备工作

支持的构建格式
=======================

主要分发包的格式
---
- `spec` to `rpm`,           e.g. [SUSE](http://suse.com), [Fedora](http://getfedora.org), [RedHat](http://redhat.com),
[CentOS](http://centos.org), [Mandriva](http://mageia.org)
- `dsc` to `deb`,            e.g. [Debian](http://debian.org), [Ubuntu](http://ubuntu.com)
- `PKGBUILD` to `pkg`,       e.g. [Arch Linux](http://archlinux.org)

图片格式
---
- `Dockerfile`—通过 `docker` 或 `podman` 工具创建 [Docker](http://docker.com) 容器
- kiwi appliances—这包括 kiwi 工具支持的[大量格式](http://documentation.suse.com/kiwi/9/html/kiwi/image-types.html)，从 Live USB Stick 镜像、网络部署镜像、虚拟机镜像到 Docker 容器。
- SUSE 产品—[SUSE](http://suse.com) 产品介质构建。
- SimpleImage*&mdash;基于 `rpm` 规范文件语法的 `chroot` `tar` 压缩包。
- [Debian](http://debian.org) *Livebuild*
- *Preinstallimages*&mdash;用于加速构建，特别是在 [OBS](http://openbuildservice.org/) 内部。

桌面图像格式
---
- *AppImage*
- *FlatPak*
- *Snapcraft*

特殊模式和格式
---
- `debbuild`：从 `rpm` spec 文件构建 [debian](http://debian.org) deb 包
- `debbootstrap`：使用 `debootstrap` 引擎构建 [debian](http://debian.org) 
- `mock`：使用 [`mock`](https://github.com/rpm-software-management/mock) 构建 `rpm` spec 文件。
- `collax`：[debian](http://debian.org) 包的变种。
- `fissile`：基于 `BOSH` 开发版本的 `docker` 镜像。
- `helm`：`helm` charts。
- `modulemd`：`modulemd` rpm-md 扩展

使用 `--help` 选项获取更多信息
