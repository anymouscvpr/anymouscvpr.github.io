# Rebuttal Material: Hyperspectral Imaging with Random Printed Mask

# Comparisons with the state-of-the-art CNN based methods(#R1):

To further demonstrate the effectiveness and practicality of our method, we have conducted more comparison experiments with the CNN based methods, both qualitatively and quantitatively. 

## Qualitative comparisons:
  
  [![link.png](https://i.postimg.cc/wT5hyR3w/link.png)](https://postimg.cc/F7RfwRyS)
  
> Fig. 1: Simulation results. The synthetic RGB images, errormaps and the spectral response of red scene point are provided.  The second column are the results of the state-of-the-art CNN method, i.e. Deep CASSI method [8]. (Note that the models are provided by the original author.) The third column are the results of our CNN model trained to recover hyperspectral images from RGB images. 

Our method achieves significantly better results compared with the third column, in terms of both the errormaps and spectral curves. This comparison demonstrate the large performance improvement by the randomly printed color mask individually and the importance of introducing uncorrelated spatial-spectral encoding of our color mask.

Compared with the second column, our method achieves comparable reconstruction results as the state-of-the-art CNN based methods. Demonstrating the effectiveness of our method.


  ## Quantitative comparison:
  
|                        | Our CNN + RGB       |  Deep CASSI                  |Our method |
| -------------------    | ------------------------| -----------------------------|-----------|
| PSNR(dB)               |            21.15        |      34.47                   | 34.74     |
|  MSE                   |            0.03         |         0.001                | 0.0004    |
|  SSIM                  |       0.57              |         0.91                 | 0.93      |
| time(s)                |         0.007           |          1800                |  0.007    |
  
  Quantitative comparison is also performed. As shown in the table, we compared our method with different methods. Compared with the our CNN network trained to recover hyperspectral images from RGB images, our method could recover significantly better results and demonstrate the importance of introducing the proposed color mask for spectral information retrieval. Further, we compare with the state-of-art CNN based hyperspectral imaging method (Deep CASSI [8]). As shown, our method achieves comparable PSNR/MSE/SSIM results with it, while our method runs signigicantly faster,further demonstrate the effectiveness of our proposed method.
  
  In conclusion, we proposed a novel, low-budget and efficient hyperspectral imaging method, which is quiet promising for wide applications.
  
# Network structure (#R4)
![image](https://github.com/anymouscvpr/anymouscvpr.github.io/blob/master/network.jpg)

We thank #R4 for pointing out the mistakes and we have fixed the mistakes in the original schematic which may mislead readers. In order to increase the receptive field (RF) of the model and enable it to integrate the coded information by mask of different size level, a multiscale network model with skip connection is employed since down-sampling operation can effectively increase the observation matrix contains different characteristic information in various scale space. The spatial kenel size of convltional layers is 3×3. With nonlinear relu activation, the network allows for nonlinear reconstruction of hyperspectral information, which fits better on the nonlinear nature of the problem, and thus leads to better results.

The network structure includes 4 downsamplings to extract features of different scales, spatial pixel of feature map is  shrunk to half of the previous level after downsampling, and then the original size is maintained after 4 times upsampling. Bottleneck whose spatial size is the same as previous layer is added following upsampling to smooth the feature map. Skip connection are introduced in our network structure to combine the shallow depth information and deep feature domain. 


# Details (#R2 & #R4)

We thank #R2 for suggesting us to explain more important details about our experiment. As for the printer type, three EPSON XP-245 printers are used to print  colorful ink of different transmission curves on transparent non-deformable film. We investigated many inks on the market, for example 
C13T761280, C13T761380, C13T761480, C13T761580, C13T761680, LAMY T52-Cyan, T52-Magenta T52-Yellow, Pilot INK-30 series, etc. Finally, 7 inks with the weakest correlation of transmission curves are selected besides the 3 camera response curves of Bayer filter.
And we can adjust the diameter of the ink droplet by changing of the relay lens. As we known that the CMYK color model is used in color printing, so we can set the density of each C M Y K channel of  CMYK image to control the distribution density of the droplets.

In practice, the ink-jet printer we used takes a long time to solidify each layer on the PET film, making it difficult to print too many layers. Since the rank improvement becomes small when the number of layer exceeds 14, we choose 14 layers instead of 50 in practice. There are blurry in Fig.5,but it is not that obvious as in picture captured by 20X microscope which is much larger than the real magnification of our relay lens, leading to the big visual difference. 
 It should be pointed out that the meaning of layers are not physically separate sheets but multiple prints on the same sheet.
 
 
