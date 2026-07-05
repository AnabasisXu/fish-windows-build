# fish-windows-build

在 GitHub Actions 上编译 fish shell 的 Windows (MSYS2) 版本，无需本地安装 MSYS2。

## 方案一：从源码编译 4.0.2（Berrysoft fork）

使用 `build-fish-windows.yml` workflow。

- 下载 fish 4.0.2 源码
- 应用 Berrysoft 的 Cygwin 补丁
- 在 Windows runner 的 MSYS2 环境内编译
- 输出 `fish.exe`、`fish_indent.exe`、`fish_key_reader.exe`

**触发方式：** push 到 main 分支，或手动触发 `workflow_dispatch`。

## 方案二：直接获取 MSYS2 预编译包

使用 `download-fish-msys2.yml` workflow。

- 直接从 MSYS2 仓库安装最新版 fish（当前 4.8.0）
- 打包为 portable artifact

**触发方式：** 手动触发。

## 使用方法

1. 创建 GitHub 仓库，推送此目录
2. 在 Actions 页面选择 workflow 运行
3. 下载 artifact 中的 fish 二进制文件

## 注意

编译产物是 MSYS2/Cygwin 可执行文件，运行时需要 `msys-2.0.dll`（MSYS2 运行时）。
最简单的使用方式：安装 MSYS2 后将编译好的 fish.exe 放入 `/usr/bin/`。
