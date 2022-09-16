Implementing centralized and ADMM for multi agent path planning. Considering that $qij$ is the coordinate of agent $i$ in time step j we want to:<br />
![image](https://user-images.githubusercontent.com/19387425/190810574-20c80446-20d1-42c0-b0a1-39f71abbd8e7.png)<br />
Constraints for the centralized method:<br />
![image](https://user-images.githubusercontent.com/19387425/190810693-1c1eb2e2-952c-4df3-9f58-f6895ce24858.png)<br />
We need to solve following:<br />
![image](https://user-images.githubusercontent.com/19387425/190811116-98ee1f79-a057-4677-8ccd-cfb23e3b2af5.png)<br />
For ADMM the constraints are as follows:<br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/ADMM%20constraints.JPG)<br />
The $Lp$ function : <br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/Lp.JPG)<br />
Other constrains for ADMM:<br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/other%20constraints%20ADMM%20format.JPG)<br />
