# Biomedical Image Segmentation with U-Net  -  ISBI Challenge

## Data Augmentation

Data augmentation is essential when the available dataset isn't sufficient for achieving high accuracy. After exploring various techniques, I selected the most relevant ones from the Albumentations library. This choice was made due to complexities in integrating masks and images in the same iteration of augmentation, which I encountered when exploring other solutions. Albumentations offers a more flexible and functional approach compared to torchvision.

### Augmentation Techniques:

#### Crop Related transformations

- **Random Resized Crop**: This involves randomly cropping a section of the image and then rescaling it to the original size using bilinear interpolation.

#### Non destructive transformations

- **Horizontal Flip**: This creates a mirrored image along the y-axis.

- **Vertical Flip**: This creates a mirrored image along the x-axis.

- **Random Rotate 90**: It randomly rotates the image by 90 degrees or more in a random direction.

- **Transpose**: This swaps the rows with columns.

#### Non-rigid transformations:

These introduce distortions that affect the spatial orientation of the image.

- **Elastic Transformation**: This method displaces each pixel to a new location, subject to linear transformation restrictions. It includes operations like rotation and scaling.

- **Grid Distortion**: While the exact explanation is elusive, it's particularly recommended for medical imaging.

- **ShiftScaleRotate**: This applies random affine transformations, including translation, scaling, and rotation to the input.

#### Non-spatial stransformations:

These do not change the orientation of the image, but alter pixel values for augmentation. No changes are made in the mask.

- **CLAHE**: This breaks the image into tiles and evenly spreads out the contrast in each tile based on a histogram distribution. A threshold is set to avoid enhancement of low contrast areas.

- **Random Brightness Contrast**: This randomly adjusts brightness and contrast.

- **Color Jitter**: This applies random changes to brightness, contrast, and saturation.



### U-Net Architecture and Model Application

The U-Net architecture has been selected for this biomedical image segmentation task. It's considered one of the most influential architectures in this field. I'm currently researching transformers to incorporate recent advancements into the model.

### Optimization Algorithm - Adam

Adam is chosen as the optimization algorithm. Its primary goal is to reach the global minima of the cost function as quickly as possible. It achieves this through two means: Gradient Descent with momentum and RMSProp.

### Loss Function - Mean Squared Error (MSE)

MSE, a simple loss function, calculates the squared difference between predicted values and ground truth, then takes the mean over the entire batch. I experimented with various other losses to address class imbalance, but found MSE to yield higher Intersection over Union (IoU) on the validation dataset.

### Batch Size and Gradient Descent Algorithms

Mini-batch gradient descent is employed for computational efficiency and stability. This approach strikes a balance between the computationally intensive batch GD and the potentially uncertain stochastic GD.

### Evaluation Metric - Intersection over Union (IoU)

IoU measures the overlap between the predicted mask and the ground truth. It's a critical evaluation metric for assessing the accuracy of the segmentation model.

This comprehensive approach encompasses data augmentation, model architecture, optimization algorithms, loss functions, and evaluation metrics to achieve accurate biomedical image segmentation.


