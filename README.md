#  Background

The [obsidian-excalidraw-plugin](https://github.com/zsviczian/obsidian-excalidraw-plugin) integrates [Excalidraw](https://excalidraw.com), a feature rich sketching tool, into Obsidian. However, because of the limitation of Obsidian plugin system and Excalidraw, it is difficult for users to customize the Text Tool's font family to a local font. As a result, some non-ASCII charactors (e.g., Chinese charactors) is displayed in system default font family style, which doesn't match the style of the integrated ASCII handwriting fonts.

Although there is not a perfect solution yet, the owner of obsidian-excalidraw-plugin [@zsviczian](https://github.com/zsviczian) is working on this problem and has put forward a [workaround](https://github.com/zsviczian/obsidian-excalidraw-plugin/issues/14#issuecomment-979460183); And the purpose of this tool, Excalipatch, is to provide another workaround as a second choice. In breif, Excalipatch embeds a user-specific local font into `main.js`, the source code of obsidian-excalidraw-plugin, and adds a new Text button to use the font.

Here are the key features of Excalipatch:

* Add a new Text Tool button with a user-specific local font into Obsidian-excalidraw-plugin
* Set the UI language of Obsidian-excalidraw-plugin

![preview](./assets/preview.jpg)

# Install

Excalipatch doesn't need to install. It's a portable tiny tool on Windows OS (at least XP). Just download `excalipatch.exe` from [Releases](https://github.com/tswwe/excalipatch/releases) page.

Though to use it, you must have Obsidian and Obsidian-excalidraw-plugin installed. A local font file is also needed (The font used in the demo is "Muyao-Softbrush").

# Usage

## Step by step

1. Close Obsidian.
2. Put `excalipatch.exe` and local font file (ttf/otf/woff/woff2 format) under the same folder with `main.js` (usually located in `YourValut\.obsidian\plugins\obsidian-excalidraw-plugin\main.js`). Run `excalipatch.exe` directly and you can get the patched `main.js.patched` file if things go well.
> You can also run `excalipatch.exe` by command line, which supports more arguments. For example, `excalipatch.exe lang="en" button="button name" font="xxx.ttf" icon="yyy.svg"`. Each argument is optional.
3. Backup the origin `main.js`, then replace it with the patched file.
4. Open Obsidian. If an error message occurs, please close Obsidian and restore the backup `main.js`.

## Attention

Although Excalidraw is easy to use, you must keep in mind that:

* This is just a workaround, NOT a full solution.
* This is NOT permanent. Every time when Obsidian-excalidraw-plugin updates, the `main.js` will be restored and need to be patched again.
* This is NOT robust. Excalipatch hacks the code of `main.js` by identifying its patterns. Thus, if the code makes big changes, Excalipatch may fail on recognizing. In that case, please [open an issue](https://github.com/tswwe/excalipatch/issues) or submit PRs.
* Excalipatch only supports Windows OS currently, though the patched `main.js` file is cross-platform.
* REMEMBER: Backup the origin `main.js` file. If you find anything wrong with your obsidian-excalidraw-plugin, please restore `main.js` first to check if it is caused by Excalipatch. If you don't have a backup, you can also update/reinstall Obsidian-excalidraw-plugin. 
