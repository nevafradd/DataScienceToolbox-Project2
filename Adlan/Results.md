# Results 

In this section, we will compare how the models performed and discuss how we might scale this project. 

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

The worst predicted classes include class 37 (straight or left), class 0 (speed limit 20km/h) and class 27 (pedestrian crosswalk ahead). Some signs were also often confused such as mixing up different kinds of speed limits and different kinds of directions. 

<img width="930" height="224" alt="image" src="https://github.com/user-attachments/assets/82dc9ed5-b51c-4159-9c17-a26638261053" />

*Figure 1: Examples of misclassified traffic signs from our models. Each image shows the true sign (T) and what the model predicted (P).*

However, the most important finding to focus on is that class 0 (speed limit 20km/h) was frequently misclassified as class 2 (50km/h). This raises notable concern given that mixing up these two signs could have disastrous consequences such as a car automatically speeding up in a residential area and greatly increasing the chances of an accident. Because of this, further model tuning would likely involve overly punishing the model for making these kinds of mistakes and not treating all misclassifications with the same weight. 

Furthermore, combined with the fact that the accuracy of even the better model was still only 74.15% - it is difficult to justify the implementation of these models in the real-world where misclassifications are incredibly dangerous. However, this nicely motivates scaling the dataset by 1000x in order to improve how applicable these models are in real world, self-driving cars.

**Implementation of Scaling the Project**

Given our current training set contains around 39,000 images with more than 40 classes, our scaled project would involve working with around 39 million images. Now, let's discuss how we would actually implement this in practice.

Firstly, we would use cloud storage instead of GitHub. GitHub is great for smaller projects but isn't suitable for storing large file sizes. Furthermore, the platform lacks a lot of features we can find in cloud platforms like different backup options, easier accessibility and overall lower chances of data corruption or losses. Some examples include Amazon S3, Google Cloud Storage and Azure Blob Storage. These would be more than adquate to handle our dataset growing from around 2GB to 1.9 TB.

Secondly, unlike our project where we used a CPU to run the models, using not just one but multiple GPUs simultaneously would allow us to tackle different parts of the dataset at the same time. Our scaling analysis previously showed that with 32 GPUs and 90% efficiency, training would take 31 days under EfficientNet and 10 days under ResNet. To coordinate the use of these GPUs, we could use a framework like PyTorch's DistributedDataParallel which simply involves splitting the data, running the same model on each GPU and updating each model at the same time.

One key risk to look out for is the potential of a bottleneck created by the GPUs not receiving information fast enough - which we can refer to as an input/output bottleneck. A key way to avoid this is to reduce the number of disk seeks (loading each file one at a time) by combining the images in to larger chunks, for example putting them in to a TFRecord format. Additionally, we can use PyTorch DataLoader which allows the use of multiple CPUs to further keep up with the computational power of the GPUs. 

Finally, we can consider which model to implement at scale. Given that ResNet-18 ran 3 times quicker than EfficientNet, we must consider the tradeoff between speed and accuracy. Especially at scale, ResNet appears to be the more practical choice in spite of its lower accuracy. 





























