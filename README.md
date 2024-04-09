# Tesseract OCR Image Processing Pipeline

This repository contains code for an initial attempt to apply Tesseract OCR on example images. The pipeline consists of several steps to preprocess images before feeding them into the Tesseract OCR engine. Below is an overview of each step:

## 1. Convert PDF Pages to Images

The first step involves converting pages from a PDF document into image files. The `pdf2image` library is used for this purpose.

## 2. Preprocessing Images

### Standard Preprocessing Steps:
- Upscale the images for better resolution using OpenCV.
- Convert the images to grayscale.
- Apply Gaussian blur for denoising.
- Apply Otsu's thresholding for binarization.

### Optional: Crop Region of Interest (ROI)
- This step involves cropping specific regions of interest from the processed images. However, it's not utilized in the subsequent code.

## 3. Text Extraction Using Tesseract

Once the images are preprocessed, the Tesseract OCR engine is used to extract text from the images. The extracted text is then saved to output text files.

## 4. Post-processing: Formatting Extracted Text

After extracting text using Tesseract, there might be noise in the extracted numbers. To clean up the extracted text, the following post-processing steps are applied:
- Non-numeric characters are replaced with spaces using regular expressions.
- If the first number in each line is less than 3 digits long or ends with a period, noise is removed by replacing it with the subsequent number.
- The formatted text is then saved to output files for further analysis.

## Usage
1. Ensure you have the necessary dependencies installed, including `pytesseract`, `pdf2image`, `opencv-python`, and `numpy`.
2. Provide the path to the PDF file containing the images you want to process.
3. Run the provided code cells in a Python environment to execute the image processing pipeline.

(OPTIONAL) The pdf should be replaceable with any pdf. The code is easily modifiable for multiple pdfs through loops.

IMPORTANT: this is very experimental; there are many problems still needing to be addressed due to the complexities within the PDF.