# 固定来源与构建说明

普通用户直接下载 Releases，无需编译。本仓库保存实际汉化补丁，不复制整个上游仓库；完整源码通过下列固定提交取得。先安装 Git、Rust 及其 GNU Windows x64 工具链、MinGW-w64 和 CMake，并按各上游构建说明准备其他依赖。

下面命令从本仓库根目录运行，`work/` 中每个目录应不存在。补丁必须按顺序应用，不能直接应用到未知版本的上游 main。本次发布前已在固定提交的干净副本上逐项验证补丁应用。

```powershell
$patchRoot = (Resolve-Path './patches').Path
New-Item -ItemType Directory -Path './work' -Force
```

## FilmCraft

```powershell
git clone --no-checkout https://github.com/storytold/filmcraft.git ./work/filmcraft
git -C ./work/filmcraft checkout --detach 7b6c134472287db4367fca80bcb498240ba36567
git -C ./work/filmcraft apply --whitespace=nowarn "$patchRoot/FilmCraft/filmcraft-zh-hans.patch"
$env:CARGO_PROFILE_RELEASE_LTO = 'false'
$env:CARGO_PROFILE_RELEASE_CODEGEN_UNITS = '16'
cargo build --manifest-path ./work/filmcraft/Cargo.toml --release --locked --target x86_64-pc-windows-gnu -p filmcraft -j 2
```

## EffectCraft

```powershell
git clone --no-checkout https://github.com/storytold/effectcraft.git ./work/effectcraft
git -C ./work/effectcraft checkout --detach 30aaddf7c23329dcdfc72a5bf65b55747bbd6be1
git -C ./work/effectcraft apply --whitespace=nowarn "$patchRoot/EffectCraft/local-common-chinese-ui.patch"
git -C ./work/effectcraft apply --whitespace=nowarn "$patchRoot/EffectCraft/remove-artcraft-mark.patch"
$env:CARGO_PROFILE_RELEASE_LTO = 'false'
$env:CARGO_PROFILE_RELEASE_CODEGEN_UNITS = '16'
cargo build --manifest-path ./work/effectcraft/Cargo.toml --release --locked --target x86_64-pc-windows-gnu -p effectcraft -j 2
```

## PdfCraft

```powershell
git clone --no-checkout https://github.com/storytold/pdfcraft.git ./work/pdfcraft
git -C ./work/pdfcraft checkout --detach a016f88a908716e965e9905da7632cb136234bb7
git -C ./work/pdfcraft apply --whitespace=nowarn "$patchRoot/PdfCraft/local-chinese-font-fallback.patch"
git -C ./work/pdfcraft apply --whitespace=nowarn "$patchRoot/PdfCraft/remove-restricted-artcraft-marks.patch"
$env:CARGO_PROFILE_RELEASE_LTO = 'false'
$env:CARGO_PROFILE_RELEASE_CODEGEN_UNITS = '16'
cargo build --manifest-path ./work/pdfcraft/Cargo.toml --release --locked --target x86_64-pc-windows-gnu -p pdfcraft -j 2
```

## 组装

PhotoCraft 使用官方 0.5.0 Windows x64 portable 原包，无源码修改。四款 CLI 分别使用 UPSTREAM.json 对应官方 release 的 EXE，不使用 GUI 构建代替官方 CLI。将三个 GUI 构建及官方程序放入 `portable/<应用名>/` 的相应位置，保留每个官方包和本仓库提供的许可；中文启动入口引用该目录下 EXE。EffectCraft 必须通过入口设置 `EFFECTCRAFT_CONFIG_DIR`，否则默认配置位置不同。

发布版使用 Rust 1.99.0 GNU、MinGW-w64。以上记录源码和主要参数，不承诺不同工具链或机器得到逐字节相同的二进制。中文字体从系统读取，不把 Windows 字体文件复制进分享包。
