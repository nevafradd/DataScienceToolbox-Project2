# EDA and Evaluation

This will be a summary of the EDA and (Billy's) evaluation of the German Traffic Sign dataset.

## EDA

The EDA conducted clearly shows large disparities in the data. The initial plot of class distributions demonstrate that class size varies immensely, with some classes having over 2000 images and others only containing roughly 200. This will lead to an underrepresentation of certain classes in the training set, and this issue may be clouded due to high accuracy being dominated by the larger classes. Following this, we generated random images from the training set to better understand the data. This was then repeated class-wise, making it easier to spot any common extremeties - lighting, blurriness, rotation, obstruction and so on. The differences in images drastically hinders our models capability of accurately determing the correct class type, perhaps explaining the difficulty in classifying certain classes. We then looked at the resolution of images in the training set and witnessed large variations in the height and width of images, further reinforcing our need for preprocessing, particularly resizing and normalisation, of the data. A brief analysis of pixel distribution was then conducted, and then we moved onto image augmentation. This concludes our EDA and, even without expert knowledge, it is clear what the issues are with said data and how we aim to overcome them. This naturally leads us into training the models, which will not be discussed here but can be found in either Neva or Gracie's folders, or in the report folder. A more developed EDA could examine specific details more in depth. The next section discusses the findings, impact, scope and journey of my evaluation.

## Evaluation

finish eval soon. talk about changes in models and impact on evaluation and EDA and summarise MY evaluation (my folder)
