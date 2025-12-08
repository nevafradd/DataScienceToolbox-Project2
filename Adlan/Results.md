# Results 

In this section, we will summarise and analyse the results of implementing our models EfficientNet and ResNet-18.

**Comparing the Effectiveness of Both Models**

As expected given its more modern architecture, EfficientNet outperformed ResNet-18 across various metrics, notably:

1. Accuracy: 74.15% vs 68.36%
2. Top-5 Accuracy: 94.75% vs 93.56%
3. Weighted F1-score: 0.7391 vs 0.6884

Interestingly, however, this isn't the full story given that we must also consider how these are implemented in the real-world. 

Despite being more accurate, EfficientNet is computationally much slower. It can process about 17 images every second compared to ResNet-18's 51 images every second. For a car camera's typical 30 frames per second, EfficientNet would certainly struggle to keep up. This also translates to scaling where with 32 GPUs, inference time would be 22.16 hours for Efficient Net and 7.45 hours for ResNet-18. Training time would be 31 days for EfficientNet and 10 days for ResNet.

Ultimately, this means that while EfficientNet has better predictive power, ResNet-18 is often better in practice for self-driving cars - where high throughput is paramount.

**Common Weaknesses**

Both models struggled similary in a few different ways. The worst predicted classes include class 37 (straight or left), class 0 (speed limit 20km/h) and class 27 (pedestrian crosswalk ahead). Some signs were also often confused such as mixing up different speed limits and directions being confused with other directions.

However, the most crucial finding to bring attention to is class 0 (speed limit 20km/h) being frequently classified as class 2 (50km/h). This raises notable concern given that mixing up these two signs could have disastrous consequences such as a car automatically speeding up in a residential area and greatly increasing the chances of an accident. Because of this, further model tuning would likely involve overly punishing the model for making these kinds of mistakes and not treating all misclassifications with the same weight. 

Furthermore, combined with the fact that the accuracy of even the better model was still only 74.15% - it is difficult to justify the implementation of these models in the real-world where misclassifications are incredibly dangerous. However, this nicely motivates scaling the dataset by 1000x in order to improve how applicable these models are in real world, self-driving cars.



