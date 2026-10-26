# Real-Time Sign Language Recognition
## Project Context and Requirements

## 1. Project Identity

**Project Name:** Real-Time Sign Language Recognition

**Project Type:** Full-Stack Machine Learning Application

**Application Category:** Computer Vision and Deep Learning

**Primary Goal:** Recognize isolated sign language gestures from webcam input and convert them into readable text in real time.

**Frontend:** React.js, TypeScript, Vite

**Backend:** FastAPI, Python

**Machine Learning:** PyTorch, LSTM, MediaPipe, OpenCV

**Dataset:** WLASL

## 2. Project Overview

Real-Time Sign Language Recognition is a full-stack machine learning application designed to recognize sign language gestures using a webcam.

The application captures video frames from the user's camera, extracts hand and relevant body landmarks using MediaPipe, and processes these landmarks as temporal sequences.

A trained LSTM model analyzes the sequence and predicts the corresponding sign language word.

The predicted word and confidence score are returned to the frontend and displayed to the user.

The project combines computer vision, deep learning, backend API development, and frontend development into a single integrated application.

## 3. Problem Statement

Communication between sign language users and people unfamiliar with sign language can be challenging.

Traditional communication methods may require interpreters or specialized assistance, which may not always be immediately available.

Sign language recognition systems can help reduce this communication barrier by identifying gestures and converting them into readable text.

However, sign language recognition is a complex machine learning problem because gestures contain temporal information, hand movements, and variations between individuals.

This project aims to develop a webcam-based recognition system that can classify isolated sign language gestures using a machine learning model.

## 4. Project Objectives

The main objectives are:

1. Develop a webcam-based sign language recognition application.
2. Extract relevant hand and body landmarks from video frames.
3. Convert landmark data into temporal sequences.
4. Train an LSTM model to recognize isolated sign language gestures.
5. Develop a FastAPI backend for model inference.
6. Build a React frontend using TypeScript.
7. Integrate webcam input with backend prediction.
8. Display recognized words and confidence scores.
9. Maintain a basic prediction history.
10. Create a modular architecture that supports future improvements.

## 5. Project Scope

### 5.1 Included Features

The initial application will include:

- Webcam access.
- Video frame capture.
- Landmark extraction.
- Temporal sequence processing.
- LSTM-based sign classification.
- Backend prediction API.
- Frontend-backend integration.
- Recognized word display.
- Confidence score display.
- Basic prediction history.
- Prediction stabilization.
- Basic error handling.

### 5.2 Out of Scope

The initial version will not include:

- Continuous sign language sentence translation.
- Full natural language understanding.
- Speech-to-sign language translation.
- Sign language avatar generation.
- Advanced user authentication.
- Cloud-based model training.
- Mobile application development.
- Large-scale multilingual sign recognition.

The project focuses on isolated sign recognition rather than complete sentence translation.

## 6. Target Users

The application is intended for:

- People interested in sign language recognition.
- Developers exploring computer vision.
- Students learning machine learning.
- Researchers experimenting with gesture recognition.
- Users interested in webcam-based accessibility applications.

## 7. User Workflow

The expected user workflow is:

1. Open the application.
2. Allow webcam access.
3. Start the recognition session.
4. Perform a sign language gesture.
5. The webcam captures video frames.
6. The backend extracts landmarks.
7. The model predicts the sign.
8. The frontend displays the recognized word.
9. The application displays the confidence score.
10. The prediction is added to the session history.

## 8. Functional Requirements

### 8.1 Webcam

- The frontend must access the user's webcam.
- The application must display the webcam feed.
- The application must handle camera permission errors.
- The application must capture frames for prediction.

### 8.2 Landmark Extraction

- The system must process video frames.
- MediaPipe must extract relevant landmarks.
- The system must handle frames where landmarks are not detected.
- Landmark output must follow a consistent format.

### 8.3 Sequence Processing

- The system must collect landmark data over time.
- The system must prepare fixed-length sequences for the model.
- The initial baseline sequence length is 30 frames.
- Preprocessing must be consistent during training and inference.

### 8.4 Machine Learning

- The system must use an LSTM-based classifier.
- The model must be trained using the prepared dataset.
- The model must classify gestures into supported classes.
- The model must return prediction probabilities or confidence scores.
- The trained model must be loadable by the backend.

### 8.5 Backend

- The backend must use FastAPI.
- The backend must expose a health-check endpoint.
- The backend must expose a prediction endpoint.
- The backend must validate incoming data.
- The backend must process frames and generate predictions.
- The backend must return structured responses.

### 8.6 Frontend

- The frontend must use React and TypeScript.
- The frontend must display the webcam feed.
- The frontend must communicate with the backend.
- The frontend must display predictions.
- The frontend must display confidence.
- The frontend must maintain a basic prediction history.

