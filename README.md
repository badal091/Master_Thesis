# Master's Thesis

# Cross-Attention and ViT for Multi-Task Learning

Our main objective is to leverage vision transformer (ViT) and cross-attention take it from classification tasks to semantic segmentation and then later to multi-task learning, by designing new models that incorporate both concepts.

Multi task learning include classification, semantic segmentation, monocular depth estimation & surface normal estimation etc.

<img src="https://github.com/badal091/Master_Thesis/assets/103456016/3555dda8-0f75-45bf-a1bc-bf4e3b742fc8" width="500" height="500" />


## New Architecture
Original image size: 128x256x3

Small Branch: 8x8x3 patch 

Large Branch: 16x16x3 patch

Obtain their feature embedding and pass through a self-attention network

![image](https://github.com/badal091/Master_Thesis/assets/103456016/2bd8993c-f0d7-4929-924a-116bd66a8dc2)



Exchange the tokens and do the cross-attention.

Reshape:

Small Branch: 512x256 to 16x32x256

Large Branch: 128x256 to 8x16x256

Upconvolve to give output of size: 128x256x256

![image](https://github.com/badal091/Master_Thesis/assets/103456016/69aa09c6-8d7e-474a-9486-93596ca9b6c6)





Add X1 and X2 elementwise and apply last cnn layer to give output of 8 channels ( num classes = 8).

![image](https://github.com/badal091/Master_Thesis/assets/103456016/a4b18d36-3402-4734-b201-a5b74ad7da36)

## Experiment Conducted & Metric Used

1. Citiscapes dataset with 8 classes was used to train and test the model
2. mIOU and pixel accuracy was the metric used to determine the performance.
3. pixel accuracy is basically, total number of correctly predicted pixel / total pixels.
4. IOU is quantifies the overlap between the predicted bounding box and the ground truth bounding box from a dataset.
5. Cross-Entropy and Dice loss were considered
6. Dice loss measures the overlap between the predicted and target segmentation masks

Hyper-parameters:

1. Num Epochs = 40
2. LR = 0.001
3. Batch Size =32

## Results & Observation

1. We obtained mIoU of 84.76% on testing data

![image](https://github.com/badal091/Master_Thesis/assets/103456016/9b76b077-5b5f-4cf2-a4cd-3f2acb4cebed)

Example-1

![image](https://github.com/badal091/Master_Thesis/assets/103456016/0e5e66f6-55af-409b-9b95-c0cd07089a27)

Example-2

![image](https://github.com/badal091/Master_Thesis/assets/103456016/d3c27ca8-9531-4f1c-a847-a5533ee5cf44)

