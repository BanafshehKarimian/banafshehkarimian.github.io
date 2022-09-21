The dataset we use is Camvid: <br />
https://s3.amazonaws.com/fast-ai-imagelocal/camvid.tgz<br />
http://mi.eng.cam.ac.uk/research/projects/VideoRec/CamVid/data/LabeledApproved_full.zip<br />
We implement SegNet Base from its paper: https://arxiv.org/abs/1505.07293<br />
The architecture of the SegNet is:<br />
![image](https://user-images.githubusercontent.com/19387425/191544843-50a27d51-26aa-4fd3-b77d-10f326ce7357.png)<br />
SegNet has 13 encoder (Convolutional layer with kernel 7x7 and stride 1 followed by ReLU and maxpooling down sampling with kernel 2x2 and stride 2)/decoder (Up sampling with saved edge features and Convolutional layer with kernel 7x7 and stride 1) layers and the output of the last layer is given to a softmax in order to produce a probability of each class for each pixel. The 2x2 maxpooling has the stride of 2, the loss function is cross entropy and SGD with fixed lr of 0.1 and momentum of 0.9 is used to train the network. Unlike SegNet, SegNet base uses only 4 encoder/decoder layers. <br />
Class N1 learns weights of the middle encoder decoder set. Class N2 freezes the learned weights from N1 and trains the third encoder with the second decoder. class N3 freezes the learned weights from N2 and trains the second encoder with the third decoder. Class N4 freezes the learned weights from N3 and trains the first encoder with the last decoder. <br />
The mentioned method, which is used in the paper, is time consuming, so we use NT that trains all 4 encoder/decoder paires at the same time.<br />
results without batch normalization:<br />
![image](https://user-images.githubusercontent.com/19387425/191544956-268f3bc6-83a0-4587-9be9-2fb4fe744f9a.png)<br />
![image](https://user-images.githubusercontent.com/19387425/191545045-2befca3e-12ac-4c57-983f-619bddb37bb2.png)<br />
results with batch normalization:<br />
![image](https://user-images.githubusercontent.com/19387425/191545152-5ce66956-9585-4bee-abfc-221f57a57660.png)<br />
![image](https://user-images.githubusercontent.com/19387425/191545283-c3b19617-0cb8-4b24-bd23-43e9cca907f7.png)<br />
