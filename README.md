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
  
  Quantitative comparison was also performed. As can be seen from the above table, our method is not only practical and simple, but also maintains a good reconstruction performance, which provides a new idea for spectral image coding and acquisition.

# Network structure (#R4)
![image](https://github.com/anymouscvpr/anymouscvpr.github.io/blob/master/network.jpg)

In order to increase the receptive field (RF) of the model and enable it to integrate the coded information by mask of different size level, a multiscale network model with skip connection is employed since down-sampling operation can effectively increase the observation matrix contains different characteristic information in various scale space. The spatial kenel size of convltional layers is 3×3. With nonlinear relu activation, the network allows for nonlinear reconstruction of hyperspectral information, which fits better the nonlinear nature of the problem, and thus leads to better results.

The network structure includes 4 downsamplings to extract features of different scales, spatial pixel of fearure map is  shrunk to half of the previous level after downsampling, and then  original size is maintained after 4 times of upsampling. Bottleneck  whose spatial size is the same as previous layer is added following upsampling to smooth the feature map.  Skipping connection are introduced in our network structure to combine the shallow information and deep feature domain. Sorry, there were some errors in the original schematic which may mislead readers and it is not on purpose. 


# Details (#R2)

We thank #R2 for suggesting us to explain more important details about our experiment. Three EPSON XP-245 printer are used to print  colorful ink of different transmission curves on transparent non-deformable film. We investigated many inks on the market, for example 
C13T761280, C13T761380, C13T761480, C13T761580, C13T761680
When print the mask, we pay more attention to try different print parameters because different parameters determine different inkjet mode which can influence the diameter of ink droplets. For instance, we set type of printing paper as epson rough paper with high print quality in which situation the diameter is equal to 4. In addition, we control density through setting different CMYK concentrations when we make the print source.Fig5 shows different pseudo-color mask with different parameters.贴图
