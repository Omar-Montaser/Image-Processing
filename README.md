# Image Processing Phase 1: Jigsaw Puzzle Edge Detection

## 📌 Project Overview
This project implements **Phase 1** of a Jigsaw Puzzle Solver. The goal of this phase is to automate the pre-processing of shuffled puzzle images. The system automatically detects the puzzle grid size (2x2, 4x4, or 8x8), segments the image into individual pieces, and performs advanced edge detection to prepare for future reconstruction.

## 📂 Project Structure (phase 1)

* **`phase1_pipeline.ipynb`** The main driver notebook. It processes a batch of images, runs the full pipeline (Detection → Splitting → Edge Extraction), and saves the results.
    
* **`image_utils.py`** A helper library containing core functions for:
    * Loading images.
    * `detect_grid_size()`: Energy-based grid detection using Sobel gradients and relative strength thresholds.
    * `compute_spatial_energy()`: Computes gradient energy profiles for boundary detection.
    * `evaluate_partition_score()`: Evaluates the strength of boundaries at expected grid positions.
    * `split_image()`: Slicing images into puzzle patches.

* **`edge_detection_visualizer.ipynb`** A demo notebook to visualize the effects of different filters (CLAHE, Bilateral, Canny) on a single puzzle piece.

* **`grid_detection_visualizer.ipynb`** A debug notebook showing how the system calculates Sobel gradient energy profiles and uses relative strength thresholds to determine if a puzzle is 2x2, 4x4, or 8x8.

## ⚙️ Key Features (phase 1)
1.  **Automatic Grid Detection:** Uses Sobel gradient energy profiles with relative strength thresholds to identify puzzle grid size. The algorithm checks ODD-numbered divisions (1/N, 3/N, 5/N...) to avoid false positives when some pieces are in correct positions.
2.  **Adaptive Pre-processing:** Implements **CLAHE** (Contrast Limited Adaptive Histogram Equalization) to handle low-contrast images.
3.  **Noise-Resistant Edge Detection:** Utilizes **Canny Edge Detection** & **Bilateral Filtering** to ignore internal puzzle textures while preserving piece boundaries.
