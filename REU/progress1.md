R Markdown
----------

6/23/2017 and 6/27/2017-6/28/2017 Shoe Print Project James Kruse, Andrew
Kimble III, Marion Gray-Lion, and Sam Rew

On the 22nd and 23rd of June, we scanned 8 pairs of shoes to be used
later in the program. They were labeled and pushed into Git Hub for
storage. In addition, we were trained to take shoe prints using dust and
contact paper. They will not be extensively used later in the program,
but this technique is still relevant and necessary in the field.

Over the past two days, the shoe print team has been working to
understand Hu Moments and their use in shoe print analysis. In addition,
we have developed a function in R studio that will allow us to take the
shoe scans that were taken late last week and crop/grayscale the image
for later analysis.

After being given both videos and files to review, we were tasked to put
together a presentation that would both explain Hu Moments and their
relevance in forensic shoe print analysis. This was then presented to
our project leaders. In summary, Hu Moments are a snap shot of an image
in time. If you would like to see the full presentation, please contact
a member of the csafe REU shoe print team.

On the 27th, we learned the program to code grayscale and crop images
using R-Studio after the files are downloaded from GitHub. Each of the
images from the 8 sets were put through this code and saved. On the
28th, we cleaned up the code mentioned above by condensing it into a
function. At this point in time, you can enter in the raw image, run the
function, and end with a cropped/gray scale shoe print. Please see the
finished code below for specifics.

    GrayCrop2 <- function(x){
      img <- readImage(x) 
      img <- channel(img, mode = "grey") 
      img_crop=img[160:1800, 200:4400]
      ###display(img_crop, method = "raster")
      img_crop
    }


    GrayCrop2("Jim2_right_1.tiff")

    compute_moments(GrayCrop2("Jim2_right_1.tiff"))

    filenames <- list.files(pattern="tiff")
    filenames[x]

The past few days have been both fascinating and challenging. We would
like to thank our REU leaders and project leaders for their patience and
assistance through it all.

-csafe REU Shoe Project Team
