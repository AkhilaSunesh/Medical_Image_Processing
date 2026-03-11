# Medical_Image_Processing
# Minimal Spanning Trees for Medical Image Segmentation

Graph-based segmentation and denoising of medical images using **Minimal Spanning Trees (MST)** and **Kruskal's Algorithm**.

This project demonstrates how **graph theory** can be applied to **medical image processing** to segment anatomical structures and reduce noise while preserving important boundaries.

---

# Project Overview

Medical images such as **MRI, CT scans, and X-rays** often contain noise and complex structures.  
Image segmentation helps divide these images into meaningful regions corresponding to tissues or anatomical structures.

In this project:

- Each **pixel** is treated as a **node in a graph**
- **Edges** connect neighboring pixels
- **Edge weights** represent intensity differences
- **Kruskal's algorithm** is used to construct a **Minimal Spanning Tree**
- Similar pixels are **merged into segments**
- **Denoising** is performed using **segment-based averaging**

This method is based on the **Efficient Graph-Based Image Segmentation** technique.

---

# Algorithm Workflow

1. Load the medical image.
2. Convert to grayscale (if needed).
3. Construct a graph representation of the image:
   - Pixels → vertices  
   - Neighbor connections → edges
4. Compute edge weights based on pixel intensity differences.
5. Sort edges in ascending order.
6. Apply **Kruskal's algorithm** with **Union-Find**.
7. Merge components based on an adaptive threshold.
8. Generate segmentation map.
9. Apply region-based denoising.

---

# Algorithm Pseudocode

```
Input: Image I
Output: Segmented image S and Denoised image D

1. Convert image to grayscale
2. Represent image as graph G(V,E)
3. For each pixel pair:
       Compute weight = |I(p) - I(q)|
4. Sort edges by weight
5. Initialize Union-Find structure
6. For each edge (u,v):
       If merge condition satisfied:
           Union(u,v)
7. Assign segment labels
8. For each segment:
       Replace pixel values with mean intensity
9. Return segmented and denoised images
```

---

# Project Structure

```
MST-Medical-Image-Segmentation
│
├── images
│   ├── brain_mri.png
│   ├── chest_xray.png
│   └── ct_scan.png
│
├── results
│   ├── seg_brain.jpeg
│   ├── denoise_brain.jpeg
│   ├── seg_ct.jpeg
│   └── denoise_ct.jpeg
│
├── Assignment1.ipynb
├── Image_segmentation_Akhila.pdf
└── README.md
```

---

# Results

The MST-based algorithm was tested on multiple medical images. (view pdf)


# Performance Metrics

| Metric | Description |
|------|-------------|
| Segments | Number of regions detected |
| MSE | Mean Squared Error |
| PSNR | Peak Signal-to-Noise Ratio |
| Execution Time | Algorithm runtime |

Typical output:

```
Number of segments: 120
MSE: 45.3
PSNR: 31.6 dB
Execution time: ~0.8 seconds
```

---

# Segmentation Histogram

The project also generates a **segment size distribution histogram**, showing the number of pixels belonging to each segment.

This helps analyze how the algorithm partitions the image.

---

# Installation

Install the required libraries:

```
pip install scikit-image numpy matplotlib
```

---

# Running the Project

## Option 1 — Google Colab

1. Upload the notebook or script.
2. Upload images when prompted.
3. Run all cells.


# Applications

This technique can be applied to:

- Tumor detection
- Organ segmentation
- Medical diagnosis support
- Noise reduction in scans
- Biomedical image analysis

---

# References

- https://www.researchgate.net/figure/CT-scan-image-of-brain-tumor_fig1_277132123  
- https://radiopaedia.org/articles/chest-pa-view-1  
- https://www.researchgate.net/figure/Axial-T1W-MRI-of-the-brain-Though-the-entire-image-occupies-hard-disk-space-for-storage_fig3_225059460  

---

# Author

**Akhila Sunesh**  
Computational Mathematics for Engineers  
Saintgits College of Engineering
