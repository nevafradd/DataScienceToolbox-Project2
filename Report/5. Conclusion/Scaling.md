**Changes to scale our project**

Our chosen dataset contains 50,000 images with more than 40 classes. If we were to scale this by a factor of 1000, we would be working with around 50 million images. This would alter our approach in a few different ways. 

1.	Moving to cloud storage 
The main drawback of using GitHub and local storage on our laptops and computers is of course capacity. Platforms like Amazon S3, Google Cloud Storage or Azure Blob Storage not only solve this issue but reduce the chance of data corruption, allow for easy file access and have various backup options were anything to happen.

2.	Utilising multiple GPUs
For our project, we used a CPU given our lack of access to a proper GPU which works for our smaller dataset but would naturally struggle with a dataset much larger and more demanding. Implementing multiple, powerful GPUs at the same time would allow us to tackle different portions of the dataset simultaneously, improving speed and efficiency 

3.	Distributing data more efficiently 
In order to coordinate the use of our GPUs effectively, we could use a popular framework by PyTorch called DistriutedDataParallel. This involves splitting the data automatically, runs the same model on each GPU, shares the finding from each GPU and then finally updates all the different models. 

4.	Avoiding bottlenecks 

Another issue created by multiple GPUs is that although they are computationally much more powerful, they can only work as fast as the data that is being given to them. A CPU is much slower in comparison and especially at scale, this could mean that we have really long run times because of this bottleneck – commonly referred to as an input/output bottleneck. 
One way we can avoid this is by combining the image files in to much larger files like in to a TFRecord format which basically reduces the number of disk seeks. Secondly, we could use PyTorch DataLoader which allows us to use multiple CPUs.

5.	Handling GPU memory constraints 
An important consideration is that even with powerful GPUs, they are still have memory requirements we have to be wary of when working with so much data. One option is to use something called mixed precision training where we use 16 bit instead of 32 bit numbers. Although this reduces precision, it also halves the memory usage thus ensuring we do not exceed the limitations of the GPUs.


**Real-world application**
Wanting to scale this project also makes a lot of sense beyond just improving our model.


Given our dataset is specific to Germany, scaling would allow us to incorporate data from other countries. In the context of self-driving cars, this would help companies deploy cars more globally as they learn to navigate a wider variety of environments and regions with different signs and weather conditions. 

Also, our dataset is convenient in that the pictures of the signs does not show much of the background which is great for our project but not realistic. Scaling would allow us to consider the first step of identifying the sign within a landscape and then carrying out the classification task that we have done here.

Lastly, our use of cloud storage would allow for continuous learning as a self-driving car could easily add new pictures to the dataset for the model to retrain on. This would be especially helpful in edge cases where the dataset is more limited, such as where weather conditions like snow obscure a sign which the model may not be used to. 




