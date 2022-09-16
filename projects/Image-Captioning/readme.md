We use flickr8K dataset that has 5 captions for each traing image:<br />
https://www.kaggle.com/adityajn105/flickr8k <br />
After adding start and end tokens to the caption and assigning an index to words, we embed the captions. The following two architecture are relatively used in training and testing the model. We compare results with and without freezing the reznet part of the architecture.<br />
![training the model](https://github.com/BanafshehKarimian/Image-Captioning/blob/main/1.PNG)<br />
![testing the model](https://github.com/BanafshehKarimian/Image-Captioning/blob/main/2.PNG)<br />
A sample of the result:<br />
<p align="center">
  <img src="https://github.com/BanafshehKarimian/Image-Captioning/blob/main/resultsample.PNG" alt="A sample of the result"/>
</p>
[Github Link](https://github.com/BanafshehKarimian/Image-Captioning)
