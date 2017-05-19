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
|Dataset        |Multimedia Commons|Images crawled from the web|

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
