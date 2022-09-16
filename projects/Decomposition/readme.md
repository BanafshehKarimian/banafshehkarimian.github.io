Implementing centralized and ADMM for multi agent path planning. Considering that $qij$ is the coordinate of agent $i$ in time step j we want to:<br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/main.JPG)<br />
Constraints for the centralized method:<br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/centralized%20constraints.JPG)<br />
We need to solve following:<br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/centralized%20system%20inequality.JPG)<br />
For ADD the constraints are as follows:<br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/ADMM%20constraints.JPG)<br />
The $Lp$ function : <br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/Lp.JPG)<br />
Other constrains for ADMM:<br />
![](https://github.com/BanafshehKarimian/decomposition_methods/blob/main/img/other%20constraints%20ADMM%20format.JPG)<br />
