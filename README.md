# -Automated-Detection-of-Endometrial-Polyps-in-Hysteroscopy

Endometrial polyps are identified by the overgrowth of endometrial glands, stroma, and blood vessels in the uterine lining. 
Typical symptoms of polyps include abnormal uterine bleeding, pelvic pain, and infertility. 
As it poses a serious health threat for women, precise diagnosis of endometrial polyps is vital for delivering the right care at the right time and ensuring proper patient management. 

This project aims to create a computer-aided system to enhance the detection and classification of endometrial polyps using hysteroscopy. 



** Instruction **:

Each code file in this project is independent, meaning there are no dependencies among them. The writer used Jupyter Lab to run the codes. 
To get started, download both the image datasets and the code files. You can then run the code files individually to observe their performance.



1.	** image_preprocessing.ipynb **: 

This code file contains all the necessary code for preprocessing images in the datasets. 
Specialized preprocessing techniques are essential to normalize variability and enhance the quality of input data. 
By tailoring image preprocessing to our specific needs, we can achieve better results when utilizing them in our code files.

The preprocessing techniques applied to our images are detailed below:

•	Extracting Frames from Videos: Our image datasets consist of frames extracted from hysteroscopy videos. We employed code to extract these frames efficiently.

•	Removing Duplicate images: While extracting image frames from a video, duplicate frames may be saved. 
To address this, we implemented code to delete all the duplicate images, keeping only one copy of each.

•	Cropping: Hysteroscopy images often come in a circular format. For such images, we developed a code to crop out unnecessary areas while keeping the circular shape intact. 
This process improves image classification and segmentation tasks, as it prevents the model from being distracted or shifting attention to irrelevant areas of the image. 

•	Image Resizing: Images need to be resized to a specific size so that the model finds them easier to work with. The images in our datasets were resized to 400 by 400 pixels. 

•	Converting Images from .png to .jpg: Working with RGBA images with 4 channels can be challenging. 
We used code to convert the RGBA images into RGB format, which made the process much smoother as working with 3 channels is easier. 

•	Image Renaming: To streamline image handling, we employed code to rename images in sequential numerical order.

•	Splitting Dataset: We used two methods for splitting the dataset into training, testing, and validation sets. 
As we know, image segmentation tasks require original images with their corresponding images in order to identify the area of interest. 
That’s why one specific method of splitting had to be applied. Another method of splitting was implemented for images used in polyp classification tasks. 



2.	** Datasets **:
   
In this project, the "cervix4" dataset is utilized for the "cervix_entry_point_detection.ipynb" code file, while the "lumen4" dataset is employed for the "cervix_lumen_detection.ipynb" code file.
The "up4" dataset is utilized in all the "polyps_classification" code files. We have divided the datasets into training, testing, and validation sets.

•	"cervix4": The “image” folders contain labelled images of the cervix opening/ entry point. The “mask” folders contain the corresponding masks for the images in the “image” folder. 

•	"lumen4": The “image” folders contain labelled images of the cervix canal/ lumen area. The “mask” folders contain the corresponding masks for the images in the “image” folder.

•	"up4": The “polyp” folder contains labelled images of cervical polyps. The “uterus” folder contains labelled images of a clear uterus without any polyps. 



3.	** cervix_entry_point_detection.ipynb **:
   
This code file segments the cervix entry point, marking the exact location and shape of the cervix's opening. 
Proper segmentation of the cervix entry point is necessary in order to provide an accurate point of entry for the hysteroscope. 
Using the results of the cervix entry point segmentation, this code then determines the central point/ centroid of the cervix opening. 
This point serves as the target for the initial entry of the hysteroscope. 



4.	** cervix_lumen_detection.ipynb **:
   
This code file segments the cervix canal/lumen interior.
Segmentation is important to recognize the boundaries of the lumen and to provide a safe navigation further into the reproductive tract.
Based on the lumen segmentation, this code also determines the central point/ centroid of the lumen. This point guides the hysteroscope's deeper navigation towards the uterus.



5.	** Polyps Classification **:
   
We used an FCNN model with different types of pre-processors and feature extractors. 
Our goal is to determine which combination correctly classifies polyps (with higher True Negatives) and reduces the rate of overlooking polyps when they are actually present (with fewer False Positives).

•	"polyps_classification_lbp_sift_fast_clahe.ipynb": This model uses FCNN with FAST denoising + CLAHE methods and LBP + SIFT feature extractions. 

•	"polyps_classification_lbp_sift_thres_bil.ipynb": This model uses FCNN with Thresholding + Bilateral denoising methods and LBP + SIFT feature extractions.

•	"polyps_classification_orb_hist_fast_clahe.ipynb": This model uses FCNN with FAST denoising + CLAHE methods and Color Histogram + ORB feature extractions.

•	"polyps_classification_orb_hist_thres_bi.ipynb": This model uses FCNN with Thresholding + Bilateral denoising methods and Color Histogram + ORB feature extractions.

