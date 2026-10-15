# Creative Tools 中文适配版

**基于上游开源项目的非官方汉化整理版。本仓库只做界面中文适配及配套整理，软件核心功能来自原作者，原项目版权和贡献归属不变。**

本仓库不代表原作者或 ArtCraft 团队，也不是上游官方发布。这里集中维护汉化补丁、中文启动入口、来源及许可证；完整 Windows 程序在 Releases 下载。

## 下载与使用

- [下载本次完整中文合集（Windows x64，约 248 MB）](https://github.com/yuyuezhou0806/creative-tools-zh/releases/download/v2026.10.15-zh.1/CreativeTools-Chinese-Windows-x64.zip)
- [查看所有发布版本](https://github.com/yuyuezhou0806/creative-tools-zh/releases)
- [SHA-256 校验值](SHA256SUMS.txt)

完整解压 ZIP，然后双击最外层对应的中文 `启动…` 文件。无需安装 Codex、Python 或 Rust。适用于 Windows 64 位 Intel / AMD 电脑；不要直接在压缩包里启动程序。详细说明见包内「中文使用说明.html」。

## 引用与原项目

四款软件均来自 **[storytold](https://github.com/storytold)** 维护的开源项目，核心程序由 ArtCraft 团队及上游贡献者开发：

| 软件 | 上游项目 | 本包基准版本 | 本地工作范围 |
| --- | --- | --- | --- |
| PhotoCraft | [storytold/photocraft](https://github.com/storytold/photocraft) | [0.5.0](https://github.com/storytold/photocraft/releases/tag/v0.5.0) | 官方程序原样保留；使用上游已有简体中文，预设语言并添加中文入口 |
| FilmCraft | [storytold/filmcraft](https://github.com/storytold/filmcraft) | [0.4.0](https://github.com/storytold/filmcraft/releases/tag/v0.4.0) | 新增简体中文词表及语言选项、系统中文字体回退、便携设置 |
| EffectCraft | [storytold/effectcraft](https://github.com/storytold/effectcraft) | [0.6.0](https://github.com/storytold/effectcraft/releases/tag/v0.6.0) | 常用界面中文适配及便携中文配置；部分专业名称和诊断文字仍为英文 |
| PdfCraft | [storytold/pdfcraft](https://github.com/storytold/pdfcraft) | [0.4.0](https://github.com/storytold/pdfcraft/releases/tag/v0.4.0) | 使用上游已有中文词表，修复系统中文字体回退和方框缺字，预设中文 |

准确的源码提交、补丁顺序及程序哈希见 [UPSTREAM.json](UPSTREAM.json)。**PhotoCraft 和 PdfCraft 已有的中文翻译属于上游贡献，不宣称为本仓库原创。**

## 关于“只是做了汉化”

本仓库的定位是汉化与中文使用体验适配，不是重新开发这四款软件。为准确记录实际差异，除词条翻译外还包含中文字体回退、语言/便携设置、中文入口与说明；修改版按上游品牌许可移除了受限制的 ArtCraft 品牌图案。未添加新的图像、剪辑、动效或 PDF 处理核心功能。四款 CLI 均保留官方版本。

FilmCraft 共适配 3466 个界面键：其中 405 个复用 PhotoCraft / PdfCraft 的开源中文词条，3061 个根据英文界面翻译。来源与署名见 [FilmCraft 汉化说明](docs/FilmCraft-汉化说明.md) 及补丁内的 `zh-hans.tsv.attribution`。不使用 Adobe 翻译资源，也不宣称完整兼容 Adobe 产品或文件格式。

## 许可证与署名

上游应用代码采用 MIT OR Apache-2.0，第三方资源遵循各自许可。原作者声明、NOTICE、翻译归属、字体与依赖许可保留在 [licenses](licenses/) 和下载包内。汉化修改按对应上游许可提供；本仓库的说明及启动入口采用同样的 MIT OR Apache-2.0 许可。品牌名称和图案受独立许可约束，不因代码开源而授予商标权。参见 [LICENSE.md](LICENSE.md)。

## 目录

- `patches/`：三个本地 GUI 构建的实际修改补丁。
- `portable/`：干净的中文配置、相对路径启动入口和使用说明；不含 EXE，不能单独运行。
- `licenses/`：上游和第三方许可及来源记录。
- [BUILD.md](BUILD.md)：固定上游提交及补丁应用/编译说明。

## 验证范围

下载包构建于 2026-10-10，本次发布复核包的 SHA-256，保持原包字节不变。已在一台 Windows 电脑完成中文界面、基本文件读写/渲染、便携目录验证；最终 ZIP 完整解压校验及四款 CLI 启动通过。未做所有功能覆盖或第二台电脑兼容测试。包内不含打包者的项目、历史、缓存或凭据。

中文依赖收件电脑的系统字体；若出现方框字，请安装 Windows 简体中文补充字体后重启软件。软件功能问题可先对照上游，汉化或打包问题可在本仓库提出。
