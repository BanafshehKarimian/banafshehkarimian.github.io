Implementing centralized and ADMM for multi agent path planning. Considering that $qij$ is the coordinate of agent $i$ in time step j we want to:<br />
![image](https://user-images.githubusercontent.com/19387425/190810574-20c80446-20d1-42c0-b0a1-39f71abbd8e7.png)<br />
Constraints for the centralized method:<br />
![image](https://user-images.githubusercontent.com/19387425/190810693-1c1eb2e2-952c-4df3-9f58-f6895ce24858.png)<br />
We need to solve following:<br />
![image](https://user-images.githubusercontent.com/19387425/190811116-98ee1f79-a057-4677-8ccd-cfb23e3b2af5.png)<br />
For ADMM the constraints are as follows:<br />
![image](https://user-images.githubusercontent.com/19387425/190811568-c089020f-7d9f-49aa-a5c0-f18490c3f0a6.png)<br />
The $Lp$ function : <br />
![image](https://user-images.githubusercontent.com/19387425/190811642-c1633419-8105-4393-a40a-6d7ff59e4d2b.png)<br />
Other constrains for ADMM:<br />
![image](https://user-images.githubusercontent.com/19387425/190811735-2b8e87d7-9aa3-4f39-a11b-4b53c034107e.png)
