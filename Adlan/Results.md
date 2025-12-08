# Results 

In this section, we will summarise and analyse the results of implementing our models EfficientNet and ResNet.

**Comparing the Effectiveness of Both Models**

As expected given the model's more modern architecture, EfficientNet outperformed ResNet across various metrics, notably:

1. Accuracy: 74.15% vs 68.36%
2. Top-5 Accuracy: 94.75% vs 93.56%
3. Weighted F1-score: 0.7391 vs 0.6884

While tempting to conclude that EfficientNet is the better model, we need to also think about how each model translates to the specific application of self-driving cars.

Despite being more accurate, EfficientNet is computationally much slower. It can process about 17 images every second compared to ResNet's 51 images every second. For a car camera's typical 30 frames per second, EfficientNet's 17 images per second falls well below this threshold. This also translates to hypothetically scaling the project with 32 GPUs and 90% efficiency:

1. Projected inference time - 22.16 hours for EfficientNet and 7.45 hours for ResNet
2. Projected training time - 31 days for EfficientNet and 10 days for ResNet

What this means is that while EfficientNet is better at classifying signs, ResNet is actually better in practice - specifically for self-driving cars where there is a need to process images quickly enough so that the car can take corrective action. This really shows the importance of considering not just the accuracy of a model but its speed and feasibility. 

**Common Weaknesses**

Interestingly, both EfficientNet and ResNet struggled in a few similar ways.

The worst predicted classes include class 37 (straight or left), class 0 (speed limit 20km/h) and class 27 (pedestrian crosswalk ahead). Some signs were also often confused such as mixing up different kinds of speed limits and different kinds of directions

However, the most important finding to focus on is that class 0 (speed limit 20km/h) was frequently misclassified as class 2 (50km/h). This raises notable concern given that mixing up these two signs could have disastrous consequences such as a car automatically speeding up in a residential area and greatly increasing the chances of an accident. Because of this, further model tuning would likely involve overly punishing the model for making these kinds of mistakes and not treating all misclassifications with the same weight. 

Furthermore, combined with the fact that the accuracy of even the better model was still only 74.15% - it is difficult to justify the implementation of these models in the real-world where misclassifications are incredibly dangerous. However, this nicely motivates scaling the dataset by 1000x in order to improve how applicable these models are in real world, self-driving cars.



