# Introduction 

Firstly, we shall outline our initial exploration and the different options we considered.

**Deciding on our area**

We explored datasets across a range of sources from Kaggle to 	Hugging Face. Below outlines the main options we explored. 

Our first consideration was predicting house prices based on metadata and imaging. Although this would have been quite intuitive and very practical, we struggled to find housing images. For example, Willow offers a comprehensive range of housing data, but this was limited to metadata. There was the option of manually scraping housing images, but this would have been too computationally intensive and would have likely resulted in an inconsistent dataset.  

The next area we considered was medical data. Given the common use of x-rays, we had a range of options from predicting bone fractures and brain tumours. Bone fractures seemed a bit too simple, and it was also difficult to justify the need for scaling. Conversely, brain tumours were too complex given our lack of knowledge around different parts of the brain. 
Finally, we decided on classifying different traffic signs. Not only did this task have a very tangible impact, but it would also allow us to not get distracted by having to have specific expert knowledge. Furthermore, scalability seemed justifiable given:
1.	The dataset was specific to Germany so our model could be expanded to different countries 
2.	Given our images were exactly fitted to the sign, we could involve the wider timeline of having the model first identify the sign from a larger picture 

**Choosing our specific dataset** 

Our chosen dataset was better than others in the traffic area domain in a few key areas:

Size – other datasets were either too small which would lead to less interesting results or too large, requiring intense computational power. At more than 50,000 images, our dataset finds a balance between the two 

Comprehensive – with more that 40 different classes, we have enough complexity to take advantage of our neural network and increase the applicability of our results to the real world 

Documentation – being one of the most upvoted datasets with 537 different codes written for it, we benefit from an extensive list of examples of approaches to the data, helping to contrast our own work and improve our own approach 


**Finalising our question**

The dataset naturally lends itself to the task of classifying images of different traffic signs. This is further motivated by the increasing use of self-driving cars and the topical implementation of AI. Not only can we explore neural networks, but we can also produce a tangible result surrounding the ability of self-driving cars to navigate roads which has real world, tangible consequences. 
