# Rebuttal Material: Hyperspectral Imaging with Random Printed Mask

# Comparative Experiment(#R1):

To further support the effectiveness and practicality of our method, we have done some comparative experiments. Qualitative and quantitative analysis of reconstruction results are conducted. 

  ## Qualitative comparison:
  
  ![image](https://github.com/anymouscvpr/anymouscvpr.github.io/blob/master/network.jpg)
  
> Fig. 1: Simulation results. The synthetic RGB images, errormap over all bands and the spectral response of scene point are provided. The experimental results in second column is from the same CNN model as ours on RGB images. The third and forth column are respectively the state-of-art HSCNN(2017) and Deep CASSI method(2017)

Campared with the second column, our idea of printed mask shows better results in terms of errormap and curves, which strongly support that the simple spectral imaging scheme provides a large number of uncorrelated spectral transmission curves to improve reconstructed performance. 


  ## Quantitative comparison:
  
|                        | Our Network + RGB       | HSCNN + RGB       | Deep CASSI + random mask |Our method |
| -------------------    | ------------------------| ------------------|--------------------------|-----------|
| PSNR                   |    1/8                  | 30        |
| MSE                    |    1/8                  | 30        |
| time(s)                |    1/8                  | 30        |
  
  Quantitative comparison was also performed. 

# Network structure (#R4)
![image](https://github.com/anymouscvpr/anymouscvpr.github.io/blob/master/network.jpg)

In order to increase the receptive field (RF) of the model and enable it to integrate the coded information by mask of different size level, a multiscale network model with skip connection is employed since down-sampling operation can effectively increase the observation matrix contains different characteristic information in various scale space. The spatial kenel size of convltional layers is 3×3. With nonlinear relu activation, the network allows for nonlinear reconstruction of hyperspectral information, which fits better the nonlinear nature of the problem, and thus leads to better results.

The network structure includes 4 downsamplings to extract features of different scales, spatial pixel of fearure map is  shrunk to half of the previous level after downsampling, and then  original size is maintained after 4 times of upsampling. Bottleneck  whose spatial size is the same as previous layer is added following upsampling to smooth the feature map.  Skipping connection are introduced in our network structure to combine the shallow information and deep feature domain. Sorry, there were some errors in the original schematic which may mislead readers and it is not on purpose. 


# Details (#R2)



Different coefficients are used to represent the strength of different constraints which determines convergence speed of algorithm. Empirically, by monitoring the convergence direction of temporary variables, and different parameters are set by coarse-to-fine tuning method. It should be noted that these parameters are almost system-independent and fixed in both synthetic and real experiments.

For experimental reproducibility, hardware parameters are listed in the table below.



As for running time, the iterative method takes about 2 hours to converge on the Intel(R)Core(TM)i7-6700K CPU @4.00GHz hardware platform with 32.0G RAM.
