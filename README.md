# Facial Recognition Project

Group 3: AI Facial Recognition Project  
ITEC 612: Spring 2026  

Steve Millett, Ronaldo Encarnacion, Rachel Baker, Tiffany Lam  
Dr. Pampapura Madali  

---

## Project Overview
This repository contains the dataset and preprocessing workflow for a closed-set facial recognition project. The goal is to organize facial image data and standardize it for use in future model training and evaluation.

This is a closed-set classification problem, meaning the model will only predict among the known individuals included in the dataset.

---

## Dataset
The dataset consists of facial images organized by subject and split into training, validation, and testing sets.

Each subject includes approximately 15 images, typically split:
- 10 training
- 3 testing
- 2 validation

### Classes (Subjects)
- A_Daddario  
- A_Samberg  
- B_Eilish  
- B_Pitt  
- C_Boseman  
- C_Theron  
- E_Moss  
- H_Jackman  
- J_Travolta  
- T_Cruise  

---

## Dataset Structure

Raw images are stored in:
`dataset/Facial_Recognition_[Train | Test | Val]/`

Processed images are stored in:
`processed_data/Facial_Recognition_[Train | Test | Val]/`

Each folder contains subfolders for each subject.

---

## Preprocessing Script Summary

The preprocessing script standardizes all images to ensure consistency across the dataset before model training.

### What the script does:
- Converts all images to RGB format  
- Crops images to a square format to reduce distortion  
- Resizes images to 224 x 224 pixels  
- Preserves the original folder structure (train/test/validation and subject folders)  
- Saves processed images into a new `processed_data/` directory  
- Creates a zipped version of the processed dataset for download  

### Tools Used:
- Python  
- Pillow  
- tqdm  
- Google Colab  

---

## How to Run

Open the script in Google Colab

Install dependencies:

```python
!pip install Pillow tqdm
```

Clone the repository:

```python
!git clone https://github.com/RachelBaker26/Grp3_ITEC612/
```

Navigate into the repo:

```python
import os
os.chdir("Grp3_ITEC612")
```

Run the preprocessing script

Download the processed dataset (`processed_data.zip`)

---

## Project Timeline / Development Log

### 3/26/26 - 3/28/26: Initial Setup
1. Steve initiated group email about project  
2. Steve created Teams group & invited all group members  
3. Rachel set up GitHub repository and raw image file structure for each group member  
4. Rachel invited all group members and professor to repository  


### 3/30/26: File Directory Change
1. Deleted previous file structure  
2. Created file structure to align with example from Professor  
3. R Baker added images  
   - 3 subjects: Alexandra Daddario, Billie Eilish, Chadwick Boseman  
   - 15 images per subject, split 10/3/2 for train/test/validate  
4. Rachel advised group members of file changes via Teams message


### 4/02/26: File Directory Change
1. S Millett added images  
   - 3 subjects: Tom Cruise, John Travolta, Elisabeth Moss  
   - 15 images per subject, split 10/3/2 for train/test/validate  


### 04/04/26: Processing Code Created
1. S Millett created preprocessing script for image standardization  
   - Converts images to RGB and resizes to 224x224  
   - Preserves train/test/validation folder structure by subject  
   - Saves processed images and exports zipped output file  


### 04/04/26: File Directory Change
1. R Encarnacion added images  
   - 4 subjects: Andy Samberg, Brad Pitt, Charlize Theron, Hugh Jackman  
   - 15 images per subject  


### 04/05/26: Readme Update
1. R Baker updated README  
   - Updated project diary  
   - Added preprocessing script summary  
   - Reorganized structure for clarity  

---

## Notes / Limitations
- This is a closed-set system and will not generalize to unseen individuals  
- Some subjects may have similar features, which could impact model accuracy  
- Cropping and resizing may remove some image detail  
- Image formats vary (.jpg, .png), but are standardized during preprocessing  

---

## Current Status
- Dataset collected and organized  
- Preprocessing pipeline complete  
- Ready for model training and evaluation
