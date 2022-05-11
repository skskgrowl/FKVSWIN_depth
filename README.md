## My Paper Title
This repository is the official implementation of My Paper Title.
## Contents
1. [Installation](#installation)
2. [Datasets](#datasets)
3. [Training](#training)
4. [Evaluation](#evaluation)
5. [Models](#models)
6. [Demo](#demo)

## Installation
```
conda create -n fkvswin python=3.8
conda activate fkvswin
conda install pytorch=1.10.0 torchvision cudatoolkit=11.1
pip install matplotlib, tqdm, tensorboardX, timm, mmcv
```


## Datasets
You can prepare the datasets KITTI and NYUv2 according to [here](https://github.com/cleinc/bts), and then modify the data path in the config files to your dataset locations.


## Training
First download the pretrained encoder backbone from [here](https://github.com/microsoft/Swin-Transformer), and then modify the pretrain path in the config files.

Training the NYUv2 model:
```
python fkvswin/train.py configs/arguments_train_nyu.txt
```

Training the KITTI model:
```
python fkvswin/train.py configs/arguments_train_kittieigen.txt
```


## Evaluation
Evaluate the NYUv2 model:
```
python fkvswin/eval.py configs/arguments_eval_nyu.txt
```

Evaluate the KITTI model:
```
python fkvswin/eval.py configs/arguments_eval_kittieigen.txt
```

## Models
| Model | Abs.Rel. | Sqr.Rel | RMSE | RMSElog | a1 | a2 | a3| 
| :--- | :---: | :---: | :---: |  :---: |  :---: |  :---: |  :---: |
|[NYUv2](https://pan.baidu.com/s/1vNoHIH3bunmI5d0wL0yzQQ) | 0.0900 | 0.0433 | 0.3280 | 0.1170 | 0.929 | 0.990 | 0.998 |
|[KITTI_Eigen](https://pan.baidu.com/s/1dMsNL6wralGAd4UFcp8Acw) | 0.0520 | 0.1532 | 2.111 | 0.079 | 0.974 | 0.997 | 0.999 |
The code is:pfkv

## Demo
Test images with the indoor model:
```
python fkvswin/test.py --data_path datasets/test_data --dataset nyu --filenames_file data_splits/test_list.txt --checkpoint_path model_nyu.ckpt --max_depth 10 --save_viz
```

## Acknowledgements
Thanks to Jin Han Lee for opening source of the excellent work [BTS](https://github.com/cleinc/bts).
Thanks to Microsoft Research Asia for opening source of the excellent work [Swin Transformer](https://github.com/microsoft/Swin-Transformer).
