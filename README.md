# Rebuttal Material: Hyperspectral Imaging with Random Printed Mask

# Comparative Experiment(#R1):

To further support the effectiveness and practicality of our method, we have done some comparative experiments. Qualitative and quantitative analysis of reconstruction results are conducted. 

  ## Qualitative comparison:
  
  ![image](https://github.com/fjdksfj/fjdksfj.github.io/blob/master/more_res.png)
  
> Fig. 1: Simulation results. The synthetic RGB images, errormap over all bands and the spectral response of scene point are provided. The experimental results in second column is from the same CNN model as ours on RGB images. The third and forth column are respectively the state-of-art HSCNN(2017) and Deep CASSI method(2017)

Campared with the second column, our idea of printed mask shows better results in terms of errormap and curves, which strongly support that the simple spectral imaging scheme provides a large number of uncorrelated spectral transmission curves to improve reconstructed performance. 
Scenes with different colors are captured especially blue to validate our algorithm.

  ## Quantitative comparison:

# Network structure (#R4)
![image](https://github.com/fjdksfj/fjdksfj.github.io/blob/master/more_res.png)

# Details (#R2)



Different coefficients are used to represent the strength of different constraints which determines convergence speed of algorithm. Empirically, by monitoring the convergence direction of temporary variables, and different parameters are set by coarse-to-fine tuning method. It should be noted that these parameters are almost system-independent and fixed in both synthetic and real experiments.

For experimental reproducibility, hardware parameters are listed in the table below.

|  Sensor part number    | Aperture(F) |Exposure time(ms)|
| -------------------    | -------| ------------|
| FLIR GS3-u3-32S4C-C    |    1/8 | 30        |
| FLIR GS3-u3-32S4M-C    |    1/8 | 30        |


As for running time, the iterative method takes about 2 hours to converge on the Intel(R)Core(TM)i7-6700K CPU @4.00GHz hardware platform with 32.0G RAM.
