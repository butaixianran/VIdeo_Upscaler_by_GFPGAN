# Video Upscaler Script with GFPGAN
A Video Upscaler script based on GFPGAN.  

This script is modified from  
[https://github.com/GeeveGeorge/GFPGAN-for-Video-SR](https://github.com/GeeveGeorge/GFPGAN-for-Video-SR)  

# Install
* Install [GFPGAN](https://github.com/TencentARC/GFPGAN)
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
Compare to Real-ESRGAN, GFPGAN can restore faces nicely. But, it gonna be very slow. Only use it for short videos.  
