This section seeks to summarise and expand on some of the key decisions made in the implentation of the EfficientNet and ResNet18 models.

**Motivation behind the models**

Firstly, EfficientNet and ResNet18 contrast well given their style of architecture. ResNet18 tackled the 'vanishing gradient' problem, where neural networks trained on more and more layers would produce worse results as the model became confused. By allowing the model to skip layers, it provided a foundation for other models to build upon. EfficientNet, in contrast, is more modern and focuses on optimising the width of each layer, the number of layers and the resolution (detail of the input). As a result, we get to contrast a more foundational, standard model with a more recent, optimised one to see how the model performs in both cases.

Secondly, each model 

**Avoiding the use of Auto Augmentation**

Augmentation involves creating artificial images to introduce additional variety to the dataset to increase how well the model generalises to real world variation. These new images can involve modifying our existing images by rotating them, flipping them, distorting them, cropping them and so on. Auto Augmentation is simply where we automate this process of deciding what adjustments to make in order to create these new pictures. However, we have to be careful here because in the context of traffic signs - flipping an arrow for example completely changes its meaning which is why we do not use Auto Augmentation here. 

**Downsampling**

Downsampling is essentially reducing the amount of data our model has to work with. Models regularly took more than 2 hours to run given us being limited to the use of a CPU. Combined with limited time and us needing to rerun the models multiple times as we made certain adjustments - we needed a convenient solution. By reducing the proportion of each class by 50%, we reduced the time it took to run our models whilst ensuring that each class was similarly represented in the dataset. 

If we had more time or easy access to a strong GPU then we could simply run the models - however, downsampling allows us to achieve meaningful results within the scope of our project.



