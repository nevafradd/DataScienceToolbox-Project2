Below outlines a summary of the key steps in our EDA and pre-processing steps. For the full detail, please see the associated code.

**Exploratory Data Analysis** 

As usual, we carried out a few steps first to understand the dataset:
1.	Plotted the number of items in each class. Here, we see major class imbalance with some classes having 210 images whilst others had 2200+

<img width="940" height="350" alt="image" src="https://github.com/user-attachments/assets/130463ed-8d8d-4882-af05-fcd6e4595c5a" />

 
2.	Displayed five random items from each of the 43 classes to highlight the variation in brightness, pixelation and angle. Below, we can see an example of such variation, especially comparing the second and third picture from the left.
<img width="940" height="207" alt="image" src="https://github.com/user-attachments/assets/8208f26a-6406-497a-9039-3146af901d75" />

 
3.	Plotted distribution of the brightness of the pictures to inform potential data augmentation. However, given the large number of datapoints within each class and the benefit of having variation in the quality of the pictures, this did not seem necessary. 



**Pre-processing** 

Before training our model, we carried out the following steps:
1.	Normalised the size of the images given the variation in height and width as seen below:

<img width="854" height="260" alt="image" src="https://github.com/user-attachments/assets/7dca6e33-2bad-4ae0-b402-22e57288cd40" />

2.	Confirmed there are no missing values 
3.	Split training images in to 80% training and 20% validation 
4.	Used stratification to address the aforementioned class imbalance highlighted in the EDA 

Ultimately, these steps ensure our data is normalised through image resizing and that minority classes are sufficiently represented.



