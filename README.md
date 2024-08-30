# Video Upscaler Script with GFPGAN
A Video Upscaler script based on GFPGAN.  

This script is modified from  
[https://github.com/GeeveGeorge/GFPGAN-for-Video-SR](https://github.com/GeeveGeorge/GFPGAN-for-Video-SR)  

# Install
* Install [pytorch 1.x and torchvision](https://pytorch.org/get-started/previous-versions/)  (torch 2.x won't work)
* Install [GFPGAN](https://github.com/TencentARC/GFPGAN)
* Install `Real-ESRGAN` with command `pip install realesrgan` in your python environment
* Download Model [GFPGANv1.4.pth](https://github.com/TencentARC/GFPGAN/releases/download/v1.3.0/GFPGANv1.4.pth) to `Your GFPGAN Folder/gfpgan/weights`
* Donwload Model [detection_Resnet50_Final.pth](https://github.com/xinntao/facexlib/releases/download/v0.1.0/detection_Resnet50_Final.pth) to `Your GFPGAN Folder/gfpgan/weights`
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
### FFMpeg error "Format avi detected only with low score of 1, misdetection possible"
The real issue is your GFPGAN failed. So ffmpeg can not get the result video it need. The real error msg, is the line before `walking`. 

A basic rule for this project is: if your GFPGAN works, this project works. If your GFPGAN fails, this project fails too. So you better checking following section for issues of GFPGAN.  

### Unrecognized arguments and file path
Your file and folder path should only use English character without any space in it.  

# Comman Issue of GFPGAN
### Downloading failed
When using GFPGAN for the first time, it gonna download 2 models from github. One for `GFPGAN`, one for `Real-ESRGAN`. If downloading failed, it will show the downloading link and its target local folder path. So you can just manually download these 2 models and put them into the right folder.  

### Can not find `torchvision.transforms.functional_tensor`
GFPGAN is based on a project called `basicsr`. This project only works with pytorch 1.x. If you really want to use it with torch 2.x, you can go to basicsr's folder, find `basicsr/data/degradations.py`, replace all `torchvision.transforms.functional_tensor` to `torchvision.transforms.functional`. 







