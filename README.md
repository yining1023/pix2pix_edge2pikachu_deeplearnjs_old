# Pix2pix edge2Pikachu in deeplearnjs (OLD)

Demo: [https://yining1023.github.io/pix2pix_edge2pikachu_deeplearnjs_old](https://yining1023.github.io/pix2pix_edge2pikachu_deeplearnjs_old)

Credits: This project is based on [affinelayer](https://github.com/affinelayer)'s [pix2pix-tensorflow](https://github.com/affinelayer/pix2pix-tensorflow)

***A new front-end site coming soon! I'm rewriting it here: [https://github.com/yining1023/pix2pix_edge2pikachu_deeplearnjs](https://github.com/yining1023/pix2pix_edge2pikachu_deeplearnjs).

Todo list:
- [ ] Update to deeplearn 0.5
- [ ] Make the interface with p5.js
- [ ] Make it draw in realtime.

Try it yourself: Download the folder and run it locally, `$python -m SimpleHTTPServer`

## How to create edge2xxx from scratch
- 1. Prepare the data
- 2. Train the model
- 3. Test the model
- 4. Port the model to deeplearn.js
- 5. Create an interactive inteerface in the browser

### 1. Prepare the data
- Scrape images from google search
- Remove the background of the images
- Resize all images into 256x256 px
- Detect edges of all images
- Combine input images and target images
- Split all combined images into two folders: `train` and `val`

### 2. Train the model

### 3. Test the model

### 4. Port the model to deeplearn.js
