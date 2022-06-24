# Lung-Segmentation
Creates a lung mask that can be used to segment lung region from X-ray images as shown :- 

###### Below shown are X-ray images followed by real_mask followed by created_mask using trained model. 

![masks (1)](https://user-images.githubusercontent.com/87748321/175514569-15884638-bb23-4b85-94e7-fda82523f523.jpg)

Many time we need lung image with lung area the only visible area. Example is pneumonia detection using X-ray image 
where, region of interest is lung area and rest area is of no use in detection.

Dataset used is Shenzhen-Hospital-CXR-Set that containes over 600 X-ray images and their respective hand drawn masks.

## Steps :- 

### Loading data :-
- Loading images and masks from corresponding folder and reshaping to (512,512,1) to each image.
- Splitting into training and testing set. (Validation set will be obtained using tranging data)
- Data augmentation by flipping each training image.

### Building Model and training:-
- Unet architecture is used. It uses skip connections to pass on low level feature informations to furthur layers 
and uses convolutional architecture to pass on features to next layers to eventually extract high level features.

![architecture_unetV2 (1)](https://user-images.githubusercontent.com/87748321/175516619-21b6205e-2aca-4663-8f91-7d590f9e198a.png)
- Batch Normalization were not used here

- Dice coefficient and Dice Coefficient loss is used as loss with Adam optimizer.
- Training is done for 30 epochs and 15 batch_size, vaidation_split = 0.2
- Binary_accuracy obtained = 98.33 %
- Val_binary_accuracy = 98.01 %

