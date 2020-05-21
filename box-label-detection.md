
## Context

**Problem:** Given an image of a box face, detect the presence of a symbol. (e.g. biohazard) 

**Solution:** Object detection

### Object detection vs Image Classification

![Object detection predictions produced by YOLO](https://pjreddie.com/media/image/Screen_Shot_2018-03-24_at_10.48.42_PM.png)

- Object detection is an extension of image classification.
  - **bounding box** is drawn around objects
  - **training data** consists of bounding boxes that are manually drawn and labeled
  - **accuracy** is the amount of overlap between the predicted bounding box and the ground truth bounding box
- Object detectors are usually composed of two parts
  - **backbone**
    * pre-trained on ImageNet
    * converts input image into latent representation (features)
  - **head**
    * predict classes
    * predict bounding boxes of obj

## Approaches

We consider two types of learning used in object detection:

1. Standard, requires training data for each predicted class
2. **One shot learning**, can detect unseen objects given just **one** example.

### Standard models

Examples: YOLO, SSD, RetinaNet, R-CNN

- Require hundreds of examples for each class.
- **Transfer learning is possible** [See here](https://github.com/alankbi/detecto#transfer-learning-on-custom-datasets)
  * Requires at least 100 hand labeled examples
  * Can create bounding box training set using a tool like [labelImg](https://github.com/tzutalin/labelImg)

### One shot learning

Research paper: [One-shot query based symbol detection framework](https://arxiv.org/pdf/1811.01395.pdf),  [Source code](https://github.com/AyanKumarBhunia/Deep-One-Shot-Logo-Retrieval)

* Only requires one example of the symbol itself
* Handles multi-scale
* At this time, this method appears to be the most productive for our use case
  + Ideally we won't need to put together a domain specific data set
  + the architecture uses off-the-shelf neural network components  


### Choosing an approach

- Factors to consider when choosing an approach
  * ease of implementation
  * time spent preparing data vs implementation
  * performance
    + operates in real time?
  * accuracy
  * degree of generalization/scalability (e.g. query based)
  * dense vs sparse predictions
    + can it handle multiple overlapping objects?







