# GreenSegNet and GreenSegNet-A

Official PyTorch implementation of the following papers:

"[GreenSegNet: A Novel Deep Learning Architecture for Urban Vegetation Segmentation From MLS Data](https://doi.org/10.1109/TGRS.2024.3454990)" (IEEE TGRS), and

"[Advancing vegetation segmentation from ALS point clouds: From benchmarking to GreenSegNet-A](https://doi.org/10.1016/j.srs.2026.100382)" (SRS)

## Setup
- Clone repository 
```
git clone https://github.com/Connect2Aditya/GreenSegNet-A.git
cd GreenSegNet-A
```
- Install packages with a setup file
```
bash install.sh
```
- Dataset

```
mkdir -p data/S3DIS/
cd data/S3DIS
gdown https://drive.google.com/uc?id=1MX3ZCnwqyRztG1vFRiHkKTz68ZJeHS4Y
tar -xvf s3disfull.tar
cd ../../
```

## Run Experiments

### MLS Point Clouds: GreenSegNet (S3DIS format) 
- Train
```
CUDA_VISIBLE_DEVICES='0' python examples/segmentation/main.py  --cfg cfgs/s3dis/greensegnet.yaml
```
- Inference
```
CUDA_VISIBLE_DEVICES='0' python examples/segmentation/main.py  --cfg cfgs/s3dis/greensegnet.yaml  mode=test --pretrained_path ckpt/S3DIS/ckpt_best.pth
```

### ALS Point Clouds: GreenSegNet-A (S3DIS format) 
- Train
```
CUDA_VISIBLE_DEVICES='0' python examples/segmentation/main.py  --cfg cfgs/s3dis/greensegnet-a.yaml
```
- Inference
```
CUDA_VISIBLE_DEVICES='0' python examples/segmentation/main.py  --cfg cfgs/s3dis/greensegnet-a.yaml  mode=test --pretrained_path ckpt/S3DIS/ckpt_best.pth
```

## Acknowledgement
This repo is built upon [OpenPoints](https://github.com/guochengqian/openpoints) and [PointNeXt](https://github.com/guochengqian/PointNeXt). 
Please refer the [related article](https://arxiv.org/abs/2206.04670).

## Citation
Please cite our work as:
```tex
@article{10666736,
  title={GreenSegNet: A Novel Deep Learning Architecture for Urban Vegetation Segmentation From MLS Data}, 
  author={Aditya, Aditya and Lohani, Bharat and Aryal, Jagannath and Winter, Stephan},
  journal={IEEE Transactions on Geoscience and Remote Sensing}, 
  year={2024},
  volume={62},
  number={},
  pages={1-10},
  doi={10.1109/TGRS.2024.3454990}
}

@article{ADITYA2026100382,
title = {Advancing vegetation segmentation from ALS point clouds: From benchmarking to GreenSegNet-A},
author = {Aditya Aditya and Bharat Lohani and Jagannath Aryal and Stephan Winter},
journal = {Science of Remote Sensing},
volume = {13},
pages = {100382},
year = {2026},
doi = {https://doi.org/10.1016/j.srs.2026.100382}
}
```
