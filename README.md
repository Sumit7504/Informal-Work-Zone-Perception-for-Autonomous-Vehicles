
# Informal Work-Zone Perception for Autonomous Vehicles

A two-stage computer vision pipeline for detecting informal road work-zone devices under unstructured Indian road conditions.

**Tech Stack:** Python, YOLOv8x, YOLO-World, OpenCV, NumPy, Pandas

## Overview

Combines closed-set and open-vocabulary object detection to evaluate how effectively modern vision models perceive unconventional road work zones, including barricades, cones, concrete blocks, mesh screens, and roadside materials.

## Key Features

- **YOLOv8x:** Detects road users such as pedestrians, cars, trucks, buses, motorcycles, and bicycles.
- **YOLO-World:** Detects work-zone devices using 40+ visual prompts mapped to 9 canonical classes.
- **High-Resolution Inference:** Uses 1280px image resolution and a 0.04 confidence threshold.
- **False-Positive Filtering:** Removes overlapping road-user detections and oversized background boxes.
- **Automated Frame Extraction:** Samples one frame every 5 seconds.
- **Report Generation:** Exports annotated images and research reports in CSV, Excel, and HTML formats.

## Detection Pipeline

```text
Input Video
    |
Frame Extraction (5-second intervals)
    |
    +-------------------+
    |                   |
 YOLOv8x             YOLO-World
    |                   |
 Road Users         Work-Zone Devices
 (Blue Boxes)       (Red Boxes)
    |                   |
    +---------+---------+
              |
    False-Positive Filtering
              |
    Visualizations & Reports
              |
       CSV | Excel | HTML
```

## Experimental Results

Evaluation based on 33 sampled video frames and 153 manually reviewed bounding-box predictions.

| Device Category | Recall |
|---|---:|
| Compact Traffic-Control Devices | **76% (29/38)** |
| Linear Channelizing Barriers | **1% (1/96)** |

**Key Finding:** Conventional traffic-control devices are detected more reliably than thin, transparent, and low-contrast barriers, highlighting a significant perception gap for autonomous vehicles.

## Work-Zone Device Taxonomy

The study examines 11 categories aligned with Indian work-zone traffic management guidelines (IRC:SP:55):

- Traffic cones and warning signs
- Water-filled and concrete barriers
- Steel barricades and barricade tape
- Painted metal drums
- Marshal hand signals
- Mesh screens and flex banners
- Materials and debris on carriageways

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core development |
| YOLOv8x | Closed-set object detection |
| YOLO-World | Open-vocabulary detection |
| OpenCV | Video and image processing |
| NumPy | Numerical computation |
| Pandas | Data processing and reporting |
| OpenPyXL | Excel report generation |

## Project Structure

```text
workzone-perception/
├── workzone_perception.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

## Installation & Usage

The project is designed for Google Colab with GPU acceleration.

**1. Clone the repository**

```bash
git clone https://github.com/<your-username>/workzone-perception.git
cd workzone-perception
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Run the notebook**

1. Open `workzone_perception.ipynb` in Google Colab.
2. Enable GPU runtime.
3. Run Cell 1 to upload the video and perform detection.
4. Run Cell 2 to generate and download the complete report.

## Generated Outputs

- Extracted video frames
- Annotated detection images
- Work-zone device close-up crops
- Red-only detection visualizations
- CSV and Excel research tables
- Self-contained HTML report

## Limitations

- Evaluation is based on a limited sample of 33 frames.
- Open-vocabulary detection depends on prompt selection.
- Ground-truth annotations are currently manual.
- No temporal tracking or traffic-scene interpretation.
- Not validated for production autonomous driving.

## Future Improvements

- Expand the dataset across multiple road environments.
- Fine-tune models for informal work-zone objects.
- Integrate camera and LiDAR sensor fusion.
- Implement temporal tracking and scene understanding.
- Evaluate using precision, recall, and mAP.

## License

MIT License

## Author

**Sumit Sahu**

[GitHub](https://github.com/Sumit7504) | [LinkedIn](https://linkedin.com/in/sumitsahu7504)
