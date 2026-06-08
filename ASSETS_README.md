# UR16e MJCF assets

`ur16e.xml` 通过 `<compiler meshdir="assets"/>` 加载本目录下的 mesh。

## 文件清单

| 前缀 | 数量 | 说明 |
|------|------|------|
| `base_*` | 2 | 自 Menagerie UR10e 复制 |
| `shoulder_*` | 3 | 自 Menagerie UR10e 复制 |
| `upperarm_*` | 4 | UR16e 重建 mesh |
| `forearm_*` | 4 | UR16e 重建 mesh |
| `wrist1_*` / `wrist2_*` / `wrist3` | 7 | 自 Menagerie UR10e 复制 |

## MTL 文件

- `material.mtl`：base / shoulder / wrist 的 OBJ 在导出时引用。
- `upperarm_*.mtl`、`forearm_*.mtl`：Rhino 导出大臂 / 前臂时附带。
- MuJoCo 中的颜色由 `ur16e.xml` 内 `<material>` 定义，**不依赖** MTL；保留 MTL 仅为与 OBJ 导出一致、避免部分工具读 OBJ 时报缺文件。

## 与 `ur16e.xml` 的手动对齐（参考）

以下 `body pos` 为视觉对齐后的值（单位：米，父 body 坐标系）：

| Body | pos |
|------|-----|
| `upper_arm_link` | `0 0.094 0` |
| `forearm_link` | `0 0.004 0.4714` |
| `wrist_1_link` | `0 -0.060 0.4234` |

修改 mesh 原点或替换 OBJ 后，通常需要重新微调上述偏移。
