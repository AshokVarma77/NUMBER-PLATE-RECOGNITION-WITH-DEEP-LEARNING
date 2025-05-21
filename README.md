# NUMBER-PLATE-RECOGNITION-WITH-DEEP-LEARNING

# 🚗 Automatic Number Plate Recognition (ANPR) with Deep Learning 📸

## 🌟 Project Overview

This project focuses on developing an **Automatic Number Plate Recognition (ANPR) system using Deep Learning techniques**. The primary goal is to accurately identify and extract license plate numbers from images or video frames of vehicles. This system addresses the growing need for efficient vehicle tracking and traffic management due to the increasing number of vehicles. The project aims to simplify and expedite the process of number plate identification, offering a solution that can be applied in various real-world scenarios like law enforcement, traffic control, and security.


---
## 🎯 Project Objectives

* To design and implement an ANPR system capable of recognizing number plates from images captured by CCTV cameras or other sources.
* To reduce the computational time and increase the efficiency of existing number plate recognition models.
* To accurately detect the license plate region within an image.
* To segment and recognize characters from the localized license plate.
* To provide the recognized license plate number in both text and audio formats.
* To leverage deep learning algorithms, specifically using Python with OpenCV and Tesseract OCR, for the recognition process.

---
## 👁️ Problem Statement

With the rapid increase in vehicular traffic, manual tracking and identification of vehicles have become extremely challenging and inefficient. Existing systems often struggle with complexity, real-time processing, and variations in number plate characteristics (like fonts, colors, and numbering systems across different regions) Traffic authorities face difficulties in identifying speeding vehicles, traffic rule violators, or stolen vehicles from moving cars. This project aims to create an automated system that efficiently extracts license plate information from vehicle images, thereby saving time and effort, and aiding in traffic management and law enforcement.
---
## 💡 Proposed System & Advantages

The proposed system is an ANPR solution that takes an image of a vehicle as input and outputs the recognized license plate number in text and audio formats.

**Workflow:**
1.  **Input Image:** The system accepts a vehicle image in various formats (.jpg, .jpeg, .png).
2.  **Grayscale Conversion:** The input image is converted to grayscale to simplify subsequent processing steps like edge detection. 
3.  **Plate Localization (Edge Detection):** The Canny edge detection algorithm (via OpenCV) is used to find the edges of the number plate. The image is then cropped to isolate the number plate region.
4.  **Character Recognition (OCR):** The Pytesseract library (a wrapper for Tesseract OCR engine) is employed to extract the textual characters from the cropped number plate image.
5.  **Output:** The recognized license plate number is provided as text. [cite: 124] Additionally, the system uses the gTTS (Google Text-to-Speech) package to convert the text output into an audio format.

**Advantages:**
* **Automation:** Eliminates manual and time-consuming recording of license plate numbers.
* **Efficiency & Speed:** Captures and processes numbers in real-time, overcoming the limitations of manual tracking, especially with multiple vehicles.
* **Accuracy:** Aims for high accuracy in number plate detection and character recognition.
* **Accessibility:** Provides audio output for users with reading difficulties.

---
## 🛠️ System Architecture & Modules

The system architecture follows a sequential process:

**High-Level Workflow:**
1.  Dataset Collection
2.  Data Normalization
3.  Training
4.  Exporting Trained Data to Model
5.  Deployment

**Core Modules:**

1.  **Frame Acquisition:** Capturing the vehicle image.
2.  **Pre-processing:** Converting the image to grayscale and applying filters (e.g., bilateral filter) to reduce noise and prepare for edge detection.
3.  **Plate Localization:** Using Canny edge detection and contour analysis to find and crop the number plate.
4.  **Character Segmentation:** Isolating individual characters on the detected plate (inherent in OCR process).
5.  **Character Recognition:** Converting the segmented character images into text using Pytesseract OCR.
6.  **Audio Conversion (Optional):** Converting the recognized text to speech using gTTS. 


---
## ⚙️ Technical Stack

