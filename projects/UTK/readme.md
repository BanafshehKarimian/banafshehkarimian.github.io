For [UTKFace Data](https://susanqq.github.io/UTKFace/), we first implement Multi-layer Neural Network from scratch in order to use it as linear regression to predict age of each face. The inpute is normalized and its dimention is reduced to 128 features using PCA. Last layer loss is L2 and other layers have LeakyReLU activation function. The network learns using SGD with momentum of 0.9 . We then change the last layer of Part A to classify nationality of each face. We use Negative Log Likelihood loss function. Finally, we use Logistic Loss function to use Part A as logistic regression to predict the gender of each face. We compare loss per trial for the first phase for:
* zero weight initialization
* Xavier weight initialization
* -0.1 to 0.1 random weight initialization.
* He weight initialization
* STep decay learning rate adaption