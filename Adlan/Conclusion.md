# Conclusion 

The overarching aim for our project was to use neural networks to classify traffic signs - specifically in the context of self-driving cars. Our chosen dataset was a natural option given that it was well documented, did not require deep expert knowledge and was overall very intuitive and easy for us to understand and work with.

As for our models, ResNet-18 and EfficientNet-B0 were great options because of how well they contrasted each other. Also, using each model's more basic versions was appropriate for the scope and size of this project and provided a great foundation for discussions of scaling later on. 

In terms of how they performed, EfficientNet was more accurate (74% vs 68%) but ResNet was 3 times faster (51 vs 17 images/second). This creates a stark trade off between both speed and accuracy. While EfficientNet is better in theory, ResNet ultimately is the more feasible option in practice given that it doesn't benefit a self-driving car to be more accurate in classifying signs if it cannot do it fast enough. However, while ResNet is the relatively more practical option, both models still fall short given their limited accuracy and tendency to dangerously confused certain signs like 20km/h and 50km/h signs. 

Despite these shortcomings, this links very nicely to further actions we could take if we had more time and resources.

Firstly, we could scale the project by 1000x which we would implement through a few key changes such as using cloud storage, using multiple GPUs and frameworks like DistributedDataParallel to coordinate them. Here, we would likely use ResNet for mentioned reason of it being practically feasible. 

Secondly, we could fine tune the models to overly punish dangerous misclassifications to improve the safety of the implementation of these models. Furthermore, we could use the more intensive versions of each models like ResNet-50 and EfficientNet-B3.

Thirdly, given that the traffic signs are already zoomed in to the traffic signs, we could train the model to first identify the sign from a larger landscape picture and then carry out the classification for a complete, implementable pipeline.

Hence, despite these models not being safe for real-world deployment in their current form, the work in this project creates a great foundation to build upon to improve the safety, speed and accuracy of these models in self-driving cars. 