**Software Requirements:** 
* **Programming Language:** Python
* **IDE/Notebook:** Jupyter Notebook
* **Core Libraries:**
    * **OpenCV:** For image processing tasks like reading images, grayscale conversion, bilateral filtering, Canny edge detection, and contour finding.
    * **Pytesseract:** Python wrapper for Tesseract-OCR Engine, used for optical character recognition from images.
    * **gTTS (Google Text-to-Speech):** For converting the recognized text into an audio output.
    * **imutils:** For basic image processing utilities like resizing.
    * **NumPy:** For numerical operations (often a dependency for image processing libraries).
* **Algorithm:** Canny Edge Detection for locating the number plate.

**Hardware Requirements (Minimum):**
* **RAM:** 4 GB (for processing)
* **Camera Resolution:** 16 Megapixel (for capturing vehicle images) 
* **Memory Space:** Approximately 30 MB 

---
## 📊 Design Diagrams

The project report includes several design diagrams illustrating the system's structure and behavior:
* **State Diagram:**
* **Use Case Diagram:**
* **Deployment Diagram:**
* **Activity Diagram:** 

---
## 🚀 How to Run (Based on Appendix Code)

1.  **Install Dependencies:**
    ```bash
    pip install imutils gtts pytesseract opencv-python numpy pybind11
    ```
    [cite: 207]
2.  **Install Tesseract OCR Engine:**
    * Pytesseract requires a Tesseract OCR engine installation. Download and install it from the official Tesseract GitHub page or use a package manager (e.g., `sudo apt-get install tesseract-ocr` on Debian/Ubuntu).
    * Ensure the Tesseract installation path is correctly configured in your system's PATH environment variable or specified in the Python script as shown in the appendix: [cite: 207]
        ```python
        pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe' # Adjust path as per your installation
        ```
       
3.  **Prepare Image:**
    * Place the vehicle image (e.g., `sdfg (1).jpeg` as used in the code in the same directory as your Python script, or provide the correct path to the image.
4.  **Run the Python Script:**
    * Execute the Python script provided in Appendix A of the project report. 
    * The script will:
        * Read and resize the image.
        * Convert it to grayscale and apply a bilateral filter.
        * Perform Canny edge detection.
        * Find contours to locate the number plate (approximating a quadrilateral).
        * Crop the number plate region and save it as `1.jpeg` (or `2.jpeg`, etc., if multiple contours are processed).
        * Use Pytesseract to extract text from the cropped image.
        * Print the recognized number.
        * Convert the recognized text to speech and save it as `saved_audio.wav`, then play it.


---
## 📈 Results & Outputs

The project report includes screenshots of the code execution and intermediate image processing steps, demonstrating:
* Installation of libraries (gTTS, Pytesseract).
* Original image, grayscale image, bilateral filtered image, Canny edges, and contoured images.
* The final cropped number plate image.
* The recognized number plate text printed in the console.
* Confidence levels from Pytesseract's `image_to_data` output.
* Successful generation and playing of the audio file for the recognized number.

For example, for an input image containing the number plate "MH 20 EE 7598", the system successfully recognized and printed this number.

---
## 🔮 Future Work & Enhancements

While this project successfully implements an ANPR system, potential future enhancements could include:
* Improving accuracy for number plates with varying fonts, sizes, and under different lighting conditions.
* Training a custom deep learning model for character recognition instead of relying solely on general-purpose OCR like Tesseract for potentially better accuracy on specific plate types.
* Optimizing the algorithm for faster real-time processing from video streams.
* Integrating with a database to store recognized plate numbers along with timestamps and location data for applications like automated toll collection, parking management, or vehicle tracking.
* Developing a user interface (GUI or web application) for easier interaction.

---
## 📚 References

The project report cites several research papers and resources. Key references include studies on ANPR using deep learning, CNN models, fuzzy logic, and color image processing.
For a full list, please refer to page 26 of the "Final Major Report.pdf".

---
