# shop_classication_slash_dataset

# Dataset Overview
The dataset includes images categorized into different classes, such as Accessories, Beauty, Fashion, Home, Games, Stationary, and Nutrition. Each class contains a varying number of images, resulting in an imbalanced distribution across categories.
The dataset suffers from imbalanced class distribution, with Fashion dominating and other classes having significantly fewer samples. 
Number of classes: 7
Total number of images: 768
Number of images per class:
Accessories: 83
Beauty: 47
Fashion: 359
Games: 36
Home: 112
Nutrition: 29
Stationary: 102

# Dataset Structure
The dataset is structured as follows:
<p class="has-line-data" data-line-start="0" data-line-end="20">slash-data/<br>
├── Accessories/<br>
│   ├── Accessories1.jpg<br>
│   └── …<br>
├── Beauty/<br>
│   ├── Beauty1.jpg<br>
│   └── …<br>
├── Fashion/<br>
│   ├── Fashion1.jpg<br>
│   └── …<br>
├── Home/<br>
│   ├── Home1.jpg<br>
│   └── …<br>
├── Games/<br>
│   ├── Games1.jpg<br>
│   └── …<br>
├── Stationary/<br>
│   ├── Stationary1.jpg<br>
│   └── …<br>
└── Nutrition/</p>
    ├── Nutrition1.jpg <br>
    └── ... </br>
 

# Preprocessing Images for EfficientNet Model 
To ensure compatibility with the EfficientNet model, which requires input images of size 224x224x3, we must preprocess the dataset.<br>
Preprocessing Steps</p>
<ol>
<li class="has-line-data" data-line-start="3" data-line-end="5">Padding:<br>
Add uniform padding to the shorter sides of the images to make them square. This step avoids distortion during the resize process.</li>
<li class="has-line-data" data-line-start="5" data-line-end="7">Resize:<br>
Resize the padded images to 224x224 pixels. This step is crucial for maintaining a consistent input size for the model.</li>
<li class="has-line-data" data-line-start="7" data-line-end="11">To_Tensor and Normalize:<br>
Convert the resized images into PyTorch tensors. This conversion facilitates the utilization of GPU acceleration during training.<br>
Normalize the tensor pixel values using the mean [0.485, 0.456, 0.406] and standard deviation [0.229, 0.224, 0.225] values. Normalization standardizes the input data and improves model convergence.</li>
</ol>

# Oversampling To deal with Imbalanced Dataset: 
Strategy: Increase the number of instances in under-represented classes.<br>
Implementation: Use oversampling techniques to augment the minority classes either by duplicating existing images or applying image augmentation techniques to create plausible variations. This approach aims to achieve a more balanced class distribution, enhancing model performance on minority classes.</p>

# Modified EfficientNet Model Architecture

The `ModifiedEfficientNet` class is a neural network model designed for multi-class classification tasks. It is based on the EfficientNet architecture with custom modifications.

## Model Components:

- Convolutional Layers
- Transpose Convolutional Layer
- Base EfficientNet Model

**Note:**
- The model parameters are optimized using the Adam optimizer with a learning rate of `0.001`.
- The loss function used for optimization is the Cross Entropy Loss.

## Training Results:

After training the `ModifiedEfficientNet` model for 20 epochs, the following results were obtained:

- Average Train Loss: 0.0047
- Validation Accuracy: 85.22%
- Test Accuracy: 87.93%

