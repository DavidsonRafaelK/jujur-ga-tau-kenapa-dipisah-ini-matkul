<p align="center"><img src="https://raw.githubusercontent.com/DavidsonRafaelK/Computer-Vision/main/image/logo.png" alt="Computer Vision & Image Processing" /></p>

# Computer Vision & Image Processing

Coursework submissions for two subjects: Computer Vision and Image Processing.

## Note on Course Structure

This repository holds two folders because the material is taught as two separate subjects
running in parallel during the same semester. The division itself is standard: Image
Processing covers pixel and signal level operations, while Computer Vision covers the
extraction of geometric and semantic information from those pixels. The distinction
between the two subjects is academically reasonable; however, their concurrent scheduling
has created certain practical inefficiencies.

Week 1 of each subject, side by side:

| Topic | Computer Vision | Image Processing |
|---|---|---|
| Image loading | `cv2.imread` | `cv2.imread` |
| Channel access | RGB slicing | RGB slicing |
| Color space | BGR, RGB, HSV, LAB | BGR, RGB, grayscale luminance |
| Histogram | manual equalization, CDF | histogram, mean, standard deviation |
| Test image | `wony.jpg` | `wony.jpg` |

The two subjects diverge only after that point. Computer Vision continues into PyTorch
tensors and feature detection; Image Processing continues into histogram analysis and
image statistics.

Because neither subject can assume the other has been taken first, each has to build the
same foundation from scratch. Consequently, a portion of the available laboratory time is
allocated to exercises that have already been completed in the parallel subject. This also
separates concepts that depend on each other. Quantization degrades the histogram, and
histogram quality affects Harris corner response, but the two halves of that relationship
sit in different subjects and are never discussed together. While all required submissions
remain duly completed, this arrangement has resulted in avoidable duplication and has
limited the opportunity for a more integrated examination of closely related concepts.

From an academic and operational standpoint, it may therefore be more effective to offer
Image Processing as a prerequisite to Computer Vision. Such sequencing would preserve the
scope and independence of both subjects while reducing unnecessary repetition and allowing
the available instructional time to be used more efficiently.

## Repository Structure

```bash
.
├── ComputerVision/                                 # Computer Vision assignments
│   ├── 412024030_DAVIDSON_TUGAS_MINGGU_01.ipynb
│   └── 412024030_DAVIDSON_TUGAS_MINGGU_02.ipynb
├── ImageProcessing/                                # Image Processing assignments
│   ├── 412024030_DAVIDSON_TUGAS_MINGGU_01.ipynb
│   └── 412024030_DAVIDSON_TUGAS_MINGGU_02.ipynb
├── image/                                          # Input images  
└── hasil/                                          # Output figures
```

## Output Figures

Stored in `hasil/`:

| File | Contents |
|---|---|
| `hasil_praktikum_minggu_1.png` | 2x4 summary. RGB channels on the top row, quantization and sampling on the bottom row |
| `hasil_kuantisasi_8bit_ke_1bit.png` | Eight quantization levels shown side by side |
| `Profil Intensitas.png` | Single-row intensity profile showing the stepping caused by quantization |

## Running the Notebooks

All notebooks are written for Google Colab. No GPU is required.

To run locally:

```bash
pip install opencv-python numpy matplotlib torch torchvision scikit-image scipy
jupyter notebook
```

Some notebooks read `wony.jpg` from the working directory. That file is generated inside the
notebook from `skimage.data.astronaut()`, so run the cells in order and do not skip the
setup section.

## Implementation Note

When displaying quantization results with matplotlib, `vmin=0` and `vmax=255` must be set
explicitly. Without them, matplotlib normalizes each image to its own min-max range, so even
a 1-bit image renders normally and the comparison is no longer valid.
