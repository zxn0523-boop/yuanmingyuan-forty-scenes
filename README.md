# 圆明园四十景图

`yuanmingyuan-forty-scenes` 是一个 Codex Skill，可以把 SketchUp（SU）古建筑截图转换为《圆明园四十景图》式清代宫廷界画山水复原图。

## 示例

此处是示例

## 30 秒上手

### 1. 安装

把下面这段话发给 Codex：

```text
请安装这个 Codex Skill：
https://github.com/zxn0523-boop/yuanmingyuan-forty-scenes

仓库根目录就是 Skill，安装名使用 yuanmingyuan-forty-scenes。
```

安装完成后，从下一轮开始使用。

### 2. 准备一张 SU 截图

最简单的输入只需要**一张 PNG 截图**：建筑完整、视角清楚即可，**平行投影！**

如果想告诉 Codex 哪里是地形，直接用PS在截图上涂一大片黄色：

- 黄色区域＝地形的大致范围；
- 黄色不需要固定色号，明显的黄色、土黄色或赭黄色都可以；
- 色块尽量连续、平整，建筑仍要清晰可见；
- 色块只控制大致地形，不要求最终画面逐像素一致。

没有黄色色块也能使用，Codex 会根据建筑关系谨慎补全环境。

需要区分更多类型时，可选用：绿色＝平地，红色＝山体，蓝色＝水体。进阶标注见下附“进阶说明”。

### 3. 上传截图并调用

发送一句话即可：

```text
使用 $yuanmingyuan-forty-scenes 处理这张图。
```

Skill 会理解建模与地形，并默认输出两版：

- **A｜现状设色版**：保留 SU 建筑颜色的相对关系；
- **B｜历史校色版**：把鲜艳建模色改为低饱和旧朱、灰石青、灰石绿、灰青瓦和温灰白墙。

## 截图这样导出更稳定

- 优先使用平行投影，建议约 35°–50° 俯视角；
- 建筑、屋顶、院墙和台地完整入画；
- 关闭坐标轴、辅助线、选中框、阴影和天空渐变；
- 使用 PNG，保持边线清楚；
- 正方形、4:3 或原有横幅都可以。

## Skill 会做什么

- 尽量保留建筑数量、位置、朝向、屋顶、院墙、台地和连廊关系；
- 根据黄色色块还原大致地形范围和坡体走势；
- 使用内置原作画页参考控制界画线、山水构图、绢本底色和建筑设色；
- 自动生成 A、B 两个配对版本。

## 使用限制

- 这是图像生成工作流，不能直接读取 `.skp` 文件，请先导出截图；
- 生成结果具有随机性，不保证每次像素完全相同；
- 单张截图无法提供被遮挡建筑和精确高程，不属于测绘级复原；
- 使用者的 Codex 需要具备 Skills 和图像生成/编辑能力。

## 进阶说明

需要更精细控制时再查看：

- [Skill 完整规则](SKILL.md)
- [SU 导出与标注规范](references/input-prep.md)
- [地形控制规则](references/terrain-control.md)
- [原作风格规范](references/style-spec.md)
- [提示词模板](references/prompt-template.md)

## 手动安装

macOS / Linux：

```bash
git clone https://github.com/zxn0523-boop/yuanmingyuan-forty-scenes.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/yuanmingyuan-forty-scenes"
```

Windows PowerShell：

```powershell
$codexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $HOME '.codex' }
git clone https://github.com/zxn0523-boop/yuanmingyuan-forty-scenes.git `
  (Join-Path $codexRoot 'skills\yuanmingyuan-forty-scenes')
```
