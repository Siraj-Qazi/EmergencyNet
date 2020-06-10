# EmergencyNet

## Overview
There is a need to design specialized networks that are inherently computationally efficient to enable there use in resource contraint devices such as UAVs. The design space can be explored by focusing on the layer configurations, type and connectivity. An architecture is poropsed that allows for flexible aggregation of the multi-scale contextual information while keeping the same resolution and reduced number of parameters. It is based on the Atrous Convolutional Feature Fusion (ACFF) block. computes multiple such atrous convolutional
features for the same input map across different dilation rates. Each atrous convolution is factored into depth-wise convolution that performs lightweight filtering by applying a single convolutional kernel per input channel to reduce the computational complexity. An essential part of optimized CNNs is reducing not only the spatial size of feature maps but also the channel dimensions. Hence, prior to the atrous convolutions the input feature map channels are halved. This makes it possible to have multiple branches for atrous convolution without significantly impacting the performance. The depth reduction factor is a hyperparameter that can be further tuned depending on the requirements. The atrous convolutional features at different dilation rates need to be combined together to allow the unit to learn from representations from a large effective receptive field. The fusion mechanism is then followed by 1x1 convolutions and activation that non-linearly combine channel features together and projects them into a higher dimensional space.

The ACFF macro block is used as a starting point to build a deep neural network that is characterized by lowcomputational complexity and is suitable for embedded platforms. 
- Reduced Cost of First Layer: The first layer typically incurs the higher computational cost since it is applied across the whole image. Hence, a relatively small number of filters is selected (16)
- Early downsampling: Downsampling is performed at all the initial layers. A combination of stride and maxpooling layers are used in an effort to reduce the loss of information by aggressive striding
- Regularization: Due to the relatively small size of the dataset compared to databases such as ImageNet; additional regularization techniques are also incorporated

<img src="./Figures/Emergency_Net_ACFF.png" width="512">

<img src="./Figures/Android_App.jpg" width="512">

## Citation Information
Please cite the following paper if you find this is useful for your work: 

- C. Kyrkou and T. Theocharides, "EmergencyNet: Efficient Aerial Image Classification for Drone-Based Emergency Monitoring Using Atrous Convolutional Feature Fusion," in IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, vol. 13, pp. 1687-1699, 2020.[paper📜 ](https://ieeexplore.ieee.org/abstract/document/9050881)
