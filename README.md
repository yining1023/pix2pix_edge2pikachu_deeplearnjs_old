# Pix2pix edge2Pikachu in deeplearnjs (OLD)

Demo: [https://yining1023.github.io/pix2pix_edge2pikachu_deeplearnjs_old](https://yining1023.github.io/pix2pix_edge2pikachu_deeplearnjs_old)

Credits: This project is based on [affinelayer](https://github.com/affinelayer)'s [pix2pix-tensorflow](https://github.com/affinelayer/pix2pix-tensorflow)

A new front-end site coming soon! I'm rewriting it here: [https://github.com/yining1023/pix2pix_edge2pikachu_deeplearnjs](https://github.com/yining1023/pix2pix_edge2pikachu_deeplearnjs).

Todo list:
- [ ] Update to deeplearn 0.5
- [ ] Make the interface with p5.js
- [ ] Make it draw in realtime.

Try it yourself: Download the folder and run it locally:
```
$ python -m SimpleHTTPServer
```


## How to create edge2xxx from scratch
- 1. Prepare the data
- 2. Train the model
- 3. Test the model
- 4. Export the model
- 5. Port the model to deeplearn.js
- 6. Create an interactive interface in the browser



### 1. Prepare the data

- 1.1 Scrape images from google search
- 1.2 Remove the background of the images
- 1.3 Resize all images into 256x256 px
- 1.4 Detect edges of all images
- 1.5 Combine input images and target images
- 1.6 Split all combined images into two folders: `train` and `val`

Before we start, check out [affinelayer](https://github.com/affinelayer)'s [Create your own dataset](https://github.com/affinelayer/pix2pix-tensorflow#creating-your-own-dataset). I followed his instrustion for steps 1.3, 1.5 and 1.6.


#### 1.1 Scrape images from google search
We can create our own target images. But for this edge2pikachu project, I downloaded a lot of images from google. I'm using this [google_image_downloader](https://github.com/atif93/google_image_downloader) to download images from google.
After downloading the repo above, run -
```
$ python image_download.py <query> <number of images>
```
It will download images and save it to the current directory.


#### 1.2 Remove the background of the images
Some images have some background. I'm using [grabcut](https://docs.opencv.org/trunk/d8/d83/tutorial_py_grabcut.html) with OpenCV to remove background
Check out the script here: [https://github.com/yining1023/pix2pix-tensorflow/blob/master/tools/grabcut.py](https://github.com/yining1023/pix2pix-tensorflow/blob/master/tools/grabcut.py)
To run the script-
```
$ python grabcut.py <filename>
```
It will open an interactive interface, here are some instructions: [https://github.com/symao/InteractiveImageSegmentation](https://github.com/symao/InteractiveImageSegmentation)
Here's an example of removing background using grabcut:

<a href="https://ibb.co/iRp9LH"><img src="https://preview.ibb.co/du2kuc/Screen_Shot_2018_03_13_at_7_03_28_AM.png" alt="Screen Shot 2018 03 13 at 7 03 28 AM" border="0" with="500px"/></a>


#### 1.3 Resize all images into 256x256 px
Download [pix2pix-tensorflow](https://github.com/affinelayer/pix2pix-tensorflow) repo.
Put all images we got into `photos/original` folder
Run - 
```
$ python tools/process.py --input_dir photos/original --operation resize --output_dir photos/resized
```
We should be able to see a new folder called `resized` with all resized images in it.


#### 1.4 Detect edges of all images
The script that I use to detect edges of images from one folder at once is here: [https://github.com/yining1023/pix2pix-tensorflow/blob/master/tools/edge-detection.py](https://github.com/yining1023/pix2pix-tensorflow/blob/master/tools/edge-detection.py), we need to change the path of the input images directory on [line 31](https://github.com/yining1023/pix2pix-tensorflow/blob/3e0d6c8613b3aa69adffe5484989bbe2c82b2c57/tools/edge-detection.py#L31), and create a new empty folder called `edges` in the same directory.
Run - 
```
$ python edge-detection.py
```
We should be able to see edged-detected images in the `edges` folder.
Here's an example of edge detection: left(original) right(edge detected)

<a href="https://imgbb.com/"><img src="https://image.ibb.co/eBDGZc/0_batch2.png" alt="0_batch2" border="0" with="300px"></a>
<a href="https://imgbb.com/"><img src="https://image.ibb.co/hW410H/0_batch2_2.png" alt="0_batch2_2" border="0" with="300px"></a>


#### 1.5 Combine input images and target images
```
python tools/process.py --input_dir photos/resized --b_dir photos/blank --operation combine --output_dir photos/combined
```
Read more here: [affinelayer](https://github.com/affinelayer)'s [Create your own dataset](https://github.com/affinelayer/pix2pix-tensorflow#creating-your-own-dataset)


#### 1.6 Split all combined images into two folders: `train` and `val`
```
python tools/split.py --dir photos/combined
```
Read more here: [affinelayer](https://github.com/affinelayer)'s [Create your own dataset](https://github.com/affinelayer/pix2pix-tensorflow#creating-your-own-dataset)

I collected 305 images

### 2. Train the model
[https://github.com/affinelayer/pix2pix-tensorflow#getting-started](https://github.com/affinelayer/pix2pix-tensorflow#getting-started)



### 3. Test the model
[https://github.com/affinelayer/pix2pix-tensorflow#getting-started](https://github.com/affinelayer/pix2pix-tensorflow#getting-started)



### 4. Export the model



### 5. Port the model to deeplearn.js
I followed [affinelayer](https://github.com/affinelayer)'s instruction here: [https://github.com/affinelayer/pix2pix-tensorflow/tree/master/server#exporting](https://github.com/affinelayer/pix2pix-tensorflow/tree/master/server#exporting)
