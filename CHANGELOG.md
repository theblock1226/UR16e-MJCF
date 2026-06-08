# Changelog – Universal Robots UR16e Description (MJCF)

## [2026-06-08]

- 发布 UR16e MJCF：`ur16e.xml`、`scene.xml`、`assets/`。
- 大臂 / 前臂 mesh 替换为 UR16e OBJ；base / shoulder / wrist 沿用 Menagerie UR10e mesh。
- 手动调整 `upper_arm_link`、`forearm_link`、`wrist_1_link` 的 `body pos` 以改善关节处视觉对齐。
- `meshdir` 设为 `assets`；目录整理为独立 `ur16e_mjcf` 包。

## [2022-09-07]（上游 Menagerie UR10e）

- Menagerie UR10e MJCF 初始发布（本模型骨架与部分 mesh 之来源）。
