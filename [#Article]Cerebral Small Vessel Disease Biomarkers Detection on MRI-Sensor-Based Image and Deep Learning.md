# [#Article]:Cerebral Small Vessel Disease Biomarkers Detection on MRI-Sensor-Based Image and Deep Learning

## Author

- Yi-Zeng Hsieh
- Yu-Cin Luo
- Chen Pan
- Mu-Chun Su
- Chi-Jen Chen
- Kevin Li-Chun Hsieh

## Abstract

- **MRI:**
  - can identify tiny lesions or cerebral cortical abnormalities
  
- **The purpose of CSVD biomarkers Detection:** 

  - confirm whether there is structural variation that causes epilepsy

- **The thesis of the article:**

  - Using CNN to establish a computer-aided diagnosis system based om small blood vessel lesions in MRI images

  - <u>The structure of the system:</u>

    - **Input:** brain MRI image

    - **Output:**

      - the position coordinates of the small blood vessel blockage
      - the block range
      - the area size
      - if it may cause a stroke
      - a 3D display of the small blood vessels in the brain

## Introduction

- **Features o MRI:**

  - detailly describes each part of the brain

  - can measures not only the anatomical image of the tissue, but also **the various functional images of the organization**

    > Can be used to diagnose various tissue and organ functions and metabolic disorders.

  - higher resolution of soft tissue

- **Cerebral small vessel disease:**

  - cerebral small vessel lesion——The most common and fatal cause of stroke in brain
  - a cerebral infarction caused by a single small blood vessel obstruction
  - the cerebral small vessel in a MRI image is less than 1.5cm
  
- **MRI protocols:**

  - T1 weighting
  - turbo spin echo
  - 3.4mm length of slice
  - 1mm of slice gap

- **Related database:**

  database mainly contains the part of the stroke

  the age layer is mostly middle-aged patients

  50 patients of 1000 data 

  ##### <u>brain stroke caused by cerebral small vessel disease is marked</u>

  the following information of lesion are included	

  - location
  - extent
  - symptoms 

- **The features of the model:**
  
  - CPU-based
  - 7-layers structure at most

## The proposed methods

### Data Preprocessing

> <u>Connected-component labeling:</u>
>
> - Aim: to detect connected regions in binary digital images
> - One pass algorithm:
>   - Output: Different connected component  are labeled with different label
> - Two pass algorithm:
>   - First pass: find all the connected component and labels them, while store all the equivalence of the labels
>   - Second pass: merge all the equivalent labels

- a. Image binarization
- b. Remove head shell
- c. Image binarization(reverse)
- Union of b. and c.
- mask the image and result

### Training Model

**Key Idea:**

- Use the MRI segmentation of the brain based in the patch CNN method

  > Divide the picture into many 7×7 patches

  > Combine all the patches can get the complete and accurate image

**Measurement:**

- Confusion Matrix:

  - TP: Positive and classifier assumes it as Positive
  - TN: Negative and classifier assumes it as negative 
  - FP: Negative and classifier assumes it as positive
  - FN: Positive and classifier assumes it as negative

- Precision:
  $$
  Presion = \frac{TP}{TP + FP}
  $$

- Recall:

$$
Recall = \frac{TP}{FN+TP}
$$

- F1 Score:
  $$
  F1~Score = \frac{2}{\frac{1}{Recall} + \frac{1}{Precision}}
  $$
  



