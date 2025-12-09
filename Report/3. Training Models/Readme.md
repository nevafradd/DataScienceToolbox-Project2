The aim of this section is to simultaneously summarise and expand on some of the key decisions surrounding the implementation of our models: ResNet-18 and EfficientNet.

**1. Motivation behind the Models**

Firstly, EfficientNet and ResNet-18 contrast well given the aim and complexity of each model. ResNet-18 was crucial in tackling something called the 'vanishing gradient' problem, where neural networks that were trained on more and more layers would produce worse results as the model became confused. By allowing the model to skip layers, it helped solve this problem and also provided a foundation for other models to build upon. 

Conversely, EfficientNet, is more modern and focuses on optimising the width of each layer, the number of layers and the resolution (detail of the input). Because of this, we get to see two very different models: one that is foundational and one that is more modern and optimised.

Secondly, each model is appropriate for the computational requirements of this project. ResNet-18 refers to 18 layers being allowed in the model. There are also other versions like ResNet-18, ResNet-101 etc. Similarly, EfficientNet-B0 is a base, starting model that is meant to be fast to train with other models available like B1, B2 all the way to B7. Not only does this make sense computationally but it also leads nicely to the discussion around scaling because as we scale, we would start to look at these other variations of each model. 

**2. Stratification**

As it was shown in the EDA, the dataset has a huge imbalance between different classes with there being a roughly 2000 size difference between some of the largest and smallest classes. 

<img width="940" height="350" alt="image" src="https://github.com/user-attachments/assets/130463ed-8d8d-4882-af05-fcd6e4595c5a" />

This can create a problem where if we train our models, they might see very little of some of the minority classes leading to poor results when it comes to predicting those classes especially. Stratification just makes sure that each training sample has the same proportion of each class to prevent this. 

**3. Not using Auto Augmentation**

Augmentation is where we create artificial images to introduce additional variety to the dataset - increasing how well the model generalises to real world variation. 

These new images can involve modifying our existing images by rotating them, flipping them, distorting them, cropping them and so on. Auto Augmentation is simply where we automate this process of deciding what exact adjustments to make in order to create these new pictures. However, we have to be careful here because in the context of traffic signs - flipping an arrow for example completely changes its meaning which is why we do not use Auto Augmentation here. 

**4. Downsampling**

Downsampling is essentially reducing the amount of data our model has to work with. 

Models regularly took more than 2 hours to run given us being limited to the use of a CPU. Combined with limited time and us needing to rerun the models multiple times as we made certain adjustments - we needed a convenient solution. By reducing the proportion of each class by 50%, we reduced the time it took to run our models whilst ensuring that each class was similarly represented in the dataset. 

If we had more time or easy access to a strong GPU then we could simply run the models - however, downsampling allows us to obtain meaningful results within the scope of our project.

**5. Freezing the Backbone Layers**

What guides the implementation of both models in our project is the concept of transfer learning - the idea of taking these models that have already been trained on a massive dataset, and tailoring it to our dataset with the advantage of saving a lot of time in the process. This is why we 'freeze' the backbone layers and only change the last classifier layer so that instead of classifying the original 1000 classes, it classifies the 43 classes specific to our dataset. The backbone layers themselves are crucial in that they have already learnt a lot of general patterns like edges, shapes and different textures.





