We use flickr8K dataset that has 5 captions for each traing image:<br />
https://www.kaggle.com/adityajn105/flickr8k <br />
After adding start and end tokens to the caption and assigning an index to words, we embed the captions. The following two architecture are relatively used in training and testing the model. We compare results with and without freezing the reznet part of the architecture.<br />
![image](https://user-images.githubusercontent.com/19387425/191543268-c1052744-698e-4ef4-954a-b7885e3ed0d3.png)<br />
![image](https://user-images.githubusercontent.com/19387425/191543374-c2e9a1f7-0332-4330-ad79-bfa7481c5af0.png)<br />
A sample of the result:<br />
![image](https://user-images.githubusercontent.com/19387425/191543476-91e8cb25-5c8c-4824-9d56-a0ce28d64d0c.png)
