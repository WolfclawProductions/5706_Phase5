# Photogrammetry
## Setup
I set up a lightbox + turntable to capture the images, and then used images of one of my Warhammer models as a test case. I initially used around 20 images, but this ended up being too small of a dataset. I took the dataset up to around 45 images, which seemed to work much better with Regard3D. However, the second dataset was overexposed which created too many data artefacts. 

## Regard3D
I started with Regard3D and found it pretty straightforward to set up, including the installation of Exiftool. Unfortunately, after trying a few different settings Regard3D seemed to struggle with my dataset. As mentioned, this could be user error as It may have been overexposed. Will come back to this with a new dataset and try again. 

Note: Try a more "Medium Lighting and lock the Brightness setting on your phone"

A complaint I have about Meshroom is that it is completely CPU initialized. While I have a powerful CPU, I expect running the process through the GPU may have taken less time. 

## Meshroom
Following the tutorial was dead simple. I tried the same dataset. Luckily, Meshroom is GPU initialized. Unlike Regard3D, my computer is not slowing down or getting hot since the 3090 is taking on the process this time. It takes a while and I may try a smaller Dataset (30 Images or so). First attempt took a long time and did not produce a coherent model. Will create a new and slightly smaller dataset. 

### Meshroom App
After coming bakc to this and finding little success with Regard3D, I tried the meshroom desktop app. https://alicevision.org/#meshroom. This seems to work best. 
![[Model.png]]




