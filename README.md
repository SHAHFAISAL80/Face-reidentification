# Face-reidentification


Face Re-Identification with SCRFD and ArcFace
Downloads GitHub Repo stars GitHub Repository


 demo.mp4 
This repository implements face re-identification using SCRFD for face detection and ArcFace for face recognition. It supports inference from webcam or video sources.

Features (Updated on: 2024.07.29)
 Smaller versions of SCFRD face detection model has been added
 Face Detection: Utilizes Sample and Computation Redistribution for Efficient Face Detection (SCRFD) for efficient and accurate face detection. (Updated on: 2024.07.29)
Added models: SCRFD 500M (2.41 MB), SCRFD 2.5G (3.14 MB)
 Face Recognition: Employs ArcFace: Additive Angular Margin Loss for Deep Face Recognition for robust face recognition. (Updated on: 2024.07.29)
Added models: ArcFace MobileFace (12.99 MB)
 Real-Time Inference: Supports both webcam and video file input for real-time processing.
Project folder structure:

├── assets/
│   ├── demo.mp4
│   └── in_video.mp4
├── faces/
│   ├── face1.jpg
│   ├── face2.jpg
│   └── ...
├── models/
│   ├── __init__.py
│   ├── scrfd.py
│   └── arcface.py
├── weights/
│   ├── det_10g.onnx
│   ├── det_2.5g.onnx
│   ├── det_500m.onnx
│   ├── w600k_r50.onnx
│   └── w600k_mbf.onnx
├── utils/
│   └── helpers.py
├── main.py
├── README.md
└── requirements.txt
Installation
Clone the repository:
git clone https://github.com/yakyo/face-reidentification.git
cd face-reidentification
Install the required dependencies:
pip install -r requirements.txt
Download weight files:

a) Download weights from following links:

Model	Weights	Size	Type
SCRFD 500M	det_500m.onnx	2.41 MB	Face Detection
SCRFD 2.5G	det_2.5g.onnx	3.14 MB	Face Detection
SCRFD 10G	det_10g.onnx	16.1 MB	Face Detection
ArcFace MobileFace	w600k_mbf.onnx	12.99 MB	Face Recognition
ArcFace ResNet-50	w600k_r50.onnx	166 MB	Face Recognition
b) Run below command to download weights to weights directory (linux):

sh download.sh
Put target faces into faces folder

faces/
    ├── name1.jpg
    ├── name2.jpg
Those file names will be displayed while real-time inference.

Usage
python main.py --source assets/in_video.mp4
main.py arguments:

usage: main.py [-h] [--det-weight DET_WEIGHT] [--rec-weight REC_WEIGHT] [--similarity-thresh SIMILARITY_THRESH] [--confidence-thresh CONFIDENCE_THRESH]
               [--faces-dir FACES_DIR] [--source SOURCE] [--max-num MAX_NUM] [--log-level LOG_LEVEL]

Face Detection-and-Recognition

options:
  -h, --help            show this help message and exit
  --det-weight DET_WEIGHT
                        Path to detection model
  --rec-weight REC_WEIGHT
                        Path to recognition model
  --similarity-thresh SIMILARITY_THRESH
                        Similarity threshold between faces
  --confidence-thresh CONFIDENCE_THRESH
                        Confidence threshold for face detection
  --faces-dir FACES_DIR
                        Path to faces stored dir
  --source SOURCE       Video file or video camera source. i.e 0 - webcam
  --max-num MAX_NUM     Maximum number of face detections from a frame
  --log-level LOG_LEVEL
                        Logging level
