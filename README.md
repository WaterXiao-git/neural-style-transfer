# Fast Neural Style Transfer — 快速图像风格迁移

> **实时图像风格迁移**，基于感知损失（Perceptual Losses）的前馈式 Transformer 网络。
> 论文：[Perceptual Losses for Real-Time Style Transfer and Super-Resolution](https://arxiv.org/abs/1603.08155) (Johnson et al., ECCV 2016)

---

## 📋 成果 | Results

| 风格 | 内容权重 | 风格权重 | 效果 |
|------|---------|---------|------|
| 星空（Van Gogh） | 10 | 100 | 经典风格迁移 |
| 各种艺术风格 | 10 | 100 | 实时高清输出 |

## 💡 模型架构 | Model Architecture

```
Input (3×H×W) → Conv3→32(9×9) → IN + ReLU
  → DownBlock (32→64, stride=2)
  → DownBlock (64→128, stride=2)
  → ResidualBlock(128) × 5
  → UpBlock (128→64, nearest+conv)
  → UpBlock (64→32, nearest+conv)
  → Conv32→3(9×9) + Sigmoid → Output
```

## 🚀 快速开始 | Quick Start

```bash
pip install -r requirements.txt

# 训练
python train.py --dataset_path ./data --style_image ./styles/starry_night.jpg

# 推理
python stylize.py --model ./checkpoints/model.pth --input ./input.jpg --output ./output.jpg
```

## 📁 项目结构 | Project Structure

```
├── config.py           # 训练配置
├── model.py            # ImageTransformer 网络
├── train.py            # 训练循环
├── stylize.py          # 推理
├── vgg.py              # VGG19 特征提取器
├── image_utils.py      # 图像处理工具
└── requirements.txt
```

## 📄 许可证 | License

MIT
