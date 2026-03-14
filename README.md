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
Alternatively, the environment can be set up using the file `gsn_env.yml`

- Dataset

```
mkdir -p data/S3DIS/s3disfull/raw
```
The processing of the data is in line with the S3DIS dataset.

Place point clouds in the directory `data/S3DIS/s3disfull/raw` in the `XXXX.npy` format. The traning-file names should start with `Area_1_XXXX.npy`. For example: `Area_1_dales_1.npy`, `Area_1_dales_2.npy`. The testing-file names should start with `Area_5_XXXX.npy`. For example: `Area_5_dales_1.npy`, `Area_5_dales_2.npy`. As per the script, files starting with `Area_1_` and `Area_5_` will be considered as training and testing files, respectively.

For converting the data into `.npy` format, please refer to the repo "[PointNet](https://github.com/charlesq34/pointnet)".

Sample data is available at: "[Google Drive Link]()". There are just two classes in the data, `vegetation (label: 0)` and `non-vegetation (label: 1)`.

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
author={Aditya, Aditya and Lohani, Bharat and Aryal, Jagannath and Winter, Stephan},
journal = {Science of Remote Sensing},
volume = {13},
pages = {100382},
year = {2026},
doi = {https://doi.org/10.1016/j.srs.2026.100382}
}
```
