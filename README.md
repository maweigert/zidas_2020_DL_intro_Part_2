## ZIDAS 2020 - Deep learning 



### Fiji

We already prepared a Fiji instance with all plugins preinstalled. Please download them for you platform: 

[Linux](https://drive.switch.ch/index.php/s/OYspyjikJ3pbRbO) , [MacOSX](https://drive.switch.ch/index.php/s/l15IzCE2oFd4RbK), or [Windows](https://drive.switch.ch/index.php/s/2NH59R2RxTORDEQ)

---

### Exercise 1 - Applying DL models in Fiji

Pick one of the following 

#### Alternative 1a - Denoising with Noise2Void (20 mins)

DL-based Denoising in Fiji with Noise2Void

1. Open Fiji 

2. Load a low SNR (noisy) image containing some cells: [Low snr image](exercise1a/cells_low_snr.tif) [1]

3. Apply a median filter (poor man's denoising) of different radii to test the output of a simple baseline method:
`Process > Filters > Median`

4. Open the Noise2Void Plugin 
`Plugins > CSBDeep > N2V > N2V train + predict`  

5. Adjust training parameters

For this exercise, we will adjust some parameters, such that training finishes before the night falls :) 

 - set `epochs=50` and `numeber of steps = 50`.    
 - press `train` and discuss within your groups 
 
6. After training, prediction time  

Use "predict with last checkpoint" after the training has finished.



#### Alternative 1b - Nuclei Segmentation with StarDist (20mins)

We gonna learn about 

1. Open Fiji 

2. Load a low SNR (noisy) image containing some DAPI stained cells: [Low snr image](exercise1a/cells_low_snr.tif)

3. Try to apply a thresholding to test the output of a simple baseline method:

Use `Image > Adjust > Threshold` and see what different values would give you (hint: it shouldn't look good).
Press `Reset` and close the window, as we don't want to apply the threshold.

4. Open the StarDist plugin and predict

`Plugins > StarDist > StarDist 2D`

In the options

- select a pertrained model: `Versatile (fluorescent nuclei)` 
- Check `Normalize Image` (default)


---

#### Exercise 2 - Training DL models

Pick on of the following 

#### Exercise 2a

CARE colab 

#### Exercise 2b

StarDist colab 


---

#### Image Credits:

- [1] Broad Bioimage Benchmark Collection
- [2] Fabián Segovia-Miranda

