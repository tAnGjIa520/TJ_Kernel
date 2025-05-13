# 操作系统内核项目 Readme

## 项目概述
这是一个操作系统内核开发项目，包含了用于写入映像文件和启动 QEMU 的任务配置。该项目旨在提供一个基础的操作系统内核开发环境，方便开发者进行内核开发、测试和调试。

## 目录结构
```
.
├── script/                  # 包含各种脚本文件
│   ├── img-write-osx.sh       # macOS 下的写入映像文件脚本
│   ├── img-write-win.bat      # Windows 下的写入映像文件批处理文件
│   ├── img-write-linux.sh     # Linux 下的写入映像文件脚本
│   ├── qemu-debug-osx.sh      # macOS 下的 QEMU 启动脚本
│   ├── qemu-debug-win.bat     # Windows 下的 QEMU 启动批处理文件
│   └── qemu-debug-linux.sh    # Linux 下的 QEMU 启动脚本
├── tasks.json                 # VS Code 任务配置文件
└── README.md                  # 项目说明文档
```

## 功能介绍
### 写入映像文件
该功能允许你将操作系统的映像文件写入到指定的存储设备或文件中。根据你的操作系统类型（macOS、Windows 或 Linux），相应的脚本会被执行。

#### 脚本文件
- **macOS**: `img-write-osx.sh`
- **Windows**: `img-write-win.bat`
- **Linux**: `img-write-linux.sh`

这些脚本会将映像文件写入到 `${workspaceRoot}/../../image/` 目录下。

### 启动 QEMU
QEMU 是一个开源的硬件虚拟化工具，可以用来运行和调试操作系统内核。该功能允许你在不同操作系统下启动 QEMU，并加载当前项目的映像文件进行调试。

#### 脚本文件
- **macOS**: [qemu-debug-osx.sh](file://d:\Desktop\Kernel\start\test\script\qemu-debug-osx.sh)
- **Windows**: [qemu-debug-win.bat](file://d:\Desktop\Kernel\start\test\script\qemu-debug-win.bat)
- **Linux**: [qemu-debug-linux.sh](file://d:\Desktop\Kernel\start\test\script\qemu-debug-linux.sh)

这些脚本会在 `${workspaceRoot}/../../image/` 目录下运行 QEMU。

### 调试准备
该任务是一个组合任务，依次执行 "写入映像文件" 和 "启动 QEMU" 两个子任务，确保在启动 QEMU 前已经正确写入了映像文件。

## 使用方法
1. **写入映像文件**：
   - 在 VS Code 中选择 "写映像文件" 任务。
   - 根据你的操作系统类型，相应的脚本将会被执行，并将映像文件写入到指定目录。

2. **启动 QEMU**：
   - 在 VS Code 中选择 "启动qemu" 任务。
   - 根据你的操作系统类型，相应的脚本将会被执行，并启动 QEMU 来加载映像文件。

3. **调试准备**：
   - 在 VS Code 中选择 "调试准备" 任务。
   - 该任务会依次执行 "写映像文件" 和 "启动 QEMU"，为你准备好调试环境。

## 开发环境要求
- **VS Code**：推荐使用 Visual Studio Code 作为开发和调试工具。
- **QEMU**：需要安装 QEMU 来进行内核的模拟和调试。
- **Make 工具**：如果你的项目中有 Makefile，则需要安装 make 工具来编译代码。
- **Shell 环境**：对于 macOS 和 Linux 用户，需要有 bash shell 环境；对于 Windows 用户，需要有支持批处理文件的命令行工具。

## 注意事项
1. **路径问题**：所有脚本都依赖于 `${workspaceRoot}` 变量，确保你的工作空间根目录设置正确。
2. **权限问题**：在某些情况下，写入映像文件可能需要管理员权限，请确保你有足够的权限来执行相关操作。
3. **脚本可定制性**：你可以根据自己的需求修改脚本文件，例如更改映像文件的路径或 QEMU 的启动参数。

## 贡献者指南
欢迎贡献！如果你有任何改进或修复，请提交 Pull Request 或 Issue 到本项目仓库。

## 许可证
本项目遵循 MIT License，请参阅 LICENSE 文件以获取更多信息。
