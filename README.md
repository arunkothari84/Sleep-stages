# Sleep-stages

# Introduction

**This repo is a modified version of DeepSleepNet to predict sleep stages.**

## Changes in Original REPO

Made few changes in the original repo for testing purposes.

- Used **8 files for training purposes** and **2 for validation**.

```
NAME of the files:

VALIDATION: ['./Data with pre-processing\\SC4011E0.npz',
             './Data with pre-processing\\SC4012E0.npz']

TRAINING: ['./Data with pre-processing\\SC4001E0.npz',
           './Data with pre-processing\\SC4002E0.npz',
           './Data with pre-processing\\SC4021E0.npz',
           './Data with pre-processing\\SC4022E0.npz',
           './Data with pre-processing\\SC4031E0.npz',
           './Data with pre-processing\\SC4032E0.npz',
           './Data with pre-processing\\SC4041E0.npz',
           './Data with pre-processing\\SC4042E0.npz']
```


```
/deepsleepnet/deepsleep/trainer.py

ln[311] : x_train, y_train, x_valid, y_valid = data_loader.load_train_data(n_files=10)
```

[DRIVE LINK FOR MODIFIED REPO](https://drive.google.com/drive/folders/1yl-MZ20kRWklC0BKspHvBu5_FQmoTzk-?usp=sharing)

## Parameters:

- I have set cutoff frequency for the buttering to **25% of the lowpass and highpass frequency**.

```bash
highcut = float(raw_signals._raw_extras[0]['lowpass'][0]) * 0.25
lowcut = float(raw_signals._raw_extras[0]['highpass'][0]) * 0.25
```
## Steps:

### Loading Data:
[Download Data](https://www.physionet.org/static/published-projects/sleep-edfx/sleep-edf-database-expanded-1.0.0.zip)

[Project link](https://www.physionet.org/content/sleep-edfx/1.0.0/)

> Using **Make Data.ipynb**
- Using MNE version 0.19.0
- Cloning Original REPO
- Using **./deepsleepnet/prepare_physionet.py** to prepare dataset folder

### PreProcessing:
> Using **Pre-Processing.ipynb**
- Applying ***FFT and Buttering*** to the **.npz** file, and saving it in the **Data with pre-processing** folder.

[DRIVE LINK FOR DATA](https://drive.google.com/drive/folders/1SMHQeVfigjbKB0KBlwSqoAGOVKQcu45w?usp=sharing)

### Visualization:
- First 500 points

![image](https://i.ibb.co/x84cRLN/image.png)

- First 200 points

![image](https://i.ibb.co/4KP5cZ5/image.png)

### Driver Code:
> Using **Driver-code.ipynb**
- Uploaded validation data, training data and codes to the drive.
- Using 20 folds to train
- Last training LOOP:

```
		epoch 195: train (8.33 sec): n=7500, loss=0.588 (0.021), acc=0.992, f1=0.990 | valid (1.12 sec): n=1750, loss=22.901 (0.021), acc=0.821, f1=0.771
		epoch 196: train (8.33 sec): n=7500, loss=0.823 (0.021), acc=0.988, f1=0.985 | valid (1.17 sec): n=1750, loss=21.200 (0.021), acc=0.832, f1=0.783
		epoch 197: train (8.33 sec): n=7500, loss=0.711 (0.021), acc=0.988, f1=0.985 | valid (1.15 sec): n=1750, loss=18.673 (0.021), acc=0.851, f1=0.798
		epoch 198: train (8.33 sec): n=7500, loss=0.704 (0.021), acc=0.990, f1=0.987 | valid (1.13 sec): n=1750, loss=25.431 (0.021), acc=0.814, f1=0.765
		epoch 199: train (8.32 sec): n=7500, loss=0.785 (0.021), acc=0.988, f1=0.985 | valid (1.15 sec): n=1750, loss=21.014 (0.021), acc=0.845, f1=0.786
		 
		[2021-10-10 04:07:39.754372] epoch 200:
		train (8.315 sec): n=7500, loss=0.862 (0.021), acc=0.988, f1=0.985
		[[1044    5    0    0    1]
		 [   8  781   12    0    5]
		 [   1   14 3582   18    2]
		 [   0    0   17  666    0]
		 [   0    2    5    0 1337]]
		valid (1.139 sec): n=1750, loss=24.453 (0.021), acc=0.823, f1=0.768
		[[274  38   1   0  16]
		 [  5  43  18   3  40]
		 [  0  13 373 148  22]
		 [  0   0   0 459   0]
		 [  0   1   5   0 291]]
```

[DRIVE LINK FOR LAST CHKPT](https://drive.google.com/file/d/11nRsmo2BF7AvFsotXp39eWTQ-nDGvtT5/view?usp=sharing)


## Resources:
- [Fast Fourier Transform](https://towardsdatascience.com/fast-fourier-transform-937926e591cb)
- [Buttering of Wave](https://www.youtube.com/watch?v=juYqcck_GfU&t=625s)