### 8.7 Prediction Stabilization

The application should reduce unstable predictions caused by individual frames.

Possible approaches include:

- Collecting predictions over multiple frames.
- Applying a confidence threshold.
- Using a rolling prediction window.
- Requiring repeated predictions before updating the displayed word.

The final stabilization method will be selected during implementation.

## 9. Non-Functional Requirements

### Performance

The application should provide responsive prediction updates and minimize unnecessary processing.

### Reliability

The application should handle missing landmarks, invalid requests, and backend errors gracefully.

### Maintainability

The codebase should use modular components and clear separation of responsibilities.

### Scalability

The architecture should support additional classes, improved models, and future communication methods.

### Usability

The interface should be understandable and provide clear feedback about camera access and prediction status.

### Consistency

Training and inference preprocessing must use the same landmark representation and sequence format.

## 10. Technology Stack

### Frontend

- React.js
- TypeScript
- Vite
- HTML
- CSS

### Backend

- Python
- FastAPI
- Pydantic
- Uvicorn

### Machine Learning

- PyTorch
- LSTM
- MediaPipe
- OpenCV
- NumPy
- Pandas
- Matplotlib

### Dataset

- WLASL
- Selected initial subset: 100 classes

### Communication

- REST API for the initial implementation.
- WebSockets may be considered for future real-time communication improvements.

## 11. Machine Learning Workflow

### Step 1: Dataset Exploration

Explore the WLASL dataset and identify the selected sign classes.

Review:

- Dataset structure.
- Video availability.
- Class distribution.
- Video quality.
- Sample duration.
- Potential class imbalance.

### Step 2: Video Preprocessing

Prepare video samples for landmark extraction.

Tasks may include:

- Reading video frames.
- Handling frame dimensions.
- Sampling frames.
- Handling unreadable videos.
- Preparing consistent input formats.

### Step 3: Landmark Extraction

Use MediaPipe to extract hand and relevant body landmarks.

The extracted landmarks will represent the movement and spatial information of the gesture.

### Step 4: Sequence Preparation

Convert landmark data into fixed-length temporal sequences.

The initial baseline sequence length is 30 frames.

### Step 5: Dataset Splitting

Split the dataset into training, validation, and testing subsets.

The split should avoid leakage between related samples where possible.

### Step 6: Model Training

Train an LSTM classifier using the prepared sequences.

Initial baseline configuration:

- Sequence length: 30 frames.
- Hidden size: 128.
- LSTM layers: 2.
- Output classes: 100.
- Loss: Cross Entropy.
- Optimizer: Adam.

These values are initial experimental settings and may change based on model performance.

### Step 7: Model Evaluation

Evaluate the model using appropriate classification metrics.

Potential metrics include:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- Confusion matrix.

### Step 8: Model Inference

Load the trained model into the backend.

The backend will process incoming landmark sequences and return predictions.

## 12. Backend Requirements

The backend will be developed using FastAPI.

### Main Responsibilities

- Receive frames from the frontend.
- Validate requests.
- Extract landmarks.
- Prepare temporal sequences.
- Run model inference.
- Return prediction results.
- Handle processing errors.

### Main Endpoints

#### Health Check

`GET /health`

Returns the basic backend status.

#### Prediction

`POST /predict`

Receives frame data and returns the recognized sign.

Example response:

```json
{
  "prediction": "HELLO",
  "confidence": 0.94,
  "status": "success"
}
```

The API response structure may be expanded during development.

## 13. Frontend Requirements

The frontend will use React, TypeScript, and Vite.

### Main Components

#### WebcamView

Responsible for:

- Webcam access.
- Displaying the video feed.
- Capturing frames.
- Camera status.

#### PredictionDisplay

Responsible for displaying the recognized sign.

#### ConfidenceDisplay

Responsible for displaying the prediction confidence.

#### PredictionHistory

Responsible for displaying previous predictions during the current session.

#### Home

The main application page that combines the recognition interface and its components.

## 14. Project Structure

