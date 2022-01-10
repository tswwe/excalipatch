# 背景

[Obsidian-excalidraw-plugin](https://github.com/zsviczian/obsidian-excalidraw-plugin)是一个将功能强大的绘图工具 [Excalidraw](https://excalidraw.com) 引入 Obsidian 的插件。但由于 Obsidian 插件系统和 Excalidraw 的限制，用户在使用文本工具时，无法将文本的字体修改为本地字体。这导致插件只能调用系统默认字体来显示非ASCII字符，与插件内置的英文手写字体风格不搭。

这个问题目前还没有完美的解决方案，Obsidian-excalidraw-plugin 插件的作者（[@zsviczian](https://github.com/zsviczian)）正在努力解决这个问题，并已经提出了一种[过渡方案](https://github.com/zsviczian/obsidian-excalidraw-plugin/issues/14#issuecomment-979460183)；本工具（Excalipatch）则尝试提供另一种备选方案，大概思路是：将用户的本地字体文件嵌入 Obsidian-excalidraw-plugin 的源代码（`main.js`）中，并添加一个文本按钮来使用这个字体。

Excalipatch 的主要功能：

* 在 Obsidian-excalidraw-plugin 中添加一个新的文本工具按钮，该按钮使用用户指定的本地字体文件
* 修改 Obsidian-excalidraw-plugin 的界面语言

![preview](./assets/preview.jpg)

# 安装方法

Excalipatch 是一个便携小程序，不需要安装，只要到[发行版页面](https://github.com/tswwe/excalipatch/releases)下载 `excalipatch.exe` 即可。

当然，如果想要使用它，你需要先安装最新版本的 Obsidian（0.12.16+） 和 Obsidian-excalidraw-plugin（1.5.15+）。此外，还需要自己准备一个字体文件（上图示例中所用字体是“沐瑶软笔手写体”）。

# 使用说明

## 使用步骤

1. 退出 Obsidian。
2. 把 `excalipatch.exe` 和字体文件（支持 ttf/otf/woff/woff2 格式）放在 `main.js` （通常位于 `你的仓库\.obsidian\plugins\obsidian-excalidraw-plugin\main.js`）同一目录下，直接运行 `excalipatch.exe`，成功运行后可得到修补后的 `main.js.patched` 文件。
> 也可以通过命令行运行 Excalipatch，支持更多参数，例如：`excalipatch.exe lang="zh-CN" button="按钮名称" font="xxx.ttf" icon="yyy.svg"`。每个参数都是可选的。
3. 备份原来的 `main.js`，再将修补后的 `main.js.patched` 重命名为 `main.js`。
4. 重启 Obsidian。如果出现错误提示，说明补丁失效，请退出 Obsidian 并还原原来的 `main.js`。

## 注意事项

尽管 Excalidraw 易于使用，但你需要清楚以下几点：

* 这只是一个临时的应对方案，而不是最终的解决方案。
* 该方案不具有持久性。每次 Obsidian-excalidraw-plugin 升级都会导致 `main.js` 被还原，需要重新应用一次补丁。
* 该方案不保证可靠性。Excalipatch 通过识别 `main.js` 中的某些特征来对其进行修补，一旦源代码发生较大改动，可能会导致修补失败。如果发生这种情况，请提 Issue 或 PR。
* Excalipatch 目前只能在 Windows 系统中使用，尽管生成的 `main.js` 可能是跨平台的。
* 重要：请备份好最初的 `main.js`。如果你发现 Obsidian-excalidraw-plugin 不能正常工作，请第一时间恢复 `main.js`，以确认是否由本工具造成。如果你没有备份，也可以直接升级或重装 Obsidian-excalidraw-plugin 。

# 如何贡献

* 如果软件在使用过程中报错，请[提 Issue](https://github.com/tswwe/excalipatch/issues)，并附上错误信息截图和相关文件（通常包括 `main.js`，`manifest.json`）。
* 如果你想参与代码的开发，请 fork 并克隆本仓库到本地，仓库中的 `project` 目录包含了项目所有的工程文件，是用 [aardio](https://ide.update.aardio.com/releases/aardio.7z) 编写的。修改完成后，欢迎提 PR。

