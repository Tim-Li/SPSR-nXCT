# A-Strategy-for-Improving-Temporal-Resolution-in-X-ray-Tomography-Using-Deep-Learning
Tai-Yue Li and Chun-Chieh Wang

TLS BL01B1 beamline, National Synchrotron Radiation Research Center, Hsinchu, Taiwan

## Overview
We introduce a method to enhance the temporal resolution of XCT without increasing radiation intensity by using pixel binning to shorten exposure times and sparse-view acquisition to reduce image count. Our approach utilizes deep learning models based on SwinIR architecture to correct resolution degradation and minimize streak artifacts in sparse-view reconstructions. 

We apply a resolution restore model for spatial resolution improvement from x4 downsampled images, followed by sparse-view reconstruction using Filtered Back Projection at 5-degree intervals. This is enhanced by a sparse-view restore model to further reduce streak artifacts. Tested with simulation data and Taiwan Light Source TLS 01B1 data, our method significantly improves image quality, reduces tomography scan time by about 80 times, boosts equipment efficiency, and facilitates the study of dynamic 3D structures.

## Method
![alt text](figure/figure1.png)
### Model 1: Image Resolution restore model
![alt text](figure/figure2-1.png)

![alt text](figure/figure2-2.png)


### Model 2: Sparse-view reconstruction model
![alt text](figure/figure3-1.png)


## Environment
### Create Conda ENV
```
conda create -n txm_sr python=3.10
conda activate txm_sr
```
### Installation and check
```
# pytorch
pip install torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0 --extra-index-url https://download.pytorch.org/whl/cu113
python -c 'import torch;print(torch.cuda.is_available(),torch.cuda.device_count())'

# BasicSR
git clone https://github.com/XPixelGroup/BasicSR.git
cd Basicsr
pip install -r requirements.txt
python setup.py develop
```

## How to Inference
### pretrain model
- [Model 1: Image Resolution restore model](https://drive.google.com/drive/folders/1d5rl55zROl7_eA-w3XRvixB25QI7Ngrm?usp=drive_link)
- [Model 2: Sparse-view reconstruction model](https://drive.google.com/drive/folders/1nL9daBs-m3xi-CdC4yyi19fN5hOWNRpp?usp=drive_link)
- [Colab demo code](https://colab.research.google.com/drive/1nnDG4-a0yHmAuymWFbqpqE61kZEtmo2y?usp=drive_link)
```
python inference/inference_swinir.py --task real_sr --input {dataset_path} --patch_size 64 --model_path {model_path} --output {output_path}
```
## Citations
If our work is helpful to your reaearch, please kindly cite our work. Thank!

## Thanks
A part of our work has been facilitated by [SwinIR](https://github.com/JingyunLiang/SwinIR) framework, and we are grateful for their outstanding contributions.

Thank the National Center for High-performance Computing of
Taiwan for providing computational and storage resources.


## Contact
If you have any question, please email tim312508@gmail.com to discuss with the author.