```text
sign-language-recognition/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── splits/
│
├── notebooks/
│   ├── 01_dataset_exploration.ipynb
│   ├── 02_landmark_extraction.ipynb
│   ├── 03_model_training.ipynb
│   └── 04_model_evaluation.ipynb
│
├── src/
│   ├── preprocessing/
│   │   ├── __init__.py
│   │   ├── video_processor.py
│   │   ├── landmark_extractor.py
│   │   └── sequence_processor.py
│   │
│   ├── models/
│   │   ├── __init__.py
│   │   ├── lstm_classifier.py
│   │   └── inference.py
│   │
│   ├── training/
│   │   ├── __init__.py
│   │   ├── dataset.py
│   │   ├── train.py
│   │   └── evaluate.py
│   │
│   └── utils/
│       ├── __init__.py
│       ├── config.py
│       └── visualization.py
│
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py
│   │   ├── dependencies.py
│   │   │
│   │   ├── api/
│   │   │   ├── routes/
│   │   │   │   ├── __init__.py
│   │   │   │   ├── health.py
│   │   │   │   └── prediction.py
│   │   │   │
│   │   │   └── schemas/
│   │   │       ├── __init__.py
│   │   │       └── prediction.py
│   │   │
│   │   ├── services/
│   │   │   ├── __init__.py
│   │   │   ├── prediction_service.py
│   │   │   └── landmark_service.py
│   │   │
│   │   └── core/
│   │       ├── __init__.py
│   │       └── config.py
│   │
│   ├── tests/
│   │   ├── __init__.py
│   │   ├── test_health.py
│   │   └── test_prediction.py
│   │
│   ├── requirements.txt
│   ├── .env.example
│   └── .gitignore
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── WebcamView.tsx
│   │   │   ├── PredictionDisplay.tsx
│   │   │   ├── ConfidenceDisplay.tsx
│   │   │   └── PredictionHistory.tsx
│   │   │
│   │   ├── pages/
│   │   │   └── Home.tsx
│   │   │
│   │   ├── services/
│   │   │   └── predictionService.ts
│   │   │
│   │   ├── hooks/
│   │   │   └── useWebcam.ts
│   │   │
│   │   ├── types/
│   │   │   └── prediction.ts
│   │   │
│   │   ├── utils/
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   └── index.css
│   │
│   ├── index.html
│   ├── package.json
│   ├── tsconfig.json
│   ├── tsconfig.app.json
│   ├── tsconfig.node.json
│   ├── vite.config.ts
│   ├── .env.example
│   └── .gitignore
│
├── models/
│   └── .gitkeep
│
├── docs/
│   └── architecture.md
│
├── context.md
├── README.md
├── .gitignore
└── requirements.txt
```

## 15. Development Phases

### Phase 1: Dataset Preparation

- Explore WLASL.
- Select initial classes.
- Prepare video samples.
- Extract landmarks.
- Generate temporal sequences.

### Phase 2: Model Development

- Build the dataset pipeline.
- Implement the LSTM classifier.
- Train the model.
- Evaluate classification performance.
- Save the trained model.

### Phase 3: Backend Development

- Set up FastAPI.
- Implement health check.
- Implement prediction endpoint.
- Integrate landmark extraction.
- Integrate model inference.
- Test API responses.

### Phase 4: Frontend Development

- Set up React and TypeScript.
- Build webcam interface.
- Implement frame capture.
- Connect frontend to backend.
- Display prediction results.
- Add confidence and prediction history.

### Phase 5: Integration

- Connect all application components.
- Test webcam communication.
- Validate prediction flow.
- Improve prediction stability.
- Handle errors.

### Phase 6: Testing and Documentation

- Test model inference.
- Test API endpoints.
- Test frontend interactions.
- Document setup instructions.
- Document architecture.
- Prepare the final project demonstration.

## 16. Acceptance Criteria

The initial project will be considered functional when:

- The frontend can access the webcam.
- Video frames can be captured.
- The backend can receive frame data.
- MediaPipe can extract landmarks.
- The system can prepare model input sequences.
- The trained LSTM model can generate predictions.
- The backend returns a structured prediction response.
- The frontend displays the recognized sign.
- The frontend displays confidence.
- The application handles basic errors.
- The prediction history works during a session.

## 17. Future Improvements

Potential future improvements include:

- Increasing the number of recognized signs.
- Improving recognition accuracy.
- Supporting continuous sign recognition.
- Adding sentence-level recognition.
- Adding WebSocket communication.
- Improving prediction stabilization.
- Supporting additional datasets.
- Optimizing inference speed.
- Deploying the application.
- Exploring mobile support.

## 18. Success Criteria

The project aims to demonstrate:

- Successful webcam-based sign recognition.
- A working computer vision pipeline.
- A trained LSTM classification model.
- A functional FastAPI backend.
- A React and TypeScript frontend.
- Successful frontend-backend integration.
- A clear and understandable recognition interface.
- A modular architecture suitable for future development.

## 19. Final Project Summary

Real-Time Sign Language Recognition is a full-stack computer vision application that recognizes isolated sign language gestures from webcam input.

The system uses MediaPipe to extract landmarks, temporal sequence processing to prepare model input, and a PyTorch LSTM classifier to recognize signs.

The backend is developed using FastAPI, while the frontend is built with React and TypeScript.

The initial version focuses on isolated sign recognition, real-time prediction display, confidence scores, and basic prediction history.

The architecture is designed to remain modular and extensible, allowing future improvements in recognition accuracy, supported classes, and continuous sign language processing.
