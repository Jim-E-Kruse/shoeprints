## 6-29-17

This is the GrayCrop function that takes an image, converts it to gray scale,
crops it, and makes it negative. Removing the "#" will also allow this function
to display the image after the changes.
```
GrayCrop <- function(x){
  img <- readImage(x) 
  img <- channel(img, mode = "gray")
  img_crop =img[160:1800, 200:4400]
  img_neg = max(img_crop) - img_crop
  #display(img_neg, method = "raster" )    
}
```
Library these for everything to work correctly.
```
library(purrr)
library(EBImage)
library(dplyr)
```
This is the Hu function that computes the Hu moments from the altered image
and outputs them in a data frame.
```
filenames <- list.files(pattern = "tiff")

Hu<- function(x) {
  out <- compute_moments(GrayCrop(filenames[x]))
  data_frame(argument = filenames[x],
             Hu1 = out[1],Hu2 = out[2],Hu3 = out[3],Hu4 = out[4],
             Hu5 = out[5],Hu6 = out[6],Hu7 = out[7],Hu8 = out[8])
}

```
Running this line will load all 48 of the altered prints into a data set of Hu moments.
```
d <- map_df(1:48, Hu)
```
This will make the data more organized by specifying which shoe, which side, and which
print the moments are for.
```
library(tidyr)

shoeprints <- 
  d %>% 
  mutate(argument = gsub(".tiff", "", argument)) %>%
  separate(argument, c("id", "side", "rep"), sep = "_")
```
This should show the data as it is organized.
```
shoeprints
```
