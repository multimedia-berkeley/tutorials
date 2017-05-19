# Geo-location Tutorial

Download model:
https://s3.amazonaws.com/mmcommons-tutorial/models/RN101-5k500-0012.params
https://s3.amazonaws.com/mmcommons-tutorial/models/RN101-5k500-symbol.json

Geolocation model inspired by ideas presented in:
PlaNet - Photo Geolocation with Convolutional Neural Networks (ECCV 2016),
Tobias Weyand, Ilya Kostrikov, James Philbin 
https://research.google.com/pubs/pub45488.html

## Difference between our model and PlaNet:

|               | Ours  | PlaNet |
|---------------|-------|--------|
|Dataset source        |Multimedia Commons|Images crawled from the web|
|Training set|33.9 million|91 million|
|Validation|1.8 million|34 million|
|S2 Cell Partitioning|t_1=5000, t_2=500 ==> 15,527 cells|t_1=10,000, t_2=50 ==> 26,263 cells|
|Training time| 9 days on 16 NVIDIA K80 GPUs (p2.16xlarge), 12 epochs|2.5 months on 200 CPU cores|
|Framework|MXNet | DistBelief|
|Test set|Placing Task 2016 Test Set (1.5 million Flickr images)|2.3 M geo-tagged Flickr images|

## Result
### Im2GPS test set 
|Method|1km|25km|200km|750km|2500km|
|------|---|----|-----|-----|------|
|PlaNet|8.4|24.5|37.6|53.6|71.3|
|Ours|16.8|39.2|48.9|67.9|82.2|

### Flickr Images 
Note that this result is not directly comparable as the test set images used in PlaNet is not publicly released. 
|Method|1km|25km|200km|750km|2500km|
|------|---|----|-----|-----|------|
|PlaNet|3.6|10.1|16.0|28.4|48.0|
|Ours|6.2|13.5|20.8|35.6|55.2|

### Ours
We used 35 million geo-tagged images from YFCC100M dataset (Flickr images). 
(33.9 M for training, 1.8 M for validation)
S2 cell paritioning (t_1=5000, t_2=500) ==> 15,527 S3 cells. 
Used GoogleNet and ResNet with 101 layers. 
Training time: 10~ days on 16 GPU cores (p2.16xlarge - 16 NVIDIA K80 GPUs) using MXNet. 
Tested on Placing Task 2016 Test Set (1.5 million Flickr images)

PT2016 - 9.8% (1km), 
Im2GPS - 


### PlaNet 
Used 126 million photos all over the web (91M for training, 34M for validation). 
S2 cell partitioning (t_1=10,000, t_2=50) ==> 26,263 S3 cells. 
Used Inception model for training 97,321,048 parameters. 
Training time: 2.5 months on 200 CPU cores using the DistBelief framework
Tested on 2.3M geo-tagged Flickr photos
Result: 
PlaNet (91M) - 8.4% (1km), 24.5% (25km), 37.6% (200km), 53.6% (750km), 71.3% (2500km)
Im2GPS - 2.5% (1km), 21.9% (25km), 32.1% (200km), 35.4% (750km), 51.9% (2500km)
