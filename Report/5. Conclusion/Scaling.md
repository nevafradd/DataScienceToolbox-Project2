**Changes to scale our project** 

Our chosen dataset contains 50,000 images with more than 40 classes. Scaling this by a factor of 1000 would mean we would have around 50 million images. Here are the changes we would make:

Storage – Given the limited storage using GitHub or storing data locally on our computers, we would opt for cloud storage such as Amazon S3, Google Cloud Storage or Azure Blob Storage. These platforms also offer improved backup features with 99.999999999% durability and 99.99% availability. 

Hardware – Currently for the models we utilised a CPU given the lack of easy access to a GPU – this, however, would lead to very long runtimes at scale. Instead, we would implement multiple GPUs at the same time which would be able to process different portions of the dataset simultaneously.

Data Distribution – To take full advantage of the aforementioned hardware, we would then need software to coordinate them. PyTorch’s framework DistributedDataParallel is a popular choice that splits the data automatically, runs the same model on each GPU, shares each GPUs findings and then updates all the different models.

I/O Bottleneck – Although we might have the strong computational power of our GPUs, they can be limited by the speed at which data arrives and leaves especially given the relatively slower speed of a CPU thus creating an input/output bottleneck. To avoid opening each image individually, we would shard images in to TFRecord formats which are larger files that reduce disk seeks. Using PyTorch DataLoader would also allow the use of multiple CPUs.

GPU Memory Limitations – Even with powerful GPUs, they are still limited by their memory. To address this, we could use mixed precision training where we use 16 bit instead of 32 bit numbers which would lowers numerical precision but halves memory usage.


**Real-world application**

There exists great motivation to scale this project.

Firstly, we would be able to train our models on data beyond the scope of Germany to other countries and regions with different traffic sign symbols. In the context of self-driving cars, this would encourage the deployment of self-driving cars more globally as they learn to navigate different environments. 

Furthermore, we could expand the pipeline to include firstly the identification of the sign from an image including the full landscape and then the task of classifying the actual sign to more closely resemble the real-world conditions a self-driving car would have in practice. 

Also, the use of cloud more easily enables continuous learning meaning that new edge cases (such as a sign being obscured by snow) can be easily added to the dataset so that the model can be retrained and accommodate more and more information. 


**Summary of Scaling Strategy** 

To summarise, if we were to scale the data by 1000 times we would implement:
-	Cloud storage for capacity and easily accessible data 
-	Multi-GPU clusters coordinated using DDP for parallel training 
-	Optimised data pipelines to avoid I/O bottlenecks 
-	Mixed precision training to prevent GPU memory limitations

Together, these changes create a scalable strategy capable of handling 50 million images and supporting continuous model development.  



