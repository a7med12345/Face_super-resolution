# Face Super-resolution:

1- Generating low and high resolution faces:

1-1 Generating Low resolution faces:

Similar to [[1]](https://www.adrianbulat.com/downloads/ECCV18/image-super-resolution.pdf), 
to generate low resolution faces, we apply  [Single Shot Scale-invariant Face Detector
](https://arxiv.org/pdf/1708.05237.pdf) on [wider dataset](http://shuoyang1213.me/WIDERFACE/
) and select the results with confidence greater than 80% and with maximum(width,heigth) < 37.

An example of the dataset upsampled to (64,64) with bicubic method.
![alt text](images/epoch002_real_LRv.png "Example of low resolution dataset").

In [this link](https://drive.google.com/file/d/1qeY_q2dMUsdt30V8_TuOVcNc40KbEe17/view?usp=sharing)  you will find the whole low resolution dataset.
It is divided in 49,078 training images and 5,453 testing images.


2-2 Generating High resolution faces:

Similary, we apply  [Single Shot Scale-invariant Face Detector
](https://arxiv.org/pdf/1708.05237.pdf) on [celebA dataset](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html
) and on [aflw dataset](https://www.tugraz.at/institute/icg/research/team-bischof/lrs/downloads/aflw/)
and select the results with confidence greater than 80% and with min(width,heigth) > 63.


An example of the dataset resized to (64,64) size.

![alt text](images/epoch001_real_HR.png "Example of high resolution dataset").


In [this link](https://drive.google.com/file/d/1IOH_0hGUvK0FggbdXVAAFC5TsSDHcpQG/view?usp=sharing)  you will find 
the whole high resolution dataset.
It contains 220,818  images.


2.BaseLine

2.1 FSRNet

We Use [FSRNet with Gan loss](https://drive.google.com/file/d/10i2NZfUyf2Yold4ABusz3Que-XN_gEEu/view) on wider dataset and
with the network trained with [celebA dataset](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) 
as our baseline.
 
3.Method:

3.1 Overall Architecture:

We use two generator and one discriminators: The first generator called high to low generator is used 
to create low resolution data from high resolution input; it's combined with the  discriminator called
Low Resolution Discriminator.

The second generator called low to high generator takes the output of the high to low generator as input and
produce a high resolution image.

The overall architecture is presented in the figure below.

![alt text](images/architectures/overall_architecture.png 'overall') 

3.2 High to Low Generator:

The H2L Generator follow an encoder decoder like architecture with two skip connections.
We concatenate the input image with a 1 channel image generated by passing a normal ditribution to 
a fully connected layer.

The architecture is presented in the figure below.

![alt text](images/architectures/HightoLow.png 'H2L') 

3.3 Low to High Generator:

Similar to the H2L Generator; the L2H generator follows an encoder decoder architecture with more skip connections
and an overall skip connection between the input and output.

The architecture is presented in the figure below.

![alt text](images/architectures/LowtoHigh.png 'L2H') 

3.4 LR discriminator

The architecture of the low resolution discriminator is presented in the figure below.

![alt text](images/architectures/Discriminator.png 'H2L') 

4.Results

Our method compared with [FSRNet with Gan loss ](https://drive.google.com/file/d/10i2NZfUyf2Yold4ABusz3Que-XN_gEEu/view)  that
is trained on [celebA dataset](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) 

Input                     | FSRNET                   | Ours                    |Input| FSRNET|Ours|Input|FSRNET|Ours
:-------------------------:|:------------------------:|:------------------------:|:----------------------:|:--------:|:---------------:|:------------:|:----------------:|:-------------------- 
![alt text](images/results/input/30.jpg 'input') |  ![alt text](images/results/baseline/30.jpg 'baseline') | ![alt text](images/results/first_method/30_out.png 'ours')  |  ![alt text](images/results/input/50.jpg 'input') |  ![alt text](images/results/baseline/50.jpg 'baseline') | ![alt text](images/results/first_method/50_out.png 'ours') | ![alt text](images/results/input/1790.jpg 'input') |  ![alt text](images/results/baseline/1790.jpg 'baseline') | ![alt text](images/results/first_method/1790_out.png 'ours')
![alt text](images/results/input/80.jpg 'input') |  ![alt text](images/results/baseline/80.jpg 'baseline') | ![alt text](images/results/first_method/80_out.png 'ours')  |  ![alt text](images/results/input/90.jpg 'input') |  ![alt text](images/results/baseline/90.jpg 'baseline') | ![alt text](images/results/first_method/90_out.png 'ours')  | ![alt text](images/results/input/1810.jpg 'input') |  ![alt text](images/results/baseline/1810.jpg 'baseline') | ![alt text](images/results/first_method/1810_out.png 'ours')
![alt text](images/results/input/190.jpg 'input') |  ![alt text](images/results/baseline/190.jpg 'baseline') | ![alt text](images/results/first_method/190_out.png 'ours')  |  ![alt text](images/results/input/200.jpg 'input') |  ![alt text](images/results/baseline/200.jpg 'baseline') | ![alt text](images/results/first_method/200_out.png 'ours') | ![alt text](images/results/input/1840.jpg 'input') |  ![alt text](images/results/baseline/1840.jpg 'baseline') | ![alt text](images/results/first_method/1840_out.png 'ours')
![alt text](images/results/input/210.jpg 'input') |  ![alt text](images/results/baseline/210.jpg 'baseline') | ![alt text](images/results/first_method/210_out.png 'ours')  |  ![alt text](images/results/input/220.jpg 'input') |  ![alt text](images/results/baseline/220.jpg 'baseline') | ![alt text](images/results/first_method/220_out.png 'ours') | ![alt text](images/results/input/1920.jpg 'input') |  ![alt text](images/results/baseline/1920.jpg 'baseline') | ![alt text](images/results/first_method/1920_out.png 'ours')
![alt text](images/results/input/230.jpg 'input') |  ![alt text](images/results/baseline/230.jpg 'baseline') | ![alt text](images/results/first_method/230_out.png 'ours')  |  ![alt text](images/results/input/240.jpg 'input') |  ![alt text](images/results/baseline/240.jpg 'baseline') | ![alt text](images/results/first_method/240_out.png 'ours')  | ![alt text](images/results/input/1940.jpg 'input') |  ![alt text](images/results/baseline/1940.jpg 'baseline') | ![alt text](images/results/first_method/1940_out.png 'ours') 
![alt text](images/results/input/300.jpg 'input') |  ![alt text](images/results/baseline/300.jpg 'baseline') | ![alt text](images/results/first_method/300_out.png 'ours')  |  ![alt text](images/results/input/360.jpg 'input') |  ![alt text](images/results/baseline/360.jpg 'baseline') | ![alt text](images/results/first_method/360_out.png 'ours')  | ![alt text](images/results/input/1970.jpg 'input') |  ![alt text](images/results/baseline/1970.jpg 'baseline') | ![alt text](images/results/first_method/1970_out.png 'ours')
![alt text](images/results/input/480.jpg 'input') |  ![alt text](images/results/baseline/480.jpg 'baseline') | ![alt text](images/results/first_method/480_out.png 'ours')  |  ![alt text](images/results/input/1100.jpg 'input') |  ![alt text](images/results/baseline/1100.jpg 'baseline') | ![alt text](images/results/first_method/1100_out.png 'ours') | ![alt text](images/results/input/2010.jpg 'input') |  ![alt text](images/results/baseline/2010.jpg 'baseline') | ![alt text](images/results/first_method/2010_out.png 'ours')
![alt text](images/results/input/1380.jpg 'input') |  ![alt text](images/results/baseline/1380.jpg 'baseline') | ![alt text](images/results/first_method/1380_out.png 'ours')  |  ![alt text](images/results/input/1390.jpg 'input') |  ![alt text](images/results/baseline/1390.jpg 'baseline') | ![alt text](images/results/first_method/1390_out.png 'ours') | ![alt text](images/results/input/2040.jpg 'input') |  ![alt text](images/results/baseline/2040.jpg 'baseline') | ![alt text](images/results/first_method/2040_out.png 'ours')
![alt text](images/results/input/1400.jpg 'input') |  ![alt text](images/results/baseline/1400.jpg 'baseline') | ![alt text](images/results/first_method/1400_out.png 'ours')  |  ![alt text](images/results/input/1410.jpg 'input') |  ![alt text](images/results/baseline/1410.jpg 'baseline') | ![alt text](images/results/first_method/1410_out.png 'ours') | ![alt text](images/results/input/2170.jpg 'input') |  ![alt text](images/results/baseline/2170.jpg 'baseline') | ![alt text](images/results/first_method/2170_out.png 'ours')
![alt text](images/results/input/1530.jpg 'input') |  ![alt text](images/results/baseline/1530.jpg 'baseline') | ![alt text](images/results/first_method/1530_out.png 'ours')  |  ![alt text](images/results/input/1570.jpg 'input') |  ![alt text](images/results/baseline/1570.jpg 'baseline') | ![alt text](images/results/first_method/1570_out.png 'ours') | ![alt text](images/results/input/2180.jpg 'input') |  ![alt text](images/results/baseline/2180.jpg 'baseline') | ![alt text](images/results/first_method/2180_out.png 'ours')
 
 5.Results with a discriminator for High resolution image generation
 
 Input                     | FSRNET                   | Ours                    |Input| FSRNET|Ours|Input|FSRNET|Ours
:-------------------------:|:------------------------:|:------------------------:|:----------------------:|:--------:|:---------------:|:------------:|:----------------:|:-------------------- 
![alt text](images/results/input/30.jpg 'input') |  ![alt text](images/results/baseline/30.jpg 'baseline') | ![alt text](images/results/first_method1/30_out.png 'ours')  |  ![alt text](images/results/input/50.jpg 'input') |  ![alt text](images/results/baseline/50.jpg 'baseline') | ![alt text](images/results/first_method1/50_out.png 'ours') | ![alt text](images/results/input/1790.jpg 'input') |  ![alt text](images/results/baseline/1790.jpg 'baseline') | ![alt text](images/results/first_method1/1790_out.png 'ours')
![alt text](images/results/input/80.jpg 'input') |  ![alt text](images/results/baseline/80.jpg 'baseline') | ![alt text](images/results/first_method1/80_out.png 'ours')  |  ![alt text](images/results/input/90.jpg 'input') |  ![alt text](images/results/baseline/90.jpg 'baseline') | ![alt text](images/results/first_method1/90_out.png 'ours')  | ![alt text](images/results/input/1810.jpg 'input') |  ![alt text](images/results/baseline/1810.jpg 'baseline') | ![alt text](images/results/first_method1/1810_out.png 'ours')
![alt text](images/results/input/190.jpg 'input') |  ![alt text](images/results/baseline/190.jpg 'baseline') | ![alt text](images/results/first_method1/190_out.png 'ours')  |  ![alt text](images/results/input/200.jpg 'input') |  ![alt text](images/results/baseline/200.jpg 'baseline') | ![alt text](images/results/first_method1/200_out.png 'ours') | ![alt text](images/results/input/1840.jpg 'input') |  ![alt text](images/results/baseline/1840.jpg 'baseline') | ![alt text](images/results/first_method1/1840_out.png 'ours')
![alt text](images/results/input/210.jpg 'input') |  ![alt text](images/results/baseline/210.jpg 'baseline') | ![alt text](images/results/first_method1/210_out.png 'ours')  |  ![alt text](images/results/input/220.jpg 'input') |  ![alt text](images/results/baseline/220.jpg 'baseline') | ![alt text](images/results/first_method1/220_out.png 'ours') | ![alt text](images/results/input/1920.jpg 'input') |  ![alt text](images/results/baseline/1920.jpg 'baseline') | ![alt text](images/results/first_method1/1920_out.png 'ours')
![alt text](images/results/input/230.jpg 'input') |  ![alt text](images/results/baseline/230.jpg 'baseline') | ![alt text](images/results/first_method1/230_out.png 'ours')  |  ![alt text](images/results/input/240.jpg 'input') |  ![alt text](images/results/baseline/240.jpg 'baseline') | ![alt text](images/results/first_method1/240_out.png 'ours')  | ![alt text](images/results/input/1940.jpg 'input') |  ![alt text](images/results/baseline/1940.jpg 'baseline') | ![alt text](images/results/first_method1/1940_out.png 'ours') 
![alt text](images/results/input/300.jpg 'input') |  ![alt text](images/results/baseline/300.jpg 'baseline') | ![alt text](images/results/first_method1/300_out.png 'ours')  |  ![alt text](images/results/input/360.jpg 'input') |  ![alt text](images/results/baseline/360.jpg 'baseline') | ![alt text](images/results/first_method1/360_out.png 'ours')  | ![alt text](images/results/input/1970.jpg 'input') |  ![alt text](images/results/baseline/1970.jpg 'baseline') | ![alt text](images/results/first_method1/1970_out.png 'ours')
![alt text](images/results/input/480.jpg 'input') |  ![alt text](images/results/baseline/480.jpg 'baseline') | ![alt text](images/results/first_method1/480_out.png 'ours')  |  ![alt text](images/results/input/1100.jpg 'input') |  ![alt text](images/results/baseline/1100.jpg 'baseline') | ![alt text](images/results/first_method1/1100_out.png 'ours') | ![alt text](images/results/input/2010.jpg 'input') |  ![alt text](images/results/baseline/2010.jpg 'baseline') | ![alt text](images/results/first_method1/2010_out.png 'ours')
![alt text](images/results/input/1380.jpg 'input') |  ![alt text](images/results/baseline/1380.jpg 'baseline') | ![alt text](images/results/first_method1/1380_out.png 'ours')  |  ![alt text](images/results/input/1390.jpg 'input') |  ![alt text](images/results/baseline/1390.jpg 'baseline') | ![alt text](images/results/first_method1/1390_out.png 'ours') | ![alt text](images/results/input/2040.jpg 'input') |  ![alt text](images/results/baseline/2040.jpg 'baseline') | ![alt text](images/results/first_method1/2040_out.png 'ours')
![alt text](images/results/input/1400.jpg 'input') |  ![alt text](images/results/baseline/1400.jpg 'baseline') | ![alt text](images/results/first_method1/1400_out.png 'ours')  |  ![alt text](images/results/input/1410.jpg 'input') |  ![alt text](images/results/baseline/1410.jpg 'baseline') | ![alt text](images/results/first_method1/1410_out.png 'ours') | ![alt text](images/results/input/2170.jpg 'input') |  ![alt text](images/results/baseline/2170.jpg 'baseline') | ![alt text](images/results/first_method1/2170_out.png 'ours')
![alt text](images/results/input/1530.jpg 'input') |  ![alt text](images/results/baseline/1530.jpg 'baseline') | ![alt text](images/results/first_method1/1530_out.png 'ours')  |  ![alt text](images/results/input/1570.jpg 'input') |  ![alt text](images/results/baseline/1570.jpg 'baseline') | ![alt text](images/results/first_method1/1570_out.png 'ours') | ![alt text](images/results/input/2180.jpg 'input') |  ![alt text](images/results/baseline/2180.jpg 'baseline') | ![alt text](images/results/first_method1/2180_out.png 'ours')
 
 
 6.Citer Data Results
 
 You will find the results for 71 subjects and named appropriatly in 
 [the following directory](images/citer/images/).
 
 Input                     | Output                   | Input                    |Output
:-------------------------:|:------------------------:|:------------------------:|:----------------------:
![alt text](images/citer/first_method/0_real_LR.png 'input') |  ![alt text](images/citer/first_method/0_out.png 'output') | ![alt text](images/citer/first_method/5_real_LR.png 'input')  |  ![alt text](images/citer/first_method/5_out.png 'output')
![alt text](images/citer/first_method/11_real_LR.png 'input') |  ![alt text](images/citer/first_method/11_out.png 'output')  | ![alt text](images/citer/first_method/25_real_LR.png 'input')  |  ![alt text](images/citer/first_method/25_out.png 'output') 
![alt text](images/citer/first_method/32_real_LR.png 'input')  |  ![alt text](images/citer/first_method/32_out.png 'output') |![alt text](images/citer/first_method/39_real_LR.png 'input')  |  ![alt text](images/citer/first_method/39_out.png 'output') 
![alt text](images/citer/first_method/64_real_LR.png 'input')  |  ![alt text](images/citer/first_method/64_out.png 'output') |![alt text](images/citer/first_method/51_real_LR.png 'input')  |  ![alt text](images/citer/first_method/51_out.png 'output')

7.Grayscale images results

Images found at  [the following directory](images/grayscale/).


Input                     | Output                   | Input                    |Output
:-------------------------:|:------------------------:|:------------------------:|:----------------------:
![alt text](images/grayscale/0122_final_input.png 'input') |  ![alt text](images/grayscale/0122_final_out.png 'output') | ![alt text](images/grayscale/0163_final_input.png 'input')  |  ![alt text](images/grayscale/0163_final_out.png 'output')
![alt text](images/grayscale/0164_final_input.png 'input') |  ![alt text](images/grayscale/0164_final_out.png 'output') | ![alt text](images/grayscale/0165_final_input.png 'input')  |  ![alt text](images/grayscale/0165_final_out.png 'output')
![alt text](images/grayscale/0166_final_input.png 'input') |  ![alt text](images/grayscale/0166_final_out.png 'output') | ![alt text](images/grayscale/0167_final_input.png 'input')  |  ![alt text](images/grayscale/0167_final_out.png 'output')
![alt text](images/grayscale/0168_final_input.png 'input') |  ![alt text](images/grayscale/0168_final_out.png 'output') | ![alt text](images/grayscale/0189_final_input.png 'input')  |  ![alt text](images/grayscale/0189_final_out.png 'output')
![alt text](images/grayscale/0193_final_input.png 'input') |  ![alt text](images/grayscale/0193_final_out.png 'output') | ![alt text](images/grayscale/0194_final_input.png 'input')  |  ![alt text](images/grayscale/0194_final_out.png 'output')
![alt text](images/grayscale/0254_final_input.png 'input') |  ![alt text](images/grayscale/0254_final_out.png 'output') | ![alt text](images/grayscale/0255_final_input.png 'input')  |  ![alt text](images/grayscale/0255_final_out.png 'output')
![alt text](images/grayscale/0256_final_input.png 'input') |  ![alt text](images/grayscale/0256_final_out.png 'output') | ![alt text](images/grayscale/0258_final_input.png 'input')  |  ![alt text](images/grayscale/0258_final_out.png 'output')
![alt text](images/grayscale/0259_final_input.png 'input') |  ![alt text](images/grayscale/0259_final_out.png 'output') | ![alt text](images/grayscale/0260_final_input.png 'input')  |  ![alt text](images/grayscale/0260_final_out.png 'output')
![alt text](images/grayscale/0261_final_input.png 'input') |  ![alt text](images/grayscale/0261_final_out.png 'output') | ![alt text](images/grayscale/0263_final_input.png 'input')  |  ![alt text](images/grayscale/0263_final_out.png 'output')
![alt text](images/grayscale/0264_final_input.png 'input') |  ![alt text](images/grayscale/0264_final_out.png 'output') | ![alt text](images/grayscale/0278_final_input.png 'input')  |  ![alt text](images/grayscale/0278_final_out.png 'output')
![alt text](images/grayscale/0279_final_input.png 'input') |  ![alt text](images/grayscale/0279_final_out.png 'output') | ![alt text](images/grayscale/0280_final_input.png 'input')  |  ![alt text](images/grayscale/0280_final_out.png 'output')
![alt text](images/grayscale/0704_final_input.png 'input') |  ![alt text](images/grayscale/0704_final_out.png 'output') | ![alt text](images/grayscale/0707_final_input.png 'input')  |  ![alt text](images/grayscale/0707_final_out.png 'output')
![alt text](images/grayscale/0708_final_input.png 'input') |  ![alt text](images/grayscale/0708_final_out.png 'output') | ![alt text](images/grayscale/0709_final_input.png 'input')  |  ![alt text](images/grayscale/0709_final_out.png 'output')
![alt text](images/grayscale/0710_final_input.png 'input') |  ![alt text](images/grayscale/0710_final_out.png 'output') | ![alt text](images/grayscale/0711_final_input.png 'input')  |  ![alt text](images/grayscale/0711_final_out.png 'output')
![alt text](images/grayscale/0712_final_input.png 'input') |  ![alt text](images/grayscale/0712_final_out.png 'output') | ![alt text](images/grayscale/0713_final_input.png 'input')  |  ![alt text](images/grayscale/0713_final_out.png 'output')










