Step 1: Complete the Excel Template
1.1 Stakeholder Analysis
Make Perspective: Identify the stakeholders involved in the creation of the product, such as:
AI Engineers
Data Scientists
Software Developers
Project Managers
Use Perspective: Identify the stakeholders who will use the product or be affected by it, such as:
C-Suite Executives at ArtTech Showcase
Law Enforcement Officers
End-users of the product
1.2 Requirements Gathering
Features:
People Recognition Algorithm
Real-Time Recognition Capability
Movement Tracking
Notification System
Hardware Requirements:
High-resolution camera
Robust processor
Motorised pan-tilt-zoom (PTZ) camera
Speaker system
Software Requirements:
Computer Vision software
Machine Learning algorithms
Tracking algorithms
Customisable alerting system
1.3 Resource Breakdown Structure (RBS)
Labor Resources:
2 Data Engineers ($35/hour each)
1 AI Engineer ($28/hour)
1 Data Scientist ($42/hour)
Include these details in the provided Excel template.
1.4 Work Breakdown Structure (WBS)
Hardware Development Plan:

Tasks:
Setup high-resolution camera
Integrate PTZ camera
Install speaker system
Sub-Tasks:
Test camera functionality
Calibrate PTZ camera for tracking
Test speaker system for audio notifications
Software Development Plan:

Tasks:
Develop People Recognition Algorithm
Implement Real-Time Recognition
Integrate Movement Tracking Algorithm
Implement Notification System
Sub-Tasks:
Train the recognition algorithm
Optimize real-time processing
Test tracking accuracy
Customize alerting options
1.5 Project Canvas
Complete the project canvas sections in the template, including objectives, key activities, resources, stakeholders, etc.
Step 2: Develop the Proof-of-Concept (POC)
2.1 Load Images and Detect Faces
Use the provided Python code to load images from a local directory and apply face detection.
2.2 Predict Real Faces
Classify the faces detected as either real or not real based on predefined criteria.
2.3 Draw Bounding Boxes
For correctly predicted faces, draw bounding boxes around them using OpenCV.
2.4 Save the Predicted Images
Save the images with bounding boxes to a specified output directory for verification.
2.5 Evaluate Accuracy and F1 Score
Ensure the POC achieves a minimum of 80% accuracy and F1 score.
2.6 Complete Confusion Matrix in Excel
After executing the POC, complete the confusion matrix in the Excel template based on the results.
