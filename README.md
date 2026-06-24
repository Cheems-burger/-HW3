# 基于 3DGS 与 AIGC 的多源资产生成与真实场景融合
## 项目简介
本实验使用 3D Gaussian Splatting (3DGS) 对真实物体（奶龙）进行多视角重建，并利用 COLMAP 提取相机位姿。同时，使用 threestudio 框架生成文本到3D（花瓶）和单图到3D（猫咪杯）资产，并尝试与 Mip-NeRF 360 背景场景融合。

## 
- 物体A（毛绒玩偶）：手机拍摄 → COLMAP 位姿 → 3DGS 训练 → 渲染
- 背景场景：Mip-NeRF 360 garden → 3DGS 训练 → 渲染

## 环境配置
```bash
conda env create -f environment.yml   # 3DGS 官方环境
conda activate gs

## 数据准备
物体A：手机拍摄 70+ 张环绕照片，缩放到 1200px
背景：从 Mip-NeRF 360 下载 garden 场景
##训练命令
cd gaussian-splatting
python train.py -s /path/to/data --iterations 30000
