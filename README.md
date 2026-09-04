# Computer Vision & Image Processing

Coursework submissions for two subjects: Computer Vision and Image Processing.

## Note on Course Structure

This repository holds two folders because the material is taught as two separate subjects.
In practice the foundation covered in both is largely the same.

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

The practical effect is that the same introductory material is covered twice, and lab time
in one subject is spent on work already completed in the other. It also separates concepts
that are directly related. Quantization degrades the histogram, and histogram quality
affects Harris corner response, but the two halves of that relationship belong to different
subjects and are not discussed together.

The full scope fits within a single semester as one subject, in the order: image
representation, histogram and enhancement, feature extraction, geometry and panorama.
The submissions are complete either way.

## Repository Structure

```
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
