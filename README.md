![Zidas](imgs/zidas_logo.png)

# Deep Learning for image analysis - Exercises  

---

### Setup

Please prepare the following setup steps before the exercise on Wednesday starts
 
1. Setup Fiji

Due to the downtime of Fiji/ImageJ update sites, we created prebuilt Fiji versions with all plugins preinstalled. Please download the respective version for your platform and unzip it: 

[Linux](https://drive.switch.ch/index.php/s/9eULhevg9gMPNbj) , [MacOSX](https://drive.switch.ch/index.php/s/twLVBUhl5fSDOMO), or [Windows](https://drive.switch.ch/index.php/s/y2ytRVUaexlxBZG).


2. Install deepImageJ in Fiji

- download the [deepImageJ plugin](https://github.com/deepimagej/deepimagej-plugin/releases/download/1.1.0/DeepImageJ_CPU_dependencies.zip) 
- unpack the resulting zip file which should create a folder `DeepImageJ_CPU_dependencies` containing lots of jar files:

![JarJar](imgs/screen_jar.png)  

- Copy all jar files into the `jars` subfolder of your Fiji installation:

![JarJarBinks](imgs/screen_jar_copy.png)  


2. Google Colab 

We are going to use google colab for the neural network training demonstration as it provides easy access to a jupyter notebook environment and a GPU. Google colab however needs a google account, so please create one and then login to your account at the start of the exercise.


---

## Exercise 1 - Applying DL models in Fiji


The aim of the first exercise is to try out deep learning based methods for denoising (Noie2Void) or nuclei segmentation (StarDist) in Fiji. 
We provide 2 alternative exercises for each case (1a for denoising or 1b for segmenation). Please choose the one of them closest to the the median interest of your group.

#### Alternative 1a - Denoising with Noise2Void (20 mins)

Here we will denoise a single image by training a Noise2Void network (that doesn't need high SNR ground truth). 


1. Open Fiji 

2. Load a low SNR (noisy) image containing some cells: [Low SNR image](https://github.com/maweigert/zidas_2020_DL_intro_Part_2/raw/master/exercise1a/hepatocytes_low_snr.tif)[1]

3. Apply a median filter (poor man's denoising) of different radii to test the output of a simple baseline method:
`Process > Filters > Median`

4. Open the Noise2Void Plugin 
`Plugins > CSBDeep > N2V > N2V train + predict`  

5. Adjust training parameters

For this exercise, we will adjust some parameters, such that training finishes before the night falls :) 

 - set `epochs=50` and `number of steps = 30`.    
 - press `Ok` 
 - While waiting for the training to finish, discuss the following questions in your group:
    - What is train/val/test split? Why is it important? 
    - 
 
6. After training, prediction time!  

Use "predict with last checkpoint" after the training has finished.

7. Compare with a high SNR image of the same field of view: [High SNR image](https://github.com/maweigert/zidas_2020_DL_intro_Part_2/raw/master/exercise1a/hepatocytes_high_snr.tif) [1]


#### Alternative 1b - Nuclei Segmentation with StarDist (20mins)

Here we will apply pretrained StarDist networks to different 2D images. Pretrained networks can be quite effective if your images are similar to the training images of the respective model (see [here](https://github.com/mpicbg-csbd/stardist#pretrained-models-for-2d) for an overview of available models and example training images). 

1. Open Fiji 

2. Load a low SNR (noisy) image containing histone labeled HeLa cells: [Low SNR image](https://github.com/maweigert/zidas_2020_DL_intro_Part_2/raw/master/exercise1b/fluo_low.tif)[3]

3. Try to apply a thresholding to test the output of a simple baseline method:

Use `Image > Adjust > Threshold` and see what different values would give you (hint: it shouldn't look too good).
Press `Reset` and close the window, as we don't want to apply the threshold.

4. Open the StarDist plugin

`Plugins > StarDist > StarDist 2D`

In the options

- select a pertrained model: `Versatile (fluorescent nuclei)` (as we have fluorescent cells after all) 
- Check `Normalize Image` (should be the default)
- predict!

5. Compare with high SNR image

There is a high SNR image of the same field of view: [High SNR image](https://github.com/maweigert/zidas_2020_DL_intro_Part_2/raw/master/exercise1b/fluo_high.tif)[3]. Apply StarDist to this image and compare the results.

6. Load a histopathologie (H&E stain) [image of human retina](https://github.com/maweigert/zidas_2020_DL_intro_Part_2/raw/master/exercise1b/histo_retina.tif). Mind that this time, the image is a 3 channel rgb image (and not a single channel image as before). 

7. Apply StarDist plugin, but this time with a H&E model (`Versatile (H&E stain)`).

8. Play around by applying StarDist to your own (or other) 2D images containing cell nuclei. 

---

## Exercise 2 - Training DL models

The aim of this second exercise is to demonstrate how to train your own deep learning models in python. This can be necessary, if no pretrained models are applicable to your task or if your images differ substantially from those a pretrained model was trained on. 

Again, there are 2 alternative projects:

- Exercise 2a: Training of a CARE image restoration network for denoising and upsampling of 2D images
- Exercise 2b: Training of a StarDist nuclei segmentation model for 2D images  

Again, please pick one of them.

Both altertatives can be run in your browser as google colab (jupyter) notebooks after you have signed in with your google account. 

Each notebook needs to be run line by line from the start (don't skip lines!) almost each of which contains detailed description of its purpose.  
Try to understand what is happening at each line before you run it (and ask your teacher if not!). 


#### Exercise 2a

CARE denoising/upsampling training example: [![](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/maweigert/zidas_2020_DL_intro_Part_2/blob/master/exercise2a/care_example_denoising_upsampling_2D_colab.ipynb)

#### Exercise 2b

StarDist training example: [![](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/maweigert/zidas_2020_DL_intro_Part_2/blob/master/exercise2b/stardist_example_2D_colab.ipynb) 


---
---

##### Image Credits:

- [1] Broad Bioimage Benchmark Collection
- [2] Fabián Segovia-Miranda
- [3] [Cell tracking challenge](http://celltrackingchallenge.net/)
