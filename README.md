
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
| Model | Abs.Rel. | Sqr.Rel | RMSE | RMSElog | a1 | a2 | a3| SILog| 
| :--- | :---: | :---: | :---: |  :---: |  :---: |  :---: |  :---: |  :---: |
|[NYUv2](https://pan.baidu.com/s/1vNoHIH3bunmI5d0wL0yzQQ) | 0.0952 | 0.0443 | 0.3310 | 0.1185 | 0.923 | 0.992 | 0.998 | 9.1023 |
|[KITTI_Eigen](https://pan.baidu.com/s/1dMsNL6wralGAd4UFcp8Acw) | 0.0520 | 0.1482 | 2.0716 | 0.0780 | 0.975 | 0.997 | 0.999 | 6.9859 |
The code is:pfkv

## Demo
Test images with the indoor model:
```
python fkvswin/test.py --data_path datasets/test_data --dataset nyu --filenames_file data_splits/test_list.txt --checkpoint_path model_nyu.ckpt --max_depth 10 --save_viz
```

Play with the live demo from a video or your webcam:
```
python fkvswin/demo.py --dataset nyu --checkpoint_path model_zoo/model_nyu.ckpt --max_depth 10 --video video.mp4
```

![Output1](files/output_nyu1_compressed.gif)

[Demo video1](https://www.youtube.com/watch?v=RrWQIpXoP2Y)

[Demo video2](https://www.youtube.com/watch?v=fD3sWH_54cg)

[Demo video3](https://www.youtube.com/watch?v=IztmOYZNirM)

## Acknowledgements
Thanks to Jin Han Lee for opening source of the excellent work [BTS](https://github.com/cleinc/bts).
Thanks to Microsoft Research Asia for opening source of the excellent work [Swin Transformer](https://github.com/microsoft/Swin-Transformer).
