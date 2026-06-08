# Universal Robots UR16e Description (MJCF)

> 需要 MuJoCo 2.3.3 或更高版本。

## 概述

本目录包含 **UR16e** 的 MuJoCo MJCF 模型，用于仿真与可视化。

- **实际控制**：请使用 `ur16e.urdf` 配合 ROS / MoveIt。
- **本 MJCF**：主要用于 MuJoCo viewer 中检查 mesh 与关节对齐；惯性、阻尼、碰撞几何仍 largely 继承自 [MuJoCo Menagerie UR10e](https://github.com/google-deepmind/mujoco_menagerie) 模板，未针对 UR16e 重新标定。

### 来源与修改

1. 骨架与 wrist / base / shoulder mesh：源自 Menagerie **UR10e** MJCF。
2. `upperarm_0..3.obj`、`forearm_0..3.obj`：由 UR16e 源 mesh 重建并导出。
3. `ur16e.xml` 中若干 `body pos` 经手动微调，使视觉 mesh 与关节转轴在 viewer 中对齐（肩、肘、腕 1 等处）。

### 目录结构

```
ur16e_mjcf/
├── scene.xml      # 带地面与灯光；viewer 入口
├── ur16e.xml      # 机器人本体
├── assets/        # OBJ（及导出附带的 MTL）
├── LICENSE
├── CHANGELOG.md
└── ASSETS_README.md
```

上级目录另有 `ur16e.urdf`（ROS / MoveIt 用）。

## 使用方法

在 `ur16e_mjcf` 目录下：

```bash
python -m mujoco.viewer --mjcf=scene.xml
```

或：

```python
import mujoco
import mujoco.viewer as v

m = mujoco.MjModel.from_xml_path("scene.xml")
d = mujoco.MjData(m)
v.launch(m, d)
```

## 说明

- 近距离观察个别关节仍可能有亚毫米级视觉误差；对 FoldArms 项目以 ROS 控制为主，一般可接受。
- Menagerie 原 UR10e 说明中提到的 integrator / 与其他模型组合时的稳定性建议，对本模型仍大致适用（当前使用 `implicitfast` integrator）。

## 许可证

见 [LICENSE](./LICENSE)。本模型衍生自 Menagerie UR10e（BSD-3-Clause），并包含 UR16e 相关的 mesh 与 XML 修改。
