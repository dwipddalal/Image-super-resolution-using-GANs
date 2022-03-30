# Image-super-resolution-using-GANs
The problem of single image super resolution (SISR) has been around for a long time in computer vision. The goal is to estimate the equivalent high resolution image from a low resolution input image. </br>
 
The current best approaches to the problem are deep learning based, pioneered by the [SRCNN paper by Dong, et al.](https://arxiv.org/pdf/1501.00092.pdf) The SOTA benchmarks have been set mostly by GAN based methods such as the [SRGAN by Ledig, et al.](https://arxiv.org/pdf/1609.04802.pdf)
<br/>

This is my attempt at implementing a simple [DCGAN](https://arxiv.org/pdf/1511.06434.pdf) to perform SISR at a scale of 4x.


## Dataset 
The dataset used was the CelebA dataset [available here](https://www.kaggle.com/jessicali9530/celeba-dataset). It consists of about 200,000 images of people's faces.

## Approach
The model, simply put, is a DCGAN with a modified loss function. <br/>

#### Architecture
The Generator consists of a series of Residual units followed by two upsampling layers and a Convolutional layer. BatchNormalization and Leaky ReLU activation were used in all layers, except for the output, where tanh was used.<br/>
The Discriminator consists of a series of regular Convolutional layers. For downsampling, a stride of 2 was used. BatchNormalization and Leaky ReLU activation were used in all layers, except for the output, where Global Average Pooling followed by sigmoid were used.

#### Loss Function
The loss is a weighted sum of the Adversarial loss (binary crossentropy) and MSE loss between the Superesolved and the true High-reslution images.

## Results
<p align="left">
<img align = left width="445" height="215" src="https://user-images.githubusercontent.com/91228207/160922479-beedd0af-bbc5-40c8-be4c-7a49ac576b3c.png"/>
</p>
</ br>
</ br>
</ br>
</ br></ br>

<p>
<img align = center width="445" height="215" src="https://user-images.githubusercontent.com/91228207/160922487-31d603e6-1c77-4756-af4e-76383cfc318a.png"/>
</p>


## Remarks
- The model works reasonably well for its size and simplicity. However, there are most certainly a lot of improvments that can be made here. The largest drawback being that it produces images with facial features that are too smooth and lack details. 
- For this, perception loss can used in place of MSE loss as suggested by the [SRGAN paper](https://arxiv.org/pdf/1609.04802.pdf).
