# 圆明园四十景图

`yuanmingyuan-forty-scenes` 是一个 Codex Skill，用于把 SketchUp（SU）古建筑截图转换为《圆明园四十景图》式清代宫廷界画山水复原图。

Skill 以 SU 截图作为建筑几何依据，以可选色块作为地形、水体提示，并使用仓库内置的原作画页参考控制界画线性、山水构图、绢本底色和建筑设色。

## 能做什么

- 尽量保留建筑数量、相对位置、朝向、屋顶、院墙、台地和连廊关系；
- 把白底 SU 场景补全为圆明园四十景图式山水环境；
- 支持在同一张 SU 截图上直接添加近似地形色块；
- 默认生成 A「现状设色版」和 B「历史校色版」；
- B 版降低现代建模颜色的饱和度，使用旧朱、灰石青、灰石绿、灰青瓦和温灰白墙。

## 使用条件

- 支持 Skills 的 Codex；
- 可使用内置图像生成/编辑能力；
- 能访问本仓库以下载安装。

Skill 提供的是图像生成工作流，不读取 `.skp` 文件中的原生三维几何。请先从 SketchUp 导出 PNG 截图。

## 安装

### 让 Codex 自动安装

把下面这段话直接发给 Codex：

```text
请安装这个 Codex Skill：
https://github.com/zxn0523-boop/Yuanmingyuan

仓库根目录就是 Skill，安装名使用 yuanmingyuan-forty-scenes。
```

安装完成后，从下一轮开始使用 `$yuanmingyuan-forty-scenes`。

如果安装器要求提供仓库内路径，使用：

```text
repo: zxn0523-boop/Yuanmingyuan
path: .
name: yuanmingyuan-forty-scenes
```

### 手动克隆

macOS / Linux：

```bash
git clone https://github.com/zxn0523-boop/Yuanmingyuan.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/yuanmingyuan-forty-scenes"
```

Windows PowerShell：

```powershell
$codexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME '.codex' }
git clone https://github.com/zxn0523-boop/Yuanmingyuan.git `
  (Join-Path $codexRoot 'skills\yuanmingyuan-forty-scenes')
```

## 最快使用方法

上传一张 SU 截图，然后发送：

```text
使用 $yuanmingyuan-forty-scenes 处理这张 SU 古建筑截图。
尽量保持建筑布局和地形范围，生成 A 现状设色版和 B 历史校色版。
```

未特别说明时，Skill 默认使用原图画幅、春夏之交、无人物、无船、无题签、无印章，只输出画心。

## SU 截图建议

- 使用平行投影，建议约 35°–50° 俯视角；
- 建筑完整入画，不要裁掉屋顶或院墙；
- 关闭坐标轴、辅助线、选中框、阴影和天空渐变；
- 使用 PNG，保持建筑边线清楚；
- 接近原作画心可使用正方形或 4:3，需要横幅时可保留原图比例。

只有一张带色块的截图也可以使用，不要求额外制作蒙版。

## 单图地形标注

直接在 SU 截图上覆盖大面积、连续、半透明的平涂色块。建筑应保持可见，避免使用零碎点状笔刷。

- 绿色 `#39B54A`：平地、一般陆地、低缓坡；
- 红色 `#ED1C24`：山体、隆起地形、假山；
- 蓝色 `#29ABE2`：水体；
- 黄色 `#D9A441`：未细分的通用地形，兼容旧流程。

绿色和红色共同构成陆地地形范围。色块只控制大致范围、位置和高低趋势，最终画面允许为自然衔接适度柔化边界，不要求像素级复刻。

单图模式只把大面积、连续、低纹理的平涂色域识别为标注；建筑自身的红柱、青绿彩画或蓝色构件不会被当成地形标记。

若所有色块都只表示普通地形，请在请求中明确写：

```text
所有标注色块均表示地形，不按颜色区分水体或高地。
```

## 双版本输出

### A｜现状设色版

完成建筑和山水入画，同时保留 SU 模型中红、青绿、灰瓦等颜色的相对关系和辨识度。

### B｜历史校色版

以 A 版为唯一编辑目标，只校准建筑、院墙和台基的颜色：

- 鲜红转为低饱和、偏赭的旧朱色；
- 亮青绿转为灰石青、灰石绿和黛青绿；
- 近黑瓦转为灰青、灰褐和墨灰；
- 水泥灰墙体和台基转为温灰白、浅灰褐。

A、B 两版的建筑结构、地形、树木、道路和构图应尽可能一致，主要差异集中在建筑设色。

## 推荐调用示例

```text
使用 $yuanmingyuan-forty-scenes 转换这张 SU 截图。

绿色是平地，红色是山体，蓝色是水体。色块只表示近似范围，不要求像素级还原。
建筑结构和台地轮廓优先，未标注区域只做克制补全。
输出 A 现状设色版和 B 历史校色版，不要人物、船、题签和印章。
```

## 稳定性与限制

- Skill 能稳定约束整体风格方向和工作流程，但图像生成具有随机性，不保证每次像素完全相同；
- 单张视角不能提供被遮挡建筑和精确高程，地形与构件不属于测绘级复原；
- 输入视角、分辨率和色块清晰度越统一，建筑与地形保持通常越稳定；
- 论文、考古或逐构件核验用途，建议保留 SU 线稿作为最终叠线，或使用额外线稿、深度约束流程。

## 仓库结构

```text
SKILL.md                    Skill 主入口
agents/openai.yaml          Codex 显示名称与默认调用提示
assets/reference-plates/    原作画心风格参考
references/                 输入、地形、风格、参考选择与提示词规范
```

更详细的执行规则见 [SKILL.md](SKILL.md)。
