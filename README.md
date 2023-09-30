
# **[Pyramid-VAE-GAN](https://link.springer.com/article/10.1007/s41095-022-0331-3)**

![Graphical_Abstract.jpg](https://github.com/thy960112/Pyramid-VAE-GAN/blob/main/figures/Graphical_Abstract.jpg)

**Pyramid-VAE-GAN: Transferring Hierarchical Latent Variables for Image Inpainting**

Huiyuan Tian, Li Zhang, Shijian Li, Min Yao and Gang Pan

## Introduction

Our contributions made in this paper are summarized as follows:

- To the best of our knowledge, the Pyramid-VAE backbone is used in the domain of image inpainting firstly. Our model augments the details of generated pictures by pyramid structure while improving rationality of structure via VAE.
- We propose a latent variable transfer module for the first time. The long-term correlations in high-level latent variables can be transferred to low-level latent variables with more details, thus it is capable of generating both visually and semantically convincing images.
- Our VAE-GAN hybrid model improves the robustness of the training process and enhances the sharpness of the generated images.

## Example Results

![facade.jpg](https://github.com/thy960112/Pyramid-VAE-GAN/blob/main/figures/facade.jpg)
![dtd.jpg](https://github.com/thy960112/Pyramid-VAE-GAN/blob/main/figures/dtd.jpg)
![celebahq.jpg](https://github.com/thy960112/Pyramid-VAE-GAN/blob/main/figures/celebahq.jpg)

## Run

Our work is mainly based on [PEN-Net-for-Inpainting](https://github.com/researchmm/PEN-Net-for-Inpainting).

1. Environments:
	1. Install python3.6
	2. Install PyTorch (tested on Release 1.7.1)
2. Preparation
	1. [Download](https://pan.baidu.com/s/1mD3jY49bNn3DK5ah6--fRA?pwd=k68x) training/valid/test images file lists and put them into `flist` folder
	2. Download datasets and put them into `datazip` folder
	3. Keep `flist`, `datazip` and `Pyramid-VAE-GAN` folder in the same level directory
3. Training: For different datasets, the following commands can be used for training respectively.

```Shell
# facade
python train.py -c configs/facade.json -n pvg_facade -m square -s 256
# dtd
python train.py -c configs/dtd.json -n pvg_dtd -m square -s 256
# celebahq 
python train.py -c configs/celebahq.json -n pvg_celebahq -m square -s 256
```

4. Testing: For different datasets, the following commands can be used for testing respectively.

```Shell
# facade
python test.py -c configs/facade.json -n pvg_facade -m square -s 256
# dtd
python test.py -c configs/dtd.json -n pvg_dtd -m square -s 256
# celebahq
python test.py -c configs/celebahq.json -n pvg_celebahq -m square -s 256
```

5. Evaluating:

```Shell
python eval.py --real_dir [ground truths] --fake_dir [inpainting results] --metric mae psnr ssim fid
```

## Pretrained Models

1. Download the pretrained models named `pvg_celebahq_celebahq_square256` for [CELEBA-HQ](https://pan.baidu.com/s/1g2uI1fY7w5s-EqR5NLACew?pwd=emc3) and put it under `release_model/`
2. [DTD](https://pan.baidu.com/s/1tyZUSZEejM425XtzLdpxxg?pwd=786p) and [Facade](https://pan.baidu.com/s/1t__JM61XaPRjB4mmHXgDGA?pwd=af4h) are similar.
