# Rebuttal Material: Hyperspectral Imaging with Random Printed Mask

# Comparative Experiment(#R1):

  ## Qualitative comparison:
> Fig. 1: Experimental results on captured image data. The synthetic RGB images, details and the spectral response of scene points are evaluated.

As shown in Fig. 1, the first column is the captured sharp gray image and the second column is the captured dispersive image. Based on the reconstructed multispectral images from these two measurements, the synthetic images by integrating with the camera response curve are shown in the third column. Physically captured RGB images by an additional RGB camera are in the forth column. Our hybrid system and pixel-wise reconstruction algorithm could cover the spatial details, as shown in the fifth and sixth columns. Futhermore, the spectral response curves are shown in the last column to directly verify effectiveness of our method. 
Scenes with different colors are captured especially blue to validate our algorithm.


  ## Quantitative comparison:

# Network structure (#R4)

# Details (#R2)



Different coefficients are used to represent the strength of different constraints which determines convergence speed of algorithm. Empirically, by monitoring the convergence direction of temporary variables, and different parameters are set by coarse-to-fine tuning method. It should be noted that these parameters are almost system-independent and fixed in both synthetic and real experiments.

For experimental reproducibility, hardware parameters are listed in the table below.

|  Sensor part number    | Aperture(F) |Exposure time(ms)|
| -------------------    | -------| ------------|
| FLIR GS3-u3-32S4C-C    |    1/8 | 30        |
| FLIR GS3-u3-32S4M-C    |    1/8 | 30        |


As for running time, the iterative method takes about 2 hours to converge on the Intel(R)Core(TM)i7-6700K CPU @4.00GHz hardware platform with 32.0G RAM.
