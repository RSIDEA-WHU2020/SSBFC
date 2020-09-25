<h1 align="center">spectral–structural bag-of-features scene classifier (SSBFC)</h1>
<h5 align="center">A spectral–structural bag-of-features scene classifier for very high spatial resolution remote sensing imagery</h5>

<h5 align="right">by <a>Bei Zhao</a>, <a href="http://rsidea.whu.edu.cn/">Yanfei Zhong</a> and <a href="http://www.lmars.whu.edu.cn/prof_web/zhangliangpei/rs/index.html">Liangpei Zhang</a></h5>


This is an official implementation of SSBFC in our ISPRS 2016 paper ["A spectral–structural bag-of-features scene classifier for very high spatial resolution remote sensing imagery"](https://www.sciencedirect.com/science/article/pii/S0924271616000617).

Abstract

Land-use classification of very high spatial resolution remote sensing (VHSR) imagery is one of the most challenging tasks in the field of remote sensing image processing. However, the land-use classification is hard to be addressed by the land-cover classification techniques, due to the complexity of the land-use scenes. Scene classification is considered to be one of the expected ways to address the land-use classification issue. The commonly used scene classification methods of VHSR imagery are all derived from the computer vision community that mainly deal with terrestrial image recognition. Differing from terrestrial images, VHSR images are taken by looking down with airborne and spaceborne sensors, which leads to the distinct light conditions and spatial configuration of land cover in VHSR imagery. Considering the distinct characteristics, two questions should be answered: (1) Which type or combination of information is suitable for the VHSR imagery scene classification? (2) Which scene classification algorithm is best for VHSR imagery? In this paper, an efficient spectral–structural bag-of-features scene classifier (SSBFC) is proposed to combine the spectral and structural information of VHSR imagery. SSBFC utilizes the first- and second-order statistics (the mean and standard deviation values, MeanStd) as the statistical spectral descriptor for the spectral information of the VHSR imagery, and uses dense scale-invariant feature transform (SIFT) as the structural feature descriptor. From the experimental results, the spectral information works better than the structural information, while the combination of the spectral and structural information is better than any single type of information. Taking the characteristic of the spatial configuration into consideration, SSBFC uses the whole image scene as the scope of the pooling operator, instead of the scope generated by a spatial pyramid (SP) commonly used in terrestrial image classification. The experimental results show that the whole image as the scope of the pooling operator performs better than the scope generated by SP. In addition, SSBFC codes and pools the spectral and structural features separately to avoid mutual interruption between the spectral and structural features. The coding vectors of spectral and structural features are then concatenated into a final coding vector. Finally, SSBFC classifies the final coding vector by support vector machine (SVM) with a histogram intersection kernel (HIK). Compared with the latest scene classification methods, the experimental results with three VHSR datasets demonstrate that the proposed SSBFC performs better than the other classification methods for VHSR image scenes.


## News
1. 2020/08/28, We release the code of SSBFC.


## Features
1.  Combine the spectral and structural information
2.  Represents the images with the coding vectors of low-level features obtained by an unsupervised feature learning algorithm and vector quantization coding (VQC)


## Citation
If you use SSBFC in your research, please cite the following paper:
```text
@article{article,
author = {Zhao, Bei and Zhong, Yanfei and Zhang, Liangpei},
year = {2016},
month = {06},
pages = {73-85},
title = {A spectral–structural bag-of-features scene classifier for very high spatial resolution remote sensing imagery},
volume = {116},
journal = {ISPRS Journal of Photogrammetry and Remote Sensing},
doi = {10.1016/j.isprsjprs.2016.03.004}
}
```
 

## Getting Started
### 1. Installation
System Requirements: linux

Compiler Environment:
```bash
cd SSBFC/code/topic_model/code
run make
```
*The path in Makefile should be current path (e.g. HOME = /mnt/disk1/lxm/SSBFC/code/topic_model)
### 2. Prepare datasets

The project should be organized as:
```text
SSBFC
├── code
│   ├── feat_coding       /feature coding
│   ├── libsvm-3.20       //tools of SVM classifier
│   ├── scenefeature      //feature extraction
│   ├── topic_model       //BOVW for scene classification
│   ├── util
│   ├── vlfeat-0.9.17       //tools of K-means
│   ├── demo_cal_MeanStd_KM.m
│   ├── demo_cal_SIFT_KM.m
│   ├── demo_SPM_RS_Big.m
│   ├── SSBFC_main.m
├── data        // dataset
│   ├── Google dataset of SIRI-WHU (http://rsidea.whu.edu.cn/resource_sharing.htm)

```

### 3. run experiments

#### 1. Scene feature extraction
```bash
run 'SSBFC_main.m'
```
Meaning of Variables:

"12class_tif": a folder for storing image data
image_data_dir: the path of "12class_tif" , the folder name in the path cannot have spaces.
code_book_file_dir: The output path of the cluster center file after clustering.
out_sift_feature_dir, out_meanstd_feature_dir: The output path of final feature 

*The folder name in the path cannot have spaces.

#### 2. Scene classification by SVM
```bash
cd SSBFC/code/topic_model
run  './mfcode_hik ssbfc_google.txt'  (ssbfc_google.txt is the configuration file)
```


### License
The copyright belongs to Intelligent Data Extraction, Analysis and Applications of Remote Sensing(RSIDEA) academic research group,State Key Laboratory of Information Engineering in Surveying, Mapping, and Remote Sensing (LIESMARS),Wuhan University. This program is for academic use only. For commercial use, please contact Professor.Zhong(zhongyanfei@whu.edu.cn). The homepage of RSIDEA is: http://rsidea.whu.edu.cn/index.html