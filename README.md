# Belajar Penerapan Machine Learning dengan Google Cloud

This project is the final submission for the "Belajar Penerapan Machine Learning dengan Google Cloud" course on Dicoding. It demonstrates the implementation of machine learning using TensorFlow.js and Google Cloud Firestore in a web-based application.

## Features

- Prediction Model: Uses TensorFlow.js to load a pre-trained model and classify images as "Cancer" or "Non-Cancer."
- Data Storage: Stores prediction results in Google Cloud Firestore.
- REST API: Implements Hapi.js to provide REST endpoints for predictions and prediction histories.
- Error Handling: Custom error classes for handling user input and server-side errors.

## Technologies Used

- TensorFlow.js: For running the pre-trained machine learning model.
- Google Cloud Firestore: To store prediction data.
- Hapi.js: As the web framework for building the REST API.
- Node.js: For the backend runtime environment.
- dotenv: For managing environment variables.

## Installation

### Prerequisites

- Node.js: Version 16.x or 18.x recommended (TensorFlow.js may not support Node.js 20.x).
- Google Cloud Account: For setting up Firestore and storing your ML model.

### Steps

1. Clone the repository:
   bash
   git clone <repository-url>
   cd project-directory
   

2. Install dependencies:
   bash
   npm install
   

3. Create a .env file:
      PORT=8080
   MODEL_URL=<URL-to-your-TensorFlow-model>
  

4. Run the application:
   bash
   npm start
   

## API Endpoints

### POST /predict
Description: Perform image classification.

#### Request:
- Payload:
  - image (file): JPEG or PNG image file.
- Headers:
  - Content-Type: multipart/form-data

#### Response:
json
```
{
  "status": "success",
  "message": "Model is predicted successfully",
  "data": {
    "id": "<unique-id>",
    "result": "Cancer",
    "suggestion": "Segera periksa ke dokter!",
    "createdAt": "<ISO-timestamp>"
  }
}
```


### GET /predict/histories
Description: Retrieve all prediction histories.

#### Response:
json
```
{
  "status": "success",
  "data": [
    {
      "id": "<unique-id>",
      "history": {
        "result": "Non-cancer",
        "createdAt": "<ISO-timestamp>",
        "suggestion": "Penyakit kanker tidak terdeteksi."
      }
    }
  ]
}
```


## Error Handling

- InputError: Thrown when invalid data is provided.
- General Errors: All other exceptions are handled gracefully, returning a meaningful error message.

## Deployment

1. Deploy the application to a Node.js hosting service (e.g., Google Cloud Run or Heroku).
2. Ensure the environment variables (PORT, MODEL_URL) are set correctly.
3. Configure Google Cloud Firestore for data storage.

## Notes

- This project is built for educational purposes.
- Ensure proper validation and security when using in production.

---
