# SO(3)-Equivariant 3D Shape Generation with Latent VN-Diffusion and VN-Decoder

## 成员及contribution
成员: 杨子然, 王想, 王昱琛, 路涛玮

## Code Files

in code/
```
.
├── EFEM (来自follow的工作, 我没有修改其中的代码)
│   ├── ... (其他文件, 用不着)
│   ├── cache
│   │   └── mugs.npz (Autoencoder得到的 codebook, 这个是对应mugs类别的)
│   ├── lib_shape_prior
│   │   ├── configs (配置对应 setting的文件, 会自动load)
│   │   │   ├── chairs.yaml 
│   │   │   ├── kit4cates.yaml
│   │   │   └── mugs.yaml
│   │   └── core
│   │       └── ... (模型代码)
│   └── weights (对应Category的decoder的weights, 不大, 我直接放代码路径里了)
│       ├── chairs.pt
│       ├── kit4cates.pt
│       └── mugs.pt
├── README.md
├── ddpm.py (训练我们的 Latent space VN-diffusion, 其中用到了EFEM代码中涉及的一些模块, 具体见下)
├── dev_ckpt (放训练好的VN-diffusion的ckpt, 为了符合提交格式, 我放到了外面的ckpts里, 请copy回来)
│   └── (应该放一个model_epo399999.pt)
├── uncond_ddpm.ipynb (unconditional generation with DDPM model, 就是推理的代码, 按顺序执行即可)
└── viz_x.py (所有可视化相关的函数, 可视化点云, mesh, latent code的代码)

```
用到的EFEM的东西:
1. in ddpm.py, 设计VN-diffusion用到了EFEM中的VN-layer代码
   ```
   from EFEM.lib_shape_prior.vec_layers_out import VecLinearNormalizeActivate as VecLNA
   from EFEM.lib_shape_prior.vec_layers_out import VecLinear
   ```
2. in uncond_ddpm
   用到了EFEM开源的decoder, codebook. 

## Usage:
1. 请按照https://github.com/JiahuiLei/EFEM/tree/main中的installation安装环境

2. 训练VN-diffusion:
   python ddpm.py即可

3. 查看inference的结果:
   依次运行uncond_ddpm.ipynb即可
