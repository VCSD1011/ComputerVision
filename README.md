Setup Instructions
1. Environment Requirements
Python Version: 3.9 or higher

Hardware: A GPU is recommended for YOLO inference and training, though it will run on a CPU.

2. Installation
Clone this repository and install the required libraries using pip:

Bash
pip install numpy matplotlib scipy scikit-image opencv-python ultralytics pandas pyyaml
3. Dataset Preparation
This project uses a subset of the GoPro Motion Deblurring Dataset (Kaggle).

Download the dataset and place it in your local directory.

Update the SOURCE_DIR or --indir variables in the notebook/scripts to point to your local path.

Dependencies & Tech Stack
The project relies on the following core libraries:

ultralytics (YOLOv8n): Used for pre-trained and fine-tuned object detection.

scipy.signal: For Point Spread Function (PSF) estimation and FFT convolutions.

skimage.restoration: Implementation of the Richardson-Lucy algorithm.

opencv-python: Image manipulation and BGR/RGB conversions.

matplotlib: For generating comparison plots and PSNR/SSIM visualizations.

Reproducibility Guide
To reproduce the results shown in the report and presentation, follow these steps in order:

Step 1: Image Restoration
Run the deblurring module. The project uses a motion blur kernel (Length=20, Angle=45°).

Wiener Filter: Used for noise-balanced restoration.

Richardson-Lucy: Iterative restoration (30 iterations) to sharpen edges for detection.

Step 2: YOLO Inference
Compare detection counts across the three image states:

blur_01: Simulated motion blur.

01_rl: Result of 30 iterations of Richardson-Lucy.

01_sharp: The original ground truth.

Step 3: Model Fine-Tuning
The project includes a fine-tuning phase:

Epochs: 30

Data: 179 images from the GoPro subset.
