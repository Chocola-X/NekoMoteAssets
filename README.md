# NekoMote Assets

NekoMote 动态壁纸引擎的资产包。包含角色模型、背景图片与 UI 图标，供 [NekoMote](https://github.com/Chocola-X/NekoMote) 播放器或 Plasma 壁纸插件加载使用。

## 内容

- **角色模型** — 8 个角色组，每组含多个型号变体
- **背景** — 静态 PNG 背景与分时段动态背景（白天/黄昏/夜晚三相）
- **图标** — UI 控制面板图标

## 目录结构

```
assets/
├── characters/
│   ├── characters.json               # 角色显示名字典
│   └── <角色组>/                     # 如 chocola、azuki、fraise …
│       └── <变体>/                   # 如 date-a、maid-a
│           ├── model.nkm.json        # 规范化模型（schema 6）
│           ├── session.nks.json      # 反应会话（视线/触摸/动作）
│           ├── meta.json             # 可选：显示名、排序、裁切等
│           └── textures/             # PNG 纹理图集
├── backgrounds/
│   ├── background.json               # 静态背景显示名字典
│   ├── BG_*.png                      # 静态背景
│   └── dynamic/
│       ├── background.json           # 动态背景显示名字典
│       └── <组名>/                   # 如 BG_01
│           ├── config.json           # 各相图片与切换时间
│           ├── A.png                 # 白天相
│           ├── B.png                 # 黄昏相
│           └── C.png                 # 夜晚相
└── icons/
    └── toggle.png                    # UI 面板图标
```

> `config.json`（壁纸运行配置）不包含在本仓库中，它由 NekoMote 首次运行时自动生成。

## 使用方法

### 配合播放器

将本仓库内容放入 NekoMote 的 `assets/` 目录，然后启动播放器：

```bash
nekomote_player --assets /path/to/assets --character chocola/date-a
```

### 配合 Plasma 壁纸

安装 NekoMote Plasma 插件后，在壁纸配置中将 assets 目录指向本仓库的路径即可。

### 角色名格式

角色名采用 `组/变体` 格式，例如 `chocola/date-a`、`fraise/maid-a`。完整列表见 `characters/characters.json`。

## 资产来源

- **角色模型与背景图片** — 原始素材来自 NEKOPARA Steam 版游戏，使用 [FreeMote](https://github.com/UlyssesWu/FreeMote) 工具解包，再经 NekoMote 资产导入器（`nekomote_import`）规范化为引擎格式（schema 6 模型 `model.nkm.json`）。
- **动作反应会话**（`session.nks.json`，含视线/触摸/动作）— 由本仓库维护者自行配置，非游戏原始数据。

如需从原始素材重新生成模型与背景，参见 [NekoMote 主仓库](https://github.com/Chocola-X/NekoMote) 的「资产准备」章节。

## 许可证

本仓库采用 [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/) 协议，见 [LICENSE](LICENSE)。

即：允许以非商业目的使用、修改与分发，但须署名原素材来源，并以相同协议发布衍生作品。许可依据 [FreeMote](https://github.com/UlyssesWu/FreeMote) 使用条款。
