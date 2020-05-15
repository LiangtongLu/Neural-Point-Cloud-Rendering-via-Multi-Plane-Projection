# NeuralPointCloudRendering

**Neural Point Cloud Rendering via Multi-Plane projection** (CVPR 2020)  
Peng Dai*, [Yinda Zhang*](https://www.zhangyinda.com/), [Zhuwen Li*](https://scholar.google.com/citations?user=gIBLutQAAAAJ&hl=en), [Shuaicheng Liu](http://www.liushuaicheng.org/), [Bing Zeng](https://scholar.google.com/citations?user=s-kUGYQAAAAJ&hl=en).
<br>In [CVPR](https://arxiv.org/abs/1912.04645.pdf), 2020.

## Introduction
<img src='./images/framework.png' width=1000>
<br>
Our method is divided into two parts, the multi-plane based voxelization (left) and multi-plane rendering(right). For the first part, point clouds are re-projected into camera coordinate system to form frustum region and voxelization plus aggregation operations are adopted to generate a multi-plane 3D representation, which will be concatenated with normalized view direction and sent to render network. For the second part, the concatenated input is feed into a 3D neural render network to predict the product with 4 channels (i.e. RGB + blend weight) and the final output is generated by blending all planes. The training process is under the supervision of perceptual loss, and both network parameters and point clouds features are optimized according to the gradient.

## Environments
Tensorflow 1.10.0
<br>
Python 3.6
<br>
OpenCV

## Preprocessing
Before training, there are several steps required. And pre-processing results are stored in 'pre_processing_results/'.

### Data downloads
Download datasets(i.e. ScanNet and Matterport 3D) into corresponding 'data/...' folders or use your own datasets.

### Point clouds generation
Generate point clouds files from registrated RGB-D images. Run 'pre_processing/generate_pointclouds_* .py' for point cloud files generation('point_clouds.ply'). Change file paths accordingly.

### Point clouds simplification
Based on generated point cloud files, we provide 'pre_processing/pointclouds_simplification.py' for point cloud simplification, results are saved in 'point_clouds_simplified.ply'. Also change file paths accordingly.

### Voxelization and Aggregation
In order to save training time, we voxelize and aggregate point clouds in advance by running 'pre_processing/voxelization_aggregation_* .py'. Also change file paths accordingly. 

## Network training/testing
To train the model, just run 'python npcr_ScanNet.py' for ScanNet and 'python npcr_Matterport3D.py' for Matterport3D. Set "is_training=True" and change path accordingly.
<br>
<br>
Set "is_training=False" for testing.

## Pretrained model
If you need the point cloud files and pretrained models, please email me(daipengwa@gmail.com) and show licenses of [ScanNet](https://github.com/ScanNet/ScanNet) and [Matterport3D](https://github.com/niessner/Matterport).

## Citation
If you use our code or method in your work, please cite the following:
```
@InProceedings{Dai_2019_neuralpointcloudrendering,
author = {Peng, Dai and Yinda, Zhang and Zhuwen, Li and Shuaicheng, Liu and Bing, Zeng},
title = {Neural Point Cloud Rendering via Multi-plane Projection},
booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
month = {June},
year = {2020}
}

