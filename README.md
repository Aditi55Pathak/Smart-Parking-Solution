# Smart Parking Solution

A smart parking solution that uses computer vision and machine learning to detect available parking spots in real-time, making parking management more efficient.

## Project Overview

This project leverages video footage and a parking lot's mask image to identify and monitor parking spots. By analyzing the video frames, it determines the availability of parking spaces, providing real-time updates for users.

## Features

- **Parking Spot Detection:** Uses connected components to detect parking spots in a given video feed.
- **Parking Spot Status:** Identifies whether a parking spot is empty or occupied using a machine learning model.
- **Real-time Monitoring:** Displays live updates of parking spot availability.
- **Visual Feedback:** Highlights available (green) and occupied (red) spots on the video feed.

## Technologies Used

- **OpenCV:** For video processing and image manipulation.
- **Scikit-learn:** For machine learning model prediction (empty or occupied parking spots).
- **NumPy:** For numerical operations.
- **Matplotlib:** For visualizing data (if required).
- **Python 3.x:** The primary language for implementing the solution.

## Requirements

Install the required dependencies:

```bash
pip install -r requirements.txt
```

### `requirements.txt`

- `opencv-python==4.6.0.66`
- `scikit-learn==1.1.3`
- `pandas==1.5.1`
- `Pillow==9.3.0`
- `scikit-image==0.17.2`
- `matplotlib==3.4.3`

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/smart-parking-solution.git
   cd smart-parking-solution
   ```

2. **Ensure you have a valid model file (`model/model.p`) in the project directory.**

3. **Prepare your video feed and parking mask:**

   - Place your parking lot mask image (e.g., `mask_1920_1080.png`) in the root folder.
   - Place your parking lot video feed (e.g., `parking_1920_1080_loop.mp4`) in the `data/` folder.

## How to Run

To run the Smart Parking Solution, simply execute the Python script:

```bash
python smart_parking.py
```

This will start the parking spot detection process on the provided video. The system will show a real-time display of available and occupied parking spots.

## Code Explanation

### Main Code (`smart_parking.py`)

1. **`calc_diff(im1, im2)`**: Calculates the difference between two images based on their mean pixel values. This helps detect changes between frames.
   
2. **`get_parking_spots_bboxes()`**: Extracts the bounding boxes of detected parking spots from the mask image using connected components.
   
3. **`empty_or_not()`**: Uses a pre-trained machine learning model to predict if a parking spot is empty or occupied. The model processes resized images of each parking spot.

4. **Real-time Video Processing**: The code processes the video frame by frame. For each frame, it analyzes the parking spots, highlights their status (green for available, red for occupied), and displays the result.

### Helper Functions (`util.py`)

- **`empty_or_not()`**: Predicts whether the spot is empty or not based on a machine learning model. The model is loaded from a pickle file (`model/model.p`).
- **`get_parking_spots_bboxes()`**: Extracts the coordinates and dimensions of the detected parking spots from the connected components of the mask image.

## Model

The model used to classify parking spots as empty or occupied is trained on a dataset of parking spot images. You can update or retrain the model as needed for better accuracy.

- **Model file location:** `model/model.p`
  
> **Note:** The model was trained with images resized to 15x15 pixels for simplicity and efficiency.

## Expected Outputs

Once the program runs, the following outputs will be visible:

- A video feed with highlighted parking spots.
- A count of available spots displayed on the top-left corner of the frame.

---

## Screenshots

![image](https://github.com/user-attachments/assets/aa7c286b-1cb3-4e1f-abec-51316870a350)

