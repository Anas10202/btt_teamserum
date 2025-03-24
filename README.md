# btt_teamserum

## Project Overview

**Describe the Kaggle competition and its connection to the Break Through Tech AI Program**  

**Describe the objective of the challenge**  
The objective of the challenge is to build a machine learning model that can accurately classify 21 different skin conditions from images, while making sure that the model performs equitably across different skin tones. In addition to trying to achieve a strong overall accuracy, the challenge is focused on creating a model that is fair and mindful of performance across different skin tones, especially for groups that have been underrepresented in healthcare AI.

**Explain the real-world significance of the problem and the potential impact of your work**  
In the real world, dermatology AI systems often underperform for individuals with darker skin tones due to biased or incomplete training data. This contributes to misdiagnoses, delayed treatment, and unfair outcomes for marginalized communities. By creating a more equitable AI model, our goal was to reduce these differences and improve healthcare access and quality for everyone. It also shows the importance of inclusivity in AI.



## Data Exploration

## Dataset Description

This project uses a subset of the **Fitzpatrick17k** dataset, which consists of approximately **4,500 images** representing **21 dermatological conditions** across diverse skin tones. The images are sourced from **DermaAmin** and **Atlas Dermatologico**, two widely used dermatology resources.

### Data Overview:
- **Source**: Fitzpatrick17k dataset  
- **Images**: ~4,500 skin condition images  
- **Classes**: 21 skin conditions (e.g., malignant melanoma, acne vulgaris, keloid)  
- **Skin Tone Representation**: Labeled using the **Fitzpatrick Skin Tone (FST) scale**  
- **Evaluation Metric**: Weighted **F1-score**  

### Additional Notes:
- The dataset highlights fairness concerns in dermatology AI models, as many existing models underperform on darker skin tones.
- **Potentially Sensitive Content**: Some images depict serious wounds, burns, and scars.

More details can be found in the [Kaggle competition page](https://www.kaggle.com/competitions/bttai-ajl-2025/overview).


## Data Exploration & Preprocessing

### Data Loading & Extraction
- Mounted Google Drive and extracted the dataset ZIP file to `/content/dataset/BTT_Derm_Files`.
- Loaded `train.csv` containing image metadata and labels.

### Data Analysis
- Merged `train.csv` with extracted image metadata (width, height, aspect ratio).
- Explored the **distribution of Fitzpatrick Skin Types** across conditions using histograms and box plots.
- Generated **bar plots** to visualize class distributions and skin tone representation.

### Image Preprocessing
- Organized images by **Fitzpatrick Scale** and randomly sampled images for visualization.
- Applied **grayscale conversion & heatmaps** using OpenCV for contrast enhancement, particularly for darker skin tones.
- Enhanced images with **LAB color space adjustments** to improve feature visibility for Fitzpatrick Types **5 & 6**.

### Quality Control & Cleaning
- Removed missing values from key columns (`qc` filtering).
- Dropped unnecessary metadata columns (`Width`, `Height`, `Aspect Ratio`).

### Class Balancing
- Computed **class weights** using `compute_class_weight` to address dataset imbalance.

These steps ensure a **well-structured dataset** for model training while addressing potential bias in skin tone representation.
 

![Visualization 1](https://drive.google.com/uc?export=view&id=1pNw4iKzEmQ5SrGuC1_yoZsgLfGW8eCeR)
![Visualization 2](https://drive.google.com/uc?export=view&id=1vAac9-c_u6h1zw3gpJ7FB-KbkLmxmr9W)
![Visualization 3](https://drive.google.com/uc?export=view&id=1uQcDOAcVPByvFfKNgrq9FMsA8BDdm01f)
 
