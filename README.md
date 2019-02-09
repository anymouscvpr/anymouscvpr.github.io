# Rebuttal Material: Hyperspectral Imaging with Random Printed Mask

# Comparative Experiment(#R1):

To further support the effectiveness and practicality of our method, we have done some comparative experiments. Qualitative and quantitative analysis of reconstruction results are conducted. 

## Qualitative comparison:
  
  ![link.png](https://postimg.cc/F7RfwRyS)
  
> Fig. 1: Simulation results. The synthetic RGB images, errormap over all bands and the spectral response of red scene point are provided.  The results from state-of-art Deep CASSI method(2017) are the second column  . All data is tested on the models given by the original author.The experimental results in third column is from the same CNN model as ours on RGB images. 
Campared with the third column, our idea of printed mask shows better results in terms of errormap and curves, which strongly support that the simple spectral imaging scheme provides a large number of uncorrelated spectral transmission curves to improve reconstructed performance. 
As we can see from the last two columns, printed mask may obtain more useful information and improve the reconstruction performance.



  ## Quantitative comparison:
  
|                        | Our CNN + RGB       |  Deep CASSI                  |Our method |
| -------------------    | ------------------------| -----------------------------|-----------|
| PSNR(dB)               |            21.15        |      34.47                   | 34.74     |
|  MSE                   |            0.03         |         0.001                | 0.0004    |
|  SSIM                  |       0.57              |         0.91                 | 0.93      |
| time(s)                |         0.007           |          1800                |  0.007    |
  
  Quantitative comparison was also performed. We verified on different test sets, the average of the results from the different datasets is given in the table.
  As can be seen from the above table, our method is not only practical and simple, but also maintains a good reconstruction performance, which provides a new idea for spectral image coding and acquisition. Our final goal is to implement an on-chip hyperspectral sensor,so we care more about the simplicity and practicality at this time. The main contribution of our paper is to propose a novel, low-budget spectral imaging method.
# Network structure (#R4)
![image](https://github.com/anymouscvpr/anymouscvpr.github.io/blob/master/network.jpg)

In order to increase the receptive field (RF) of the model and enable it to integrate the coded information by mask of different size level, a multiscale network model with skip connection is employed since down-sampling operation can effectively increase the observation matrix contains different characteristic information in various scale space. The spatial kenel size of convltional layers is 3×3. With nonlinear relu activation, the network allows for nonlinear reconstruction of hyperspectral information, which fits better the nonlinear nature of the problem, and thus leads to better results.

The network structure includes 4 downsamplings to extract features of different scales, spatial pixel of fearure map is  shrunk to half of the previous level after downsampling, and then  original size is maintained after 4 times of upsampling. Bottleneck  whose spatial size is the same as previous layer is added following upsampling to smooth the feature map.  Skipping connection are introduced in our network structure to combine the shallow information and deep feature domain. Sorry, there were some errors in the original schematic which may mislead readers and it is not on purpose. 


# Details (#R2 & #R4)

We thank #R2 for suggesting us to explain more important details about our experiment. Three EPSON XP-245 printers are used to print  colorful ink of different transmission curves on transparent non-deformable film. We investigated many inks on the market, for example 
C13T761280, C13T761380, C13T761480, C13T761580, C13T761680, LAMY T52-Cyan, T52-Magenta T52-Yellow, Pilot INK-30 series, etc. Finally, 7 inks with the weakest correlation of transmission curves are selected considering 3 camera response curves.

In practice, the ink-jet printer we used takes a long time to solidify each layer on the PET film, making it difficult to print too many layers. Since the rank improvement becomes small when the number of layer exceeds 14, we choose 14 layers instead of 50 in practice. which is much larger than the real magnification of our relay lens, leading tothe big visual difference. There are blurry in Fig.5,but it is not that obvious as in picture captured by 20X microscope. 
 It should be pointed out that the meaning of layers are not physically separate sheets but multiple prints on the same sheet.
