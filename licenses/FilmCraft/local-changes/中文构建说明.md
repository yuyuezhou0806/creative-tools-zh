# 简体中文本地构建

本地中文界面基于 FilmCraft 主分支提交 `7b6c134472287db4367fca80bcb498240ba36567`。
这是针对本机使用的修改版，保留官方版本和 CLI。新增的界面语言为 `zh-hans`。

`crates/ui-egui/src/i18n/zh-hans.tsv` 覆盖此提交西班牙语词表中的 3466 个界面键。
其中 405 个英文键对应的中文译文复用了 PhotoCraft 和 PdfCraft 的开源中文词表；
3061 个其余键根据英文界面含义翻译。命令 ID、文件格式、协议字段、快捷键和模板占位符保持原样。
本地构建没有使用 Adobe 的翻译资源。未经过界面词表的引擎诊断和用户素材名称仍可能显示英文。

翻译输入来源：

- PhotoCraft `9c427a7a2c792d326939f5b27b1d814a7c6321a7`，`crates/ui-egui/src/i18n/zh-hans.tsv`。
- PdfCraft `49c6e2ec5437a355da4e9dadd9cc2db3476b5cf8`，`crates/ui-egui/src/i18n/zh-hans.tsv`。
- 两个项目许可均为 MIT OR Apache-2.0，相关英文键和来源记录保存于部署目录。

新建的首选项默认选择简体中文。可以在“编辑 > 语言 > 简体中文”以及“编辑 > 首选项 > 常规”切换。
`--data-dir` 可指定配置位置；直接运行此构建时，配置默认位于可执行文件旁的 `FilmCraftData`。
明确保存的语言选择会在后续启动时保留。官方英文版的首选项不受影响。

界面使用官方 `cjk.rs` 字体回退，优先选择本机 Microsoft YaHei UI、Microsoft YaHei 等字体，
并为比例、等宽、medium 和 semibold 字体族补充中文。不打包 Windows 字体文件。
找不到支持中文的字体时回退到英语，并显示提示。

本地修改版移除了界面中的 ArtCraft 商标图片，以遵守官方 `AGENTS.md` 的商标规则。

编译：Rust 1.99.0 GNU，MinGW-w64，仅构建 GUI。

```powershell
$env:CARGO_PROFILE_RELEASE_LTO = 'false'
$env:CARGO_PROFILE_RELEASE_CODEGEN_UNITS = '16'
cargo build --release --locked -p filmcraft --target x86_64-pc-windows-gnu -j 2
```

这项修改增加界面语言，不保证与 Adobe 产品的完整功能或文件兼容性。
