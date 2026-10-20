# ATLAS — AI Gym Movement Analysis

ATLAS is a computer-vision project for analyzing gym exercise movement from video.

The current prototype focuses on bent-over rows and uses MediaPipe Pose to extract body landmarks, calculate joint and torso angles, visualize movement patterns, and generate annotated video output.

## Current Pipeline

YouTube Video
→ yt-dlp
→ OpenCV
→ MediaPipe Pose
→ 33 Body Landmarks
→ Joint and Torso Angles
→ Movement Visualization

## Current Features

- YouTube video ingestion
- Pose estimation
- 33 body landmark extraction
- Joint angle calculation
- Torso inclination analysis
- Left/right elbow asymmetry
- Annotated pose video generation
- CSV export of landmarks and angles
- Pose detection quality metrics

## Tech Stack

- Python
- MediaPipe
- OpenCV
- NumPy
- Pandas
- Matplotlib
- yt-dlp

## Current Status

Notebook 01 establishes the pose-estimation and movement-analysis foundation.

Next:
- Rep detection
- Rep segmentation
- Per-rep features
- Technique drift analysis
