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
|Model|ResNet-101|GoogleNet|Inception|
|Training time| 9 days on 16 NVIDIA K80 GPUs (p2.16xlarge), 12 epochs|2.5 months on 200 CPU cores|
|Framework|MXNet | DistBelief|
|Test set|Placing Task 2016 Test Set (1.5 million Flickr images)|2.3 M geo-tagged Flickr images|

## Result
### Im2GPS test set 
The values indicate the percentages of images within test set that were correctly localized within the given distance. 

|Method|1km|25km|200km|750km|2500km|
|------|---|----|-----|-----|------|
|PlaNet|8.4|24.5|37.6|53.6|71.3|
|Ours|16.8|39.2|48.9|67.9|82.2|

### Flickr Images 
Note that this result is not directly comparable as the test set images used in PlaNet is not publicly released. 
The values indicate the percentages of images within test set that were correctly localized within the given distance. 

|Method|1km|25km|200km|750km|2500km|
|------|---|----|-----|-----|------|
|PlaNet|3.6|10.1|16.0|28.4|48.0|
|Ours|6.2|13.5|20.8|35.6|55.2|


