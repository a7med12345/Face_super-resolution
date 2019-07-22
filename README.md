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
![alt text](images/epoch011_real_HR.png "Example of high resolution dataset").


In [this link](https://drive.google.com/file/d/1IOH_0hGUvK0FggbdXVAAFC5TsSDHcpQG/view?usp=sharing)  you will find 
the whole high resolution dataset.
It contains 220,818  images.


2.BaseLine

2.1 FSRNet

Using [FSRNet with Gan loss](https://drive.google.com/file/d/10i2NZfUyf2Yold4ABusz3Que-XN_gEEu/view) on wider dataset and
with the network trained with [celebA dataset](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) 
we obtain the following qualitative results.

 Input                     | Output                   | Input                    |Output
:-------------------------:|:------------------------:|:------------------------:|:----------------------:
![alt text](images/FSRNET/INPUT/3.jpg 'input') |  ![alt text](images/FSRNET/OUTPUT/3.jpg 'input') | ![alt text](images/FSRNET/INPUT/24.jpg 'input')  |  ![alt text](images/FSRNET/OUTPUT/24.jpg 'input')
![alt text](images/FSRNET/INPUT/4.jpg 'input') |  ![alt text](images/FSRNET/OUTPUT/4.jpg 'input')  | ![alt text](images/FSRNET/INPUT/30.jpg 'input')  |  ![alt text](images/FSRNET/OUTPUT/30.jpg 'input') 
![alt text](images/FSRNET/INPUT/14.jpg 'input')  |  ![alt text](images/FSRNET/OUTPUT/14.jpg 'input') |![alt text](images/FSRNET/INPUT/63.jpg 'input')  |  ![alt text](images/FSRNET/OUTPUT/63.jpg 'input') 
![alt text](images/FSRNET/INPUT/18.jpg 'input')  |  ![alt text](images/FSRNET/OUTPUT/18.jpg 'input') 

3.Premilinary results

Input                     | Output                   | Input                    |Output
:-------------------------:|:------------------------:|:------------------------:|:----------------------:
![alt text](images/gan1/INPUT/3.jpg 'input') |  ![alt text](images/gan1/OUTPUT/3.png 'input') | ![alt text](images/gan1/INPUT/24.jpg 'input')  |  ![alt text](images/gan1/OUTPUT/24.png 'input')
![alt text](images/gan1/INPUT/4.jpg 'input') |  ![alt text](images/gan1/OUTPUT/4.png 'input')  | ![alt text](images/gan1/INPUT/30.jpg 'input')  |  ![alt text](images/gan1/OUTPUT/30.png 'input') 
![alt text](images/gan1/INPUT/14.jpg 'input')  |  ![alt text](images/gan1/OUTPUT/14.png 'input') |![alt text](images/gan1/INPUT/63.jpg 'input')  |  ![alt text](images/gan1/OUTPUT/63.png 'input') 
![alt text](images/gan1/INPUT/18.jpg 'input')  |  ![alt text](images/gan1/OUTPUT/18.png 'input') 



4.Results

Input                     | FSRNET                   | Ours                    |Input| FSRNET|Ours
:-------------------------:|:------------------------:|:------------------------:|:----------------------:|:--------:|:--------------- 
![alt text](images/results/input/30.jpg 'input') |  ![alt text](images/results/baseline/30.jpg 'baseline') | ![alt text](images/results/first_method/30_out.png 'ours')  |  ![alt text](images/results/input/50.jpg 'input') |  ![alt text](images/results/baseline/50.jpg 'baseline') | ![alt text](images/results/first_method/50_out.png 'ours')
![alt text](images/results/input/80.jpg 'input') |  ![alt text](images/results/baseline/80.jpg 'baseline') | ![alt text](images/results/first_method/80_out.png 'ours')  |  ![alt text](images/results/input/90.jpg 'input') |  ![alt text](images/results/baseline/90.jpg 'baseline') | ![alt text](images/results/first_method/90_out.png 'ours') 
![alt text](images/results/input/190.jpg 'input') |  ![alt text](images/results/baseline/190.jpg 'baseline') | ![alt text](images/results/first_method/190_out.png 'ours')  |  ![alt text](images/results/input/200.jpg 'input') |  ![alt text](images/results/baseline/200.jpg 'baseline') | ![alt text](images/results/first_method/200_out.png 'ours')
![alt text](images/results/input/210.jpg 'input') |  ![alt text](images/results/baseline/210.jpg 'baseline') | ![alt text](images/results/first_method/210_out.png 'ours')  |  ![alt text](images/results/input/220.jpg 'input') |  ![alt text](images/results/baseline/220.jpg 'baseline') | ![alt text](images/results/first_method/220_out.png 'ours')
![alt text](images/results/input/230.jpg 'input') |  ![alt text](images/results/baseline/230.jpg 'baseline') | ![alt text](images/results/first_method/230_out.png 'ours')  |  ![alt text](images/results/input/240.jpg 'input') |  ![alt text](images/results/baseline/240.jpg 'baseline') | ![alt text](images/results/first_method/240_out.png 'ours')   
![alt text](images/results/input/300.jpg 'input') |  ![alt text](images/results/baseline/300.jpg 'baseline') | ![alt text](images/results/first_method/300_out.png 'ours')  |  ![alt text](images/results/input/360.jpg 'input') |  ![alt text](images/results/baseline/360.jpg 'baseline') | ![alt text](images/results/first_method/360_out.png 'ours')  
![alt text](images/results/input/480.jpg 'input') |  ![alt text](images/results/baseline/480.jpg 'baseline') | ![alt text](images/results/first_method/480_out.png 'ours')  |  ![alt text](images/results/input/1100.jpg 'input') |  ![alt text](images/results/baseline/1100.jpg 'baseline') | ![alt text](images/results/first_method/1100_out.png 'ours') 
![alt text](images/results/input/1380.jpg 'input') |  ![alt text](images/results/baseline/1380.jpg 'baseline') | ![alt text](images/results/first_method/1380_out.png 'ours')  |  ![alt text](images/results/input/1390.jpg 'input') |  ![alt text](images/results/baseline/1390.jpg 'baseline') | ![alt text](images/results/first_method/1390_out.png 'ours')
![alt text](images/results/input/1400.jpg 'input') |  ![alt text](images/results/baseline/1400.jpg 'baseline') | ![alt text](images/results/first_method/1400_out.png 'ours')  |  ![alt text](images/results/input/1410.jpg 'input') |  ![alt text](images/results/baseline/1410.jpg 'baseline') | ![alt text](images/results/first_method/1410_out.png 'ours')
![alt text](images/results/input/1530.jpg 'input') |  ![alt text](images/results/baseline/1530.jpg 'baseline') | ![alt text](images/results/first_method/1530_out.png 'ours')  |  ![alt text](images/results/input/1570.jpg 'input') |  ![alt text](images/results/baseline/1570.jpg 'baseline') | ![alt text](images/results/first_method/1570_out.png 'ours')   