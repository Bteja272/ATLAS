# ATLAS — AI Gym Movement Analysis

ATLAS is a computer-vision and machine-learning project for analyzing gym exercise movement from video.

The current prototype focuses on bent-over rows and uses MediaPipe Pose to extract body landmarks, calculate joint and torso metrics, detect repetitions, generate per-rep movement features, identify session-level anomalies, and prepare labeled data for supervised movement-pattern classification.

## Current Pipeline

YouTube Video  
→ yt-dlp  
→ OpenCV  
→ MediaPipe Pose  
→ 33 Body Landmarks  
→ Joint and Torso Angles  
→ Signal Smoothing  
→ Rep Detection and Segmentation  
→ Per-Rep Feature Engineering  
→ Rep Validation  
→ Isolation Forest Anomaly Detection  
→ Human Labeling Template

## Current Features

- YouTube video ingestion
- Pose estimation using MediaPipe Pose
- 33 body landmark extraction
- 3D world-coordinate landmark capture
- Joint-angle calculation
- Torso inclination analysis
- Left/right elbow asymmetry analysis
- Annotated pose video generation
- Landmark and angle CSV export
- Pose detection quality metrics
- Savitzky–Golay signal smoothing
- Automatic rep detection using peak/trough analysis
- Rep segmentation using extension and contraction points
- Rep-duration calculation
- Concentric and eccentric phase duration
- Left/right elbow range-of-motion calculation
- ROM asymmetry calculation
- Per-rep torso variation
- Set progression tracking
- Rep validation using duration and ROM checks
- Statistical torso-outlier detection
- Rep quality scoring
- Early-vs-late set movement comparison
- Standardized ML feature generation
- Isolation Forest session-level anomaly detection
- Human labeling dataset generation
- Guarded supervised-learning pipeline for future labeled data

## Current Results

The current tested video produced:

- 1,795 processed video frames
- 1,766 pose-detected frames
- 98.4% pose-detection rate
- 58,278 extracted landmark observations
- 33 landmarks per detected frame
- 14 initial rep candidates after segmentation
- 12 validated movement reps after quality filtering
- 10 rep-level features used for ML analysis
- 5 session-level anomaly candidates identified by Isolation Forest

The anomaly detections are treated as movement candidates for review rather than form-quality or injury-risk classifications.

## ML Features

The current rep-level ML pipeline uses features including:

- Rep duration
- Concentric duration
- Eccentric duration
- Left elbow ROM
- Right elbow ROM
- Mean elbow asymmetry
- Maximum elbow asymmetry
- Mean torso inclination
- Torso variation
- ROM asymmetry

## Movement Labels

The supervised-learning stage is being prepared around observable movement-pattern labels:

- `STABLE`
- `TORSO_DRIFT`
- `ASYMMETRIC`
- `LIMITED_ROM`
- `UNSURE`

ATLAS does not diagnose injuries or classify movement as medically safe or unsafe.

## Machine Learning

Notebook 03 establishes the initial ML pipeline using:

- StandardScaler
- Isolation Forest
- Logistic Regression
- Random Forest
- XGBoost
- Macro F1 evaluation
- Permutation feature importance

Supervised training is intentionally gated until enough manually labeled repetitions are collected across multiple videos and movement classes.

## Tech Stack

- Python
- MediaPipe
- OpenCV
- NumPy
- Pandas
- SciPy
- Matplotlib
- scikit-learn
- XGBoost
- yt-dlp

## Project Structure

```text
ATLAS/
├── README.md
├── notebooks/
│   ├── ATLAS_01_Pose_Extraction.ipynb
│   ├── ATLAS_02_Rep_Detection.ipynb
│   └── ATLAS_03_ML_Analysis.ipynb
├── requirements.txt
└── .gitignore
```

## Notebook Progress

### Notebook 01 — Pose Extraction and Movement Metrics

Implements:

- Video ingestion
- MediaPipe Pose inference
- 33 body landmark extraction
- World-coordinate landmark capture
- Joint-angle calculation
- Torso inclination
- Elbow asymmetry
- Annotated video generation
- Pose-quality metrics

### Notebook 02 — Rep Detection and Feature Engineering

Implements:

- Elbow-angle signal preprocessing
- Savitzky–Golay smoothing
- Peak/trough-based rep detection
- Extension-contraction rep segmentation
- Per-rep duration and movement features
- Rep validation
- ROM filtering
- Torso-outlier detection
- Early-vs-late movement comparison
- Validated rep dataset generation

### Notebook 03 — ML Analysis and Labeling

Implements:

- ML feature-matrix construction
- Feature scaling
- Feature-distribution analysis
- Correlation analysis
- Isolation Forest anomaly detection
- Session-level anomaly scoring
- Human labeling-template generation
- Guarded supervised-learning pipeline
- Logistic Regression, Random Forest, and XGBoost preparation
- Macro-F1 evaluation and feature-importance pipeline

## Current Status

The end-to-end prototype currently supports:

```text
Video
→ Pose Extraction
→ Movement Metrics
→ Rep Detection
→ Rep Validation
→ Per-Rep Features
→ ML Feature Space
→ Session-Level Anomaly Detection
→ Human Labeling
```

## Next Steps

- Collect additional bent-over-row videos
- Build a multi-video rep dataset
- Manually label observable movement patterns
- Validate rep-detection accuracy against ground truth
- Train supervised movement-pattern classifiers
- Compare Logistic Regression, Random Forest, and XGBoost
- Evaluate Precision, Recall, and Macro F1
- Add model explainability and feature importance
- Add FastAPI inference endpoints
- Build a React analysis dashboard
- Persist sessions and rep metrics in PostgreSQL
- Generate user-facing session reports and annotated playback
