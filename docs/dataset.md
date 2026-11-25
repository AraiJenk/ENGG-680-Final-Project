# Dataset record

**Dataset**: Human Against Machine with 10,000 Training Images (HAM10000)

**Original Publication**: [Tschandl et al., Scientific Data (2018)](https://www.nature.com/articles/sdata2018161).

Source: Harvard Dataverse [HAM10000 on ISIC](https://api.isic-archive.com/collections/212/)

Original Data Size: 10, 015 dermatoscopic images

Task: Binary classification of benign and malignant skin lesions. 

# Dataset Description
The HAM 10000 data set contains 10,015 dermatoscopic images representing 7 diagnostic categories. Associated Metadata included image identifiers, lesion identifiers, diagnostic labels, patient age, sex, anatomical location, and diagnostic confirmation methods. 

The model uses RBG dermatoscopic images as model inputs. Patient demographic info and other metadata are not used as predictive features. 

# Binary Class Definitions
The original diagnostic criteria were grouped as follows: 

- Malignant (1) 
images in this class had the labels of original diagnosis: Melanoma (mel) OR Basal cell carcinoma (bcc)
- Benign (0): Images in this class had the labels of original diagnosis: Melanocytic nevus (nv), Benign keratosis-like lesion (bkl), Dermatofibroms (df), Vascular lesion (vasc)
- Excluded: Actinic keratoses/ intraepithelial carcinoma (akiec).

Following exclusions 9,688 images were retained. 

# Data Splitting 
Data were split using stratification by binary classification and grouping by lesion ID to prevent images of the same lesion from appearing in multiple subsets. 

Subset: 
- Training included 6,813 images, about 70% of the dataset.
- Validation used 1,460 images, about 15% of the dataset
- Independent test used 1,415 images, about 15% of the dataset

The independent test set contains 1,087 unique lesions and was reserved for final evaluation after model selection. 

# Image preprocessing
All images were resized to 224 x 224 pixels and normalized using ImageNet channel stats. 

Training augmentation included random horizontal and vertical flips, rotation up to 20 degrees and adjustments to brightness, contrast, saturation and hue. 

# Data Quality and limitations
All 10,015 original metadata records were matched to image files. Eight duplicate JPEG copies with file names ending in (1) were excluded during matching. 

The dataset is class-imbalanced and its diagnostic distribution may not represent the prevalence of skin conditions in clinical practice. 

# Data Avaliability
The original HAM10000 images are not redistributed in the repo. The dataset can be obtained from the Harvard Dataverse listed above. 
