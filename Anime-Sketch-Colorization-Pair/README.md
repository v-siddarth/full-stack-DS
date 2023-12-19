# Anime-Sketch-Colorization-Pair

### Load Dataset that will be used in the Project
Dataset that will be used is anime-sketch-colorization-pair from kaggle

👉 [link to dataset](https://www.kaggle.com/ktaebum/anime-sketch-colorization-pair)
<br>
👉 [Kaggle Link](https://www.kaggle.com/code/sumitsahjr/pix2pix)

This dataset contains 14200 pairs of sketch and colored image used for training and 3545 pairs of sketch and colored image used for validation formatted as (.png) file. Since this dataset sized 6.53 GB, I used kaggle notebook so i don't need to download the dataset.

All image in the dataset look like this

Each image will be sized 1024x512 containing 2 image (colored and sketch). Colored image will take half of the size of full image and sketch image will take the other half. That's why I need to split the image into 2 (512x512 color image and 512x512 sketch image).

### Building the Generator Model

Generator model that are used in this project are U-net model identical with the paper, which is basically encoder and decoder with skip connection for the i and n-i layer. We can also use autoencoder model which doesn't have skip as the paper said if we want.

**note:** Architecture for the generator model is the same with the one that the paper proposed.
<br>
<img src="data:image/png;base64,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">

### Detail for the encoder and decoder for U-net model

**i. Encoder**

C64-C128-C256-C512-C512-C512-C512-C512

**ii. Decoder**

CD512-CD1024-CD1024-C1024-C1024-C512-C256-C128

* Each encoder block contains convolution layer, batch_normalization layer (except for the first block), and leaky relu layer
* Each decoder block contains transposed convolution layer, dropout layer (for the first 3 block), and relu layer
* There will be skip connection between i-th encoder and (n-i)-th decoder
* Last layer uses a single convolutional layer with three channels and tanh activation function which is commonly used for GAN Model
  
### Resulting U-net model could be seen from the image below

<img width="313" alt="Generator_U-net_result" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/7a501b02-cd56-49b5-bc1a-6d32037bdc79">

### Building the Discriminator Model

Discriminator model that are used in this project is PatchGAN identical with the paper, which basically classifies if each patch from the image is real or fake (0/1). In the research paper, the author tried pixelGAN and imageGAN also, but the patchGAN generate the best result and ran faster for pix2pix.

**note**: Architecture for the discriminator model is the same with the one that the paper proposed.

<img src="data:image/jpeg;base64,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">

### Detail for the PatchGAN model

**C64-C128-C256-C512**

* Each block contains convolution layer, batch_normalization layer, and leaky relu layer.
* The output will be 16x16x1 map which each value represent a patch from the image.

### Resulting U-net model could be seen from the image below
<img width="644" alt="discriminator U-net model" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/274dab73-2562-4f95-ab6e-b1e9f8d83811">

### Training the model
<br>
**At Epoch 1**
<img width="1252" alt="GL&DL_at_1" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/b0c360bb-d37b-43b1-bf5c-51d1774fd044">

**At Epoch 25**
<img width="1262" alt="GL&DL_at_25" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/afa8683d-f220-497b-8379-08575682a98e">

**At Epoch 49**
<img width="1258" alt="GL&DL_at_49" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/2a979bff-7267-4cd0-8405-72729f5c89d8">
<br>

### Plot loss for the generator model
<br>
<img width="651" alt="Generator_loss" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/888b1a54-7ce1-486f-aeed-2f453ec1b83f">
<br>
### Plot loss for the discriminator model
<br>
<img width="659" alt="discriminator_loss" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/8fc3f606-ecc2-4c93-be58-562652d70864">
<br>

### Result after training
<img width="901" alt="result_after_training" src="https://github.com/sumit-jr/Anime-Sketch-Colorization-Pair/assets/81641001/01d3784c-2e25-4320-b708-11e10cd274b7">

