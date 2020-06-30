## ZIDAS 2020 - Deep learning 



### Fiji

We already prepared a Fiji instance with all plugins preinstalled. Please download them for you platform: 

* [Linux](https://drive.switch.ch/index.php/s/OYspyjikJ3pbRbO)
* [MacOSX](https://drive.switch.ch/index.php/s/l15IzCE2oFd4RbK)
* [Windows](https://drive.switch.ch/index.php/s/2NH59R2RxTORDEQ)



### Exercise 1 - Applying DL models in Fiji

Pick on of the following 

#### Exercise 1a (20 mins)

Noise2Void

1. Open Fiji 

2. Load a low SNR (noisy) image containing some cells:

[Low snr image](exercise1a/cells_low_snr.tif)

3. Apply a median filter (poor man's denoising) of different radii to test what a simple baseline method would give you:
`Process > Filters > Median`

4. Open the Noise2Void Plugin 
`Plugins > CSBDeep > N2V > N2V train + predict`  

5. Adjust training parameters

For this exercise, we will adjust some parameters, such that training finishes before the night falls. 

 - set `epochs=100` and `numeber of steps = 50`.    
 - press `train` and discuss within your groups 
 
6. After training, prediction time  

Use "predict with last checkpoint" after the training has finished.



#### Exercise 1b

StarDist 


#### Exercise 2 - Training DL models

Pick on of the following 

#### Exercise 2a

CARE colab 

#### Exercise 2b

StarDist colab 




