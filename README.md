# btt_teamserum

## Team Members
- **Anans Ahmed**
- **Shannon Joseph**
- **Cassandra Gomez**
- **Ariana Smallwood**
- **Pehal Obhan**

We all worked closely together and organized calls to complete the project.
  
## **🏗️ Project Overview**

**Describe the Kaggle competition and its connection to the Break Through Tech AI Program**  
As part of the Break Through Tech AI Program, this Kaggle competition was in collaboration with the Algorithmic Justice League, an organization that highlights the social implications and harms of artificial intelligence. Our team applied our machine learning skills honed from the program to tackle this challenge on improving fairness in AI-driven dermatology diagnostics.

**Describe the objective of the challenge**  
The objective of the challenge is to build a machine learning model that can accurately classify 21 different skin conditions from images, while making sure that the model performs equitably across different skin tones. In addition to trying to achieve a strong overall accuracy, the challenge is focused on creating a model that is fair and mindful of performance across different skin tones, especially for groups that have been underrepresented in healthcare AI.

**Explain the real-world significance of the problem and the potential impact of your work**  
In the real world, dermatology AI systems often underperform for individuals with darker skin tones due to biased or incomplete training data. This contributes to misdiagnoses, delayed treatment, and unfair outcomes for marginalized communities. By creating a more equitable AI model, our goal was to reduce these differences and improve healthcare access and quality for everyone. It also shows the importance of inclusivity in AI.


## **Project Highlights**
- Built a machine learning model to recognize 21 different skin conditions using images from the Fitzpatrick17k dataset.
- Adjusted image colors to make skin conditions easier to see, especially on darker skin tones.
- Balanced the training data so the model could learn fairly from both common and rare conditions.
- Created charts to better understand how the data was spread across different skin tones and conditions.
- Focused on making sure the model worked well for all skin tones, not just the lighter ones.

## ** 👩🏽‍💻 Setup & Execution **

Follow these steps to run our project and reproduce the results:

## Clone the Repository
If working locally or on a platform like Kaggle Kernels, start by cloning the repo:
```bash
git clone https://github.com/your-username/btt_teamserum.git
cd btt_teamserum

## Install Dependencies
We used Google Colab, which already includes most required libraries. If you're running locally, install the following packages:
pip install numpy pandas matplotlib seaborn opencv-python scikit-learn tensorflow

## Set Up the Environment
To access the dataset in Google Colab:

- First, mount your Google Drive by running this code in a cell:

```python
from google.colab import drive
drive.mount('/content/drive')
```

- After mounting, make sure the dataset folder is located at:

```
/content/drive/MyDrive/BTT_Derm_Files/
```

This folder should contain all images and the `train.csv` metadata file.

## Access the Dataset
We used a subset of the **Fitzpatrick17k** dataset, provided through the competition. It contains:

- `train.csv`: a CSV file with image labels and Fitzpatrick Skin Type values.
- `images/`: a folder with approximately 4,500 images of skin conditions.

Your folder structure should look like this:

```
BTT_Derm_Files/
├── train.csv
└── images/
    ├── img_001.jpg
    ├── img_002.jpg
    └── ...
```

Make sure this folder is unzipped and correctly placed in your Google Drive for Colab to access it.

## Run the notebook
Open the project notebook (e.g., `BTT_TeamSerum_Model.ipynb`) and run each cell in order. 


## **📊 Data Exploration**
Before developing our model, we performed a thorough exploration of the dataset to gain insights into its structure, data quality, and any potential biases. A key part of this process was examining how the 21 skin conditions were distributed across the various Fitzpatrick skin tones. Understanding this representation was crucial to promoting fairness and shaping our preprocessing strategy.


## Dataset Description
This project uses a subset of the **Fitzpatrick17k** dataset, which consists of approximately **4,500 images** representing **21 dermatological conditions** across diverse skin tones. The images are associated with a FitzPatrick skin tone six point scale (FST) value, that refers to how distinct skin tones react to the sun. This value helps assess the model's performance across different skin tones. All the images are sourced from **DermaAmin** and **Atlas Dermatologico**, two widely used dermatology resources. 

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
Before building our model, we conducted an in-depth exploration of the dataset to better understand its structure, quality, and potential sources of bias. Our primary focus was to investigate how well the 21 skin conditions were represented across the different Fitzpatrick skin tones. This step was essential for ensuring fairness and guiding preprocessing decisions.

Key Insights:
- We observed class imbalance among the 21 dermatological conditions, with some classes (e.g., acne vulgaris, atopic dermatitis) having significantly more images than others (e.g., squamous cell carcinoma).
- The Fitzpatrick Skin Type distribution was skewed toward lighter skin tones (Types 1–3), which could introduce performance bias if not addressed.
- Certain conditions were underrepresented in darker skin tones, highlighting a need for augmentation or weighting techniques to avoid model bias.
- Through visual inspection and histogram analysis, we noticed some images varied greatly in brightness and contrast—especially across skin tones—reinforcing the importance of color normalization and contrast enhancement during preprocessing.

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


 ## Model Development
- **Architecture:** CNN-based classification model (e.g., ResNet or EfficientNet) for image classification.
- **Preprocessing:** Color enhancement, normalization, grayscale & heatmap visualizations.
- **Fairness Techniques:** 
  - Class reweighting using `compute_class_weight` to handle imbalanced classes.
  - Image enhancement focused on improving clarity for FST Types V–VI.
- **Optimization:**
  - Loss Function: Categorical Crossentropy
  - Optimizer: Adam
  - Evaluation Metric: Weighted F1-score
 
## 📈 Results & Key Findings
- Model achieved decent overall F1-scores while maintaining more equitable performance across skin tones.
- Visualizations showed reduced disparity in performance across Fitzpatrick scale groups compared to baseline.
- Certain underrepresented classes remained difficult to classify accurately due to limited samples.

## 💥 Impact Narrative
Our project directly addresses bias in healthcare AI, a real-world issue that impacts diagnosis and treatment quality for patients with darker skin. Dermatology tools today often fail to generalize across diverse populations, exacerbating healthcare disparities. Through this project, we worked to create a model that is not only accurate but fair—helping pave the way for more inclusive and ethical AI applications in medicine. T

## Next Steps & Future Improvements
- Use synthetic augmentation or GANs to enhance representation for rare skin tones and conditions.
- Work with dermatologists for real-world validation and feedback.
- Make the model more accessible for use in remote or underserved areas.
- Develop a fairness dashboard to continuously evaluate model performance across subgroups.

