# Geo-location Tutorial

Download model:
https://s3.amazonaws.com/mmcommons-tutorial/models/RN101-5k500-0012.params
https://s3.amazonaws.com/mmcommons-tutorial/models/RN101-5k500-symbol.json

Geolocation model inspired by ideas presented in:
PlaNet - Photo Geolocation with Convolutional Neural Networks (ECCV 2016),
Tobias Weyand, Ilya Kostrikov, James Philbin 
https://research.google.com/pubs/pub45488.html

## Difference between our model and PlaNet:
### Ours
We used 35 million geo-tagged images from YFCC100M dataset (Flickr images). 
(33.9 M for training, 1.8 M for validation)
Used ResNet with 101 layers. 
Training time: 10~ days on 16 GPU cores (p2.16xlarge - 16 NVIDIA K80 GPUs) using MXNet. 
Tested on Placing Task 2016 Test Set (1.5 million Flickr images)

### PlaNet 
Used 126 million photos all over the web (91M for training, 34M for validation). 
S2 cell partitioning (t_1=10,000, t_2=50) ==> 26,263 S3 cells. 
Used Inception model for training 97,321,048 parameters. 
Training time: 2.5 months on 200 CPU cores using the DistBelief framework
Tested on 2.3M geo-tagged Flickr photos

