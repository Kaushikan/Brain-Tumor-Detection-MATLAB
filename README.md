# Brain-Tumor-Detection-MATLAB
This project implements a Brain Tumor Detection system using deep learning techniques in MATLAB. The model is trained through transfer learning using the NasNetLarge Convolutional Neural Network (CNN).

## 📂 Contents
- **Dataset**: [Download Here](https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri)
- **Trained Model**: [Download Here](https://www.dropbox.com/scl/fi/e6hlb4nlr3gydmti2q06h/trainedNASNetLarge.mat?rlkey=3wnpuaar2jtzgg7ol5ip6ikas&st=c4kyxcrb&dl=0)
- **Usage Instructions**: Step-by-step guide on how to use the model

## 🔧 How to Use the Model
1. Download the trained model from the link above.
2. Open MATLAB and load the model.
```matlab
load('trainedNASNetLarge.mat')
```
3. Run the preprocessing steps on your MRI images.
```matlab
img = imread('path_to_image.jpg'); % Replace with the path to your image
imgResized = imresize(img, [224, 224]); %the input size of NasNetlarge is 224x224
% the network expects RGB but if the image is grayscale, convert it
if size(imgResized, 3) == 1  
    imgResized = repmat(imgResized, [1, 1, 3]); % Duplicate channels
end
```
4. Use the model to predict tumor presence.
```matlab
predictedLabel = classify(net, imgResized);
disp(['Predicted Label: ', char(predictedLabel)]);
```

## 📜 About the Trained Model
This model predicts four classes of brain tumors based on MRI scans:

- **Malignant Tumor**
- **Pituitary Tumor**
- **Glioma**
- **No Tumor**

The model is trained using **NasNetLarge** and has achieved:

- **Test Accuracy:** 95.88% (0.95881)
- Training was manually stopped, and further training might improve accuracy.

## Requirements

Ensure you have the following dependencies installed:

```bash
matlab
Deep Learning Toolbox
Image Processing Toolbox
```
## Contributing

Feel free to improve this model or add more features! Open an issue or submit a pull request.
