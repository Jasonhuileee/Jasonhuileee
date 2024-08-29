- 👋 Hi, I’m @Jasonhuileee
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Jasonhuileee/Jasonhuileee is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes. 



--->
import cv2
import os

# Paths
input_path = r'./data'
output_path = r'./output_images'
os.makedirs(output_path, exist_ok=True)

# Load face and eye cascades
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')
eye_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_eye.xml')

def detect_and_draw_objects(img, classifier, color, scaleFactor=1.2, minNeighbors=5, minSize=(30, 30)):
    objects = classifier.detectMultiScale(img, scaleFactor=scaleFactor, minNeighbors=minNeighbors, minSize=minSize)
    for (x, y, w, h) in objects:
        cv2.rectangle(img, (x, y), (x+w, y+h), color, 2)
    return objects

# Metrics initialization
TP = TN = FP = FN = 0

def classify_face(filename):
    return 'real' if filename.startswith('P') else 'not real'

for filename in os.listdir(input_path):
    if filename.endswith('.jpg'):
        img_path = os.path.join(input_path, filename)
        img = cv2.imread(img_path)
        if img is None:
            print(f"Error: Could not read image {filename}.")
            continue

        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        gray = cv2.equalizeHist(gray)

        # Detect faces
        faces = detect_and_draw_objects(gray, face_cascade, (0, 255, 0))

        # Detect eyes in the face regions
        for (x, y, w, h) in faces:
            face_roi = gray[y:y+h, x:x+w]
            eyes = detect_and_draw_objects(face_roi, eye_cascade, (255, 0, 0))
            for (ex, ey, ew, eh) in eyes:
                cv2.rectangle(img, (x + ex, y + ey), (x + ex + ew, y + ey + eh), (255, 0, 0), 2)

        # Save the processed image
        cv2.imwrite(os.path.join(output_path, filename), img)
        print(f'Saved {filename}')

        # Classification and metrics update
        classification = classify_face(filename)
        detected_faces = len(faces) > 0

        if detected_faces:
            if classification == 'real':
                TP += 1
            else:
                FP += 1
        else:
            if classification == 'real':
                FN += 1
            else:
                TN += 1

# Calculate and print accuracy
total_images = TP + TN + FP + FN
accuracy = (TP + TN) / total_images * 100 if total_images > 0 else 0.0

print(f"TP: {TP}, TN: {TN}, FP: {FP}, FN: {FN}")
print(f"Accuracy: {accuracy:.2f}%")
