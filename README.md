# Video Upscaler Script with GFPGAN
A Video Upscaler script based on GFPGAN.  

This script is modified from  
[https://github.com/GeeveGeorge/GFPGAN-for-Video-SR](https://github.com/GeeveGeorge/GFPGAN-for-Video-SR)  

# Install
* Install [pytorch 1.x and torchvision](https://pytorch.org/get-started/previous-versions/)  (torch 2.x won't work)
* Install [GFPGAN](https://github.com/TencentARC/GFPGAN)
* Install `Real-ESRGAN` with command `pip install realesrgan` in your python environment
* Download model [GFPGANv1.4.pth](https://github.com/TencentARC/GFPGAN/releases/download/v1.3.0/GFPGANv1.4.pth) to `Your GFPGAN Folder/gfpgan/weights`
* Download model [detection_Resnet50_Final.pth](https://github.com/xinntao/facexlib/releases/download/v0.1.0/detection_Resnet50_Final.pth) to `Your GFPGAN Folder/gfpgan/weights`
* Download model [parsing_parsenet.pth](https://github.com/xinntao/facexlib/releases/download/v0.2.2/parsing_parsenet.pth) to `Your GFPGAN Folder/gfpgan/weights`
* Install [opencv-python](https://pypi.org/project/opencv-python/)
* Install [ffmpeg ](https://ffmpeg.org/) for command line
  * For windows, you need to download a windows build, unzip it, put its path into your system's environment variables.   
* Download `video.py` file from this project, put it into your `GFPGAN` folder
* Create a `data` folder under your `GFPGAN` folder
* Then create this folder tree under that data folder:  
├─results  
│  ├─cmp  
│  ├─cropped_faces  
│  ├─restored_faces  
│  └─restored_imgs  
├─results_mp4_videos  
├─results_videos  
├─upload  
└─videos  

# How to use
* Put your videos into "data/videos"
* Go back to `GFPGAN` folder
* Edit `video.py`, modify its fps and upscale size for your video and save file.
* Run `python video.py` and wait.
* Upscaled new video will be under `GFPGAN/data/results_mp4_videos`
* Done

# Notice
Compare to Real-ESRGAN, GFPGAN can restore faces nicely. But, it gonna be very very slow. Only use it for short videos.  

# Common Issue

### Get the real error Msg
If you see any ffmpeg error msg like ` Format avi detected only with low score of 1, misdetection possible`, that's not the real error.  

The real issue is your GFPGAN failed. So ffmpeg can not get the result video it need. The real error msg, is the line before `walking`. 

A basic rule for this project is: if your GFPGAN works, this project works. If your GFPGAN fails, this project fails too. So you better check following issues of GFPGAN.  

### Unrecognized arguments and file path
Your file and folder path should only use English character without any space in it.  

### Downloading failed
When using GFPGAN for the first time, it gonna download some models from github. One for `Real-ESRGAN`, others for `GFPGAN`. If downloading failed, it will show the downloading link and its target local folder path. So you can just manually download these models and put them into the right folder.  

### Can not find `torchvision.transforms.functional_tensor`
GFPGAN is based on a project called `basicsr`. This project uses function `torchvision.transforms.functional_tensor` which is removed from torchvision v0.17+. So, it only works with pytorch 1.x.  

### Working with torch 2.x
1. You need to install torch 2.x by following its official installation document:
https://pytorch.org/get-started/locally/  

2. You need to update your package `basicsr`. Which is needed by GFPGAN, but only works with pytorch 1.x if you install it with pip. 

There are 2 ways to make it work with torch 2.x.
* Go to basicsr's folder in your python environment, find `basicsr/data/degradations.py`, replace all `torchvision.transforms.functional_tensor` with `torchvision.transforms.functional`.  
* Or, do not install `basicsr` with pip, which is an old version. Just install it from its source code in github:   
`pip install git+https://github.com/XPixelGroup/BasicSR`   


