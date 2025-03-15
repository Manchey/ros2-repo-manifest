# ROS2 Repo Manifest & VCS Converter
# ROS2 Repo 清单与 VCS 转换工具

[English](#english) | [中文](#chinese)

<a name="english"></a>
## English

### Introduction
This repository serves two purposes:
1. Provides official ROS2 Repo manifest files for repository management
2. Includes tools to convert from VCS-style repository configuration to Repo manifest

### Using ROS2 Repo Manifest

#### Initialize ROS2 Workspace
```bash
# Create and enter workspace directory
mkdir -p ros2_ws
cd ros2_ws

# Initialize repo with manifest
#   You can specify which manifest file to use during initialization with the `-m` parameter:
#   If no manifest file is specified with `-m`, repo will use `default.xml` by default.
# For ROS2 Rolling (default)
# repo init -u https://github.com/yourusername/ros2-repo-manifest -b master -m default.xml
# For ROS2 Humble
# repo init -u https://github.com/yourusername/ros2-repo-manifest -b master -m humble.xml
# For ROS2 Iron
# repo init -u https://github.com/yourusername/ros2-repo-manifest -b master -m iron.xml
repo init -u https://github.com/Manchey/ros2-repo-manifest -b master
repo sync -j8

# The above commands will clone all ROS2 repositories
```

#### Common Repo Commands
```bash
# Update all repositories
repo sync

# Create a new branch across repositories
repo start feature_branch --all

# View status of all repositories
repo status

# See detailed help
repo help
```

### VCS to Manifest Converter
If you want to convert your existing VCS repository configuration to Repo manifest format, you can use the included converter tool.

#### Prerequisites
- Python 3.6+
- PyYAML

#### Converting VCS to Manifest
```bash
# Install dependencies
pip install pyyaml

# Convert repos file
./tools/vcs_to_manifest.py input.repos -o output.xml

# Convert with base path (similar to 'vcs import src')
./tools/vcs_to_manifest.py input.repos -o output.xml -p src
```

The `-p/--path` option allows you to specify a base path that will be prepended to all repository paths in the manifest. For example, if you specify `-p src`, a repository that would normally be placed in `ros2/rclcpp` will instead be placed in `src/ros2/rclcpp`.

### Repository Structure

### Features
- Converts VCS repository configurations to Repo manifest format
- Preserves repository paths and branch information
- Supports custom remote configurations
- Generates properly formatted XML output
- Includes error handling and command line arguments

### License
MIT License

---

<a name="chinese"></a>
## 中文

### 简介
该仓库具有两个主要用途：
1. 提供 ROS2 的官方 Repo 清单文件用于仓库管理
2. 包含从 VCS 格式转换到 Repo 清单格式的工具

### 使用 ROS2 Repo 清单

#### 初始化 ROS2 工作空间
```bash
# 创建并进入工作空间目录
mkdir -p ros2_ws
cd ros2_ws

# 使用清单初始化 repo
#
# 您可以在初始化时通过 `-m` 参数指定要使用的清单文件：
#
# 使用 ROS2 Rolling 版本（默认）
# repo init -u https://github.com/yourusername/ros2-repo-manifest -b master -m default.xml
# 
# # 使用 ROS2 Humble 版本
# repo init -u https://github.com/yourusername/ros2-repo-manifest -b master -m humble.xml
# 
# # 使用 ROS2 Iron 版本
# repo init -u https://github.com/yourusername/ros2-repo-manifest -b master -m iron.xml
#
# 如果不使用 `-m` 参数指定清单文件，repo 将默认使用 `default.xml`。
repo init -u https://github.com/Manchey/ros2-repo-manifest -b master
repo sync -j8

# 上述命令将克隆所有 ROS2 仓库
```

#### 常用 Repo 命令
```bash
# 更新所有仓库
repo sync

# 在所有仓库中创建新分支
repo start feature_branch --all

# 查看所有仓库状态
repo status

# 查看详细帮助
repo help
```

### VCS 转 Manifest 转换工具
如果您想将现有的 VCS 仓库配置转换为 Repo 清单格式，可以使用包含的转换工具。

#### 环境要求
- Python 3.6+
- PyYAML

#### 转换方法
```bash
# 安装依赖
pip install pyyaml

# 转换 repos 文件
./tools/vcs_to_manifest.py input.repos -o output.xml

# 指定基础路径进行转换（类似于 'vcs import src'）
./tools/vcs_to_manifest.py input.repos -o output.xml -p src
```

`-p/--path` 选项允许您指定一个基础路径，这个路径会被添加到清单文件中所有仓库路径的前面。例如，如果您指定 `-p src`，原本应该放在 `ros2/rclcpp` 的仓库将会被放置在 `src/ros2/rclcpp`。

### 仓库结构

### 功能特点
- 将 VCS 仓库配置转换为 Repo 清单格式
- 保留仓库路径和分支信息
- 支持自定义远程仓库配置
- 生成格式规范的 XML 输出
- 包含错误处理和命令行参数支持

### 许可证
MIT 许可证

---

## Contributing | 贡献
We welcome contributions! Feel free to:
- Submit bug reports or feature requests through issues
- Propose improvements through pull requests
- Share your experience or questions in discussions

欢迎贡献！您可以：
- 通过 issues 提交错误报告或功能请求
- 通过 pull requests 提出改进建议
- 在讨论区分享您的经验或提问

## Contact | 联系方式
- Email | 邮箱: ljq0831@qq.com
- GitHub: [@Manchey](https://github.com/Manchey)
