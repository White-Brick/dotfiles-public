# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 代码库概述

这是一个个人dotfiles配置仓库，包含多平台开发环境的配置文件：

- **Neovim配置** (.config/nvim/): 基于LazyVim的现代Neovim配置，包含TypeScript、Rust、Tailwind等语言支持
- **Tmux配置** (.config/tmux/): 终端复用器配置，使用C-t作为前缀键
- **Fish Shell配置** (.config/fish/): 跨平台shell配置，包含macOS、Linux特定配置
- **Git配置** (.gitconfig): 包含大量有用的git别名和工具集成
- **Lazygit配置** (.config/lazygit/): Git TUI工具配置，集成了commitizen

## 架构特点

### 跨平台配置系统
- Fish shell根据系统类型(`uname`)加载对应的配置文件:
  - config-osx.fish (macOS)  
  - config-linux.fish (Linux)
- 支持本地配置覆盖(config-local.fish)

### Neovim插件系统
- 使用LazyVim作为基础配置框架
- 自动下载和管理Lazy.nvim插件管理器
- 插件配置模块化，分为不同类别(editor, ui, coding, lsp等)
- 开发插件路径设置为~/.ghq/github.com

### Tmux配置架构
- 主配置文件导入多个专门配置:
  - theme.conf: 主题配置
  - statusline.conf: 状态栏配置  
  - utility.conf: 实用功能
  - macos.conf: macOS特定配置
- 使用TPM(Tmux Plugin Manager)管理插件

## 常用别名和快捷键

### Fish Shell别名
- `g` = git
- `c` = claude  
- `claude-yolo` = claude --dangerously-skip-permissions
- `vim` = nvim (如果nvim可用)

### Git别名
- `git ps` = push到当前分支
- `git pl` = pull当前分支  
- `git hist` = 图形化历史日志
- `git a` = 交互式添加文件(使用peco)
- `git df` = 交互式diff选择(使用peco)

### Tmux快捷键
- 前缀键: `C-t`
- `r`: 重新加载配置
- `o`: 在Finder中打开当前目录
- `e`: 关闭其他面板

## 开发工具集成

### 编辑器配置
- 默认编辑器设置为nvim
- Git diff/merge工具配置为nvimdiff
- VSCode风格的调试配置可选

### 版本控制
- 集成了hub/gh CLI工具
- 配置了commitizen用于规范化提交信息
- Lazygit自定义快捷键C用于commitizen提交

### 包管理器和环境
- 支持ghq进行Git仓库统一管理(~/.ghq)
- Node.js项目本地bin目录自动添加到PATH
- Go工作区设置($GOPATH/bin添加到PATH)

## 配置文件位置

所有配置文件位于`.config/`目录下，遵循XDG Base Directory规范。主要配置文件包括:

- Neovim: `.config/nvim/`
- Tmux: `.config/tmux/` 
- Fish: `.config/fish/`
- Lazygit: `.config/lazygit/`

## 注意事项

这些配置文件针对作者的个人开发工作流进行了优化，直接使用前请仔细了解各项设置的含义。特别注意：

- Tmux前缀键被改为C-t而非默认的C-b
- 包含了大量个人化的别名和快捷键
- Neovim配置假设安装了特定的字体和终端支持

- 希望你使用中文进行对话