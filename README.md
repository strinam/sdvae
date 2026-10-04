# SDVAE 实验代码索引

这是从研究工作区整理出的 SDVAE（Score-Divergence VAE）核心实验代码。内容按论文实验章节归类，只保留用于复现实验的 Jupyter notebook；缓存、备份、论文源文件、对比方法的重复 notebook 和 notebook 生成脚本均未纳入。整理后的 `results/` 保留日志、JSON、PNG 和汇总表，模型权重文件（`.pt` / `.pth`）已排除。

Notebook 内已有的运行输出、图表和执行记录均保留，便于老师直接查看结果。

## 代码索引

| 目录 | 对应论文实验 | 内容 |
| --- | --- | --- |
| [`01_mlp_main`](notebooks/01_mlp_main) | 主实验 / 五个公开数据集 | MLP backbone 下的 VAE、IWAE、SDVAE 训练与评估 |
| [`02_medvae_main`](notebooks/02_medvae_main) | MedVAE backbone 主实验 | 五个数据集上的 MedVAE 重构实验；每个 notebook 比较 VAE / SDVAE / IWAE，并附重构图生成 notebook |
| [`03_prior_sensitivity`](notebooks/03_prior_sensitivity) | Hyperparameters / prior sensitivity | 五个数据集上不同 prior variance 的 SDVAE 与 VAE 实验 |
| [`04_post_amortization_refinement`](notebooks/04_post_amortization_refinement) | Post-amortization iterative refinement | 代表性数据集上 VAE/SDVAE 初始化后的 BaM 迭代 refinement 及汇总图 |
| [`05_variance_and_ablation`](notebooks/05_variance_and_ablation) | Variance Reduction / Ablation | control variates、学习率和组件消融的曲线汇总 |
| [`06_cardiac_application`](notebooks/06_cardiac_application) | Semi-supervised cardiac segmentation | ACDC 的 MedVAE baseline、MedVAE-SD 和分割数据划分流程 |

## 运行说明

每个 notebook 都保留了原实验的完整代码单元和运行输出。运行前请先修改配置单元中的数据路径、checkpoint 路径和 GPU 编号，再按顺序执行。代码面向 Linux + CUDA 环境，常用依赖包括 PyTorch、torchvision、Hugging Face datasets、JAX、LPIPS、torchmetrics 和 matplotlib。

notebook 中仍可能出现原实验服务器路径（例如 `/home/yzm/...`），这些路径是数据与 checkpoint 的配置项，需要按运行环境替换。仓库不包含数据集、预训练权重或原始 TensorBoard 日志。

## 目录结构

```text
sdvae/
├── README.md
├── results/
│   ├── results_medvae_0702/
│   ├── results_medvae_0705/
│   ├── results_medvae_0706/
│   └── zuixin.xlsx
└── notebooks/
    ├── 01_mlp_main/
    ├── 02_medvae_main/
    ├── 03_prior_sensitivity/
    ├── 04_post_amortization_refinement/
    ├── 05_variance_and_ablation/
    └── 06_cardiac_application/
```
