# Facial Recognition Project

Group 3: AI Facial Recognition Project  
ITEC 612: Spring 2026  

Steve Millett, Ronaldo Encarnacion, Rachel Baker  
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

Processed images (Deliverable 1) are stored in:  
`processed_data/Facial_Recognition_[Train | Test | Val]/`

Aligned and pipeline-processed images (Deliverable 2) are stored in:  
`preprocess_aligned_[Train | Test | Val]/`

Each folder contains subfolders for each subject.

---

## Preprocessing Script Summary

The notebook `ITEC_612_Facial_Recognition_Preprocessing_Group3.ipynb` standardizes all images to ensure consistency across the dataset before model training.  

The notebook `Group_Project_Deliverable_2_Face_Detection,_Extraction,_Alignment,_Preprocessing_&_Feature_ExtractionGroup3WIP.ipynb` implements the full face-processing pipeline, including detection, extraction, alignment, preprocessing, and feature (embedding) generation.

### What the script does:
Deliverable 1: `ITEC_612_Facial_Recognition_Preprocessing_Group3.ipynb` 
- Converts all images to RGB format  
- Uses black letterbox padding (letterboxing) to maintain the original aspect ratio of faces, preventing feature distortion during resizing  
- Resizes images to 224 x 224 pixels
- Performs Min-Max Normalization, scaling pixel intensity values from the standard 0–255 range to a 0–1 float range to improve model convergence.
- Preserves the original folder structure (train/test/validation and subject folders)  
- Saves processed images into a new `processed_data/` directory  
- Creates a zipped version of the processed dataset for download
  
Deliverable 2:  `Group_Project_Deliverable_2_Face_Detection,_Extraction,_Alignment,_Preprocessing_&_Feature_ExtractionGroup3WIP.ipynb`
- Output serves as the standardized input dataset for the Deliverable 2 face-processing pipeline  
- Maintains consistent image formatting to support reliable face detection, alignment, and embedding generation  
- Ensures reproducibility by applying the same preprocessing steps across all train, validation, and test images  

### Tools Used:
- Python  
- OpenCV (cv2)  
- dlib (face detection + landmark model)  
- face_recognition (embedding generation)  
- NumPy  
- matplotlib  
- tqdm  
- Pillow  
- requests / zipfile (dataset handling in Colab)  
- Google Colab  

---

## How to Run

Open both notebooks in Google Colab and run them in order.

### Step 1: Install Dependencies

Run this in Colab:

`!pip install Pillow tqdm opencv-python dlib matplotlib face_recognition requests`

### Step 2: Clone the Repository

Run this in Colab:

`!git clone https://github.com/RachelBaker26/Grp3_ITEC612/`

### Step 3: Navigate into the Repository

Run this in Colab:

`import os
os.chdir("Grp3_ITEC612")`

### Step 4: Deliverable 1 – Preprocessing

Run the notebook:

`ITEC_612_Facial_Recognition_Preprocessing_Group3.ipynb`

This step:
- Standardizes all images
- Converts images to RGB
- Resizes images to 224 x 224 pixels
- Normalizes pixel values
- Saves processed images to `processed_data/`
- Creates `processed_data.zip`

### Step 5: Deliverable 2 – Face Processing Pipeline

Run the notebook:

`Group_Project_Deliverable_2_Face_Detection,_Extraction,_Alignment,_Preprocessing_&_Feature_ExtractionGroup3WIP.ipynb`

This step:
- Uses `processed_data/` as input
- Performs face detection
- Extracts faces in memory
- Aligns faces using eye landmarks
- Applies final preprocessing
- Saves aligned images to `preprocess_aligned/`
- Generates `face_embeddings.npz`
- Creates downloadable output files

### Expected Outputs

- `processed_data/`
- `processed_data.zip`
- `preprocess_aligned/`
- `preprocess_aligned.zip`
- `face_embeddings.npz`

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
  
### 04/05/26: Preprocessing Optimization
1. R Baker refactored the preprocessing script to include black padding (aspect ratio preservation).
   - Implemented 0–1 pixel normalization logic to meet assignment requirements.
   - Fixed syntax errors and standardized GitHub workflow (branching/merging) for group collaboration.
   - Verified normalized output values via NumPy array inspection.
2. R Baker executed the final preprocessing pipeline and updated the repository with the final processed images
  
### 04/05/26: Preprocessing Optimization
1. R Baker refactored the preprocessing script to include black padding (aspect ratio preservation).

### 04/13/26: Deliverable 2 Initial Pipeline Development  
1. S Millett created first pass of Deliverable 2 notebook  
   - Implemented initial face processing pipeline structure  
   - Achieved ~75% functional completion (detection, preprocessing framework)  
   - Identified issues with runtime errors and undetected faces  
   - Added temporary error handling to allow execution on dataset  

### 04/15/26: Notebook Update & Dataset Cleanup  
1. S Millett upgraded preprocessing notebook to v3  
   - Removed outdated notebook version (v1)  
2. R Encarnacion cleaned dataset images  
   - Removed invalid or duplicate images from training and processed datasets  
   - Focused on improving data quality for Andy Samberg subject  

### 04/16/26: Dataset Refinement & Image Replacement  
1. R Encarnacion updated dataset across train/test/validation splits  
   - Removed problematic images (e.g., low quality, detection failures)  
   - Uploaded replacement images to improve dataset consistency  
2. Continued cleanup across multiple subjects (Andy Samberg, Brad Pitt)  
   - Ensured alignment with required dataset structure  

### 04/17/26: Processed Data Reset  
1. S Millett removed existing processed_data directory  
   - Cleared outdated preprocessing outputs  
2. Replaced processed data with updated outputs  
   - Prepared for revised preprocessing pipeline execution  

### 04/21/26: Preprocessing Iteration & Final Image Updates  
1. S Millett iterated on preprocessing pipeline (multiple commits)  
   - Incremental updates labeled preproc pt1, pt2, pt3  
   - Added comments and debugging improvements  
   - Created working replacement notebook (WIP)  
   - Removed outdated processed test directory  

2. R Baker curated and replaced dataset images  
   - Uploaded new image sets for Deliverable 2  
   - Replaced images causing detection/alignment issues
  
### 4/25/26: Dataset Refinement
1. R Encarnacion replaced images
   - 'no face detected' errors
   - Duplicate images
   - Update raw data folder
2. S Millett reran the preprocessing and facial detection pipeline scripts
   - Committed updated files to Git
3. R Baker updated the readme file
   - Updated log
   - Removed T Lam from collaborators & readme

---
## Notes / Limitations
- This is a closed-set system and will not generalize to unseen individuals  
- Some subjects may have similar features, which could impact model accuracy  
- Image formats vary (.jpg, .png), but are standardized during preprocessing  
- While resizing reduces resolution, the use of LANCZOS filtering and aspect-ratio padding minimizes the loss of critical spatial features compared to standard bilinear stretching  
- Some images do not contain detectable faces and are excluded during the Deliverable 2 pipeline  
- Face alignment and embedding generation depend on landmark detection and may fail on low-quality or obstructed images  

---

## Current Status
- Dataset collected, cleaned, and organized into train/validation/test splits  
- Preprocessing pipeline (Deliverable 1) complete  
- Face-processing pipeline (Deliverable 2) implemented:
  - Detection → Extraction → Alignment → Preprocessing → Embeddings  
- Outputs generated:
  - `processed_data/`
  - `preprocess_aligned/`
  - `face_embeddings.npz`  
- Pipeline validated with visualization and error handling  
- Ready for model training and evaluation
