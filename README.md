# 🌱 AgriTech-Crop-Health-Assistant

### 🌾 AI-Powered Crop Disease Identification and Agricultural Guidance
AgriTech-Crop-Health-Assistant is a web-based agricultural support application designed to help users identify potential crop diseases from plant leaf images and access useful information for crop care. It combines deep learning-based image classification with an AI-powered assistant to make crop health information easier to access.

The application provides a web interface where users can manage their accounts, submit plant images for analysis, review prediction results, and explore relevant agricultural guidance. Google Gemini API integration extends the application with conversational assistance for agricultural questions.

The goal is to demonstrate how machine learning, web development, and generative AI can be combined to build a practical tool for agricultural decision support.

---

## 1. The Problem This Project Addresses

Plant diseases can affect crop growth, product quality, and agricultural productivity. Early symptoms may be difficult for inexperienced growers to recognize, and accessing reliable guidance can take time.

Traditional disease identification may require expert consultation, agricultural knowledge, or manual examination of plant symptoms. These resources may not always be immediately available.

This project explores a technology-assisted approach to the problem:

- **Image-based identification:** Use a trained deep learning model to classify a submitted plant image.
- **Accessible information:** Present prediction results through a web application instead of requiring users to run machine learning scripts manually.
- **Conversational assistance:** Allow users to ask agricultural questions through an AI-powered chatbot.
- **Centralized access:** Provide account functionality and a web interface for accessing the application's available features.

The application is intended to support preliminary identification and learning. It is not a replacement for laboratory testing, agricultural specialists, or professional pesticide recommendations.

---

## 2. How the Application Works

The application combines a Django web application, an image classification model, and Google Gemini API integration.

### Step 1 — Access the application

Open the application in a web browser and register or log in using the available account functionality.

### Step 2 — Submit a plant image

Navigate to the crop disease detection feature and upload a clear image of a plant leaf. Images with good lighting and visible symptoms are generally more suitable for analysis.

### Step 3 — Run the disease classification model

The uploaded image is processed by the application's trained Inception-based convolutional neural network (CNN). The model produces a classification based on the classes it was trained to recognize.

### Step 4 — Review the result

View the prediction returned by the application. Treat it as a preliminary indication rather than a guaranteed diagnosis. Image quality, lighting, unfamiliar diseases, and differences between training images and real-world crops can affect accuracy.

### Step 5 — Ask agricultural questions

Use the AI assistant to ask relevant questions about plant care, possible symptoms, crop management, and general agricultural practices.

The assistant uses the Google Gemini API to generate conversational responses when API access is configured and available. Responses may be incomplete or inaccurate, so important crop-treatment decisions should be verified with a qualified agricultural expert.

### Step 6 — Use the other available features

Depending on the user's account and permissions, the application also provides features such as profile management, prediction history, user administration, and feedback monitoring.

---

## 3. Main Features

### Crop Image Classification

- Accepts plant leaf images through the web interface.
- Uses a trained Inception CNN model for image classification.
- Displays the prediction produced by the model.
- Demonstrates the integration of a machine learning model into a Django application.

### Google Gemini AI Assistant

- Provides a conversational interface for agricultural questions.
- Uses the Google Gemini API to generate responses.
- Supports general questions about plant symptoms, care practices, and crop management.
- Requires a valid API key and network access.
- Depends on the configured Gemini model and its availability, usage limits, and service conditions.

The assistant should not be treated as an authoritative source for disease diagnosis, pesticide dosage, or other safety-sensitive agricultural decisions.

### User Account Management

- Registration and login.
- Profile management.
- User-related functionality available through the application's web interface.

### Administrative Functionality

- User management and verification features.
- Access to administrative pages according to the application's existing permissions.
- Feedback monitoring and dashboard functionality where implemented.

### Web-Based Access

The application brings its supported features together in one web interface, allowing users to interact with the model and chatbot without needing to operate the model directly from a command line.

---

## 4. Technology Stack

| Technology | Purpose |
|---|---|
| Python | Application programming and machine learning integration |
| Django | Web framework, routing, views, and server-side functionality |
| HTML and CSS | Web page structure and styling |
| JavaScript | Client-side interactions where implemented |
| Inception CNN | Plant image classification |
| TensorFlow/Keras | Model loading and inference, depending on the existing model implementation |
| Google Gemini API | AI-generated conversational assistance |
| SQLite | Local database when configured through the project's Django settings |

The precise package versions and dependencies are defined in `requirements.txt`. The application should be run with the dependencies supported by its current code and model.

---

## 5. Application Architecture

The application can be understood as four cooperating components.

**Presentation layer:** Django templates provide the pages and interfaces used to register, log in, upload images, and view results.

**Application layer:** Django views process requests, coordinate user actions, validate submitted data, and connect the interface to the underlying functionality.

**Machine learning layer:** The trained Inception CNN processes plant images and produces classification results.

**AI assistance layer:** The chatbot sends supported prompts to the Google Gemini API and returns the generated response to the user.

At a high level, the image prediction flow is:

`User → Django interface → Image processing → Trained CNN → Prediction result`

The conversational flow is:

`User question → Django chatbot view → Google Gemini API → Generated response`

The Gemini API and the crop classification model serve different purposes: the CNN performs image classification, while Gemini generates conversational text. The chatbot should not be assumed to independently verify the CNN's prediction.

---

## 6. Installation and Local Setup

### Prerequisites

Install the following before starting:

- Python version compatible with the project dependencies.
- Git.
- A code editor such as Visual Studio Code.
- Internet access for downloading dependencies and using the Gemini API.
- A Google Gemini API key for chatbot functionality.

### Step 1 — Clone the repository

After the repository is published, clone it using:

```bash
git clone https://github.com/LakshmipadmajaPatha/AgriTech-Crop-Health-Assistant.git
cd AgriTech-Crop-Health-Assistant
```

### Step 2 — Create a virtual environment

On Windows:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, you can allow it for the current terminal session:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
.\.venv\Scripts\Activate.ps1
```

### Step 3 — Install dependencies

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Some machine learning dependencies may require a compatible Python version or additional system configuration. Follow any errors reported by pip and verify compatibility with the model-loading code.

### Step 4 — Configure the Google Gemini API key

Obtain an API key through Google AI Studio and configure it as an environment variable.

For the current PowerShell session:

```powershell
$env:GEMINI_API_KEY = "YOUR API KEY"
```

Replace the placeholder with your own key.


The application reads the key through the `GEMINI_API_KEY` environment variable. Chatbot functionality may be unavailable when the key is missing, invalid, rate-limited, or affected by a temporary service error.

### Step 5 — Check the model file

The application currently uses the trained model file:

```text
model_inception.h5
```

Ensure that this file is present in the expected location and that you have permission to use and distribute it. If the model is not included in the repository, obtain an authorized copy and place it where the application expects it.

### Step 6 — Apply database migrations

Run:

```powershell
python manage.py migrate
```

This creates or updates the local database tables required by the Django application.

### Step 7 — Start the development server

```powershell
python manage.py runserver
```

Open the local address in your browser:

http://127.0.0.1:8000/

Use the application's available registration and login pages to begin testing.

**Note:** These instructions describe the standard Django workflow. If the repository's existing configuration requires additional setup, follow the error messages and project-specific settings.

---

## 7. Example Use Cases

### Farmers and growers

A user can submit a plant leaf image to obtain a preliminary classification and use the chatbot to learn about general plant care.

### Agricultural students

Students can explore how a CNN model, Django views, web forms, and a generative AI API work together in an agricultural application.

### Developers

Developers can study model inference, server-side request handling, environment-variable configuration, chatbot integration, and the organization of a Django project.

### Agricultural technology demonstrations

The project can serve as a prototype for exploring how digital tools may improve access to preliminary crop health information.

These use cases describe potential applications. Actual effectiveness in agricultural environments requires testing with representative images, validated labels, and appropriate expert review.

---

## 8. Limitations and Responsible Use

- Model performance depends on the training data, recognized classes, image quality, and real-world conditions.
- A prediction does not establish a confirmed disease diagnosis.
- The application may not recognize diseases, pests, nutrient deficiencies, or environmental stress outside the model's training classes.
- Gemini responses may be inaccurate, outdated, or unsuitable for a particular crop or region.
- Pesticide selection, dosage, and application decisions should follow product labels and qualified local agricultural guidance.
- The availability of chatbot responses depends on API credentials, quotas, network connectivity, and Google's service availability.
- The application should be tested for security, reliability, and data protection before production deployment.

---

## 9. Future Improvements

Potential enhancements include:

- Evaluate the model using a held-out dataset and report appropriate classification metrics.
- Add confidence information and clearer warnings for uncertain predictions, if supported by the model.
- Expand the training dataset with verified images of locally relevant crops and diseases.
- Add tests for image uploads, authentication, and chatbot error handling.
- Improve accessibility, mobile responsiveness, and user guidance.
- Add a verified agricultural knowledge base for responses grounded in trusted sources.
- Introduce secure production deployment, logging, monitoring, and appropriate data-retention controls.
- Evaluate performance with agricultural experts and real-world users before relying on predictions for crop treatment.

---

## 10. Project Background and Attribution

This repository is an adapted version of an existing crop disease detection project. The existing implementation provides the starting point for the application's web interface and machine learning functionality.

Original project:
https://github.com/kiransainagendra/Farmers-Crop-Disease-Detection-System-AgriTech

This repository documents the adaptation and its configuration, including Google Gemini API integration and fixes made to handle missing profile images in relevant templates.

The original project and model remain subject to their applicable ownership and licensing terms. Confirm permission to redistribute the original code and model before publishing this repository publicly.

---

## 11. Contributing and Learning

Developers can explore the codebase, identify areas for improvement, and propose changes that improve correctness, maintainability, usability, and responsible AI use.

Before contributing, verify dependency compatibility, avoid committing secrets or private user data, and test changes locally.

---

## Conclusion

AgriTech-Crop-Health-Assistant demonstrates an approach to combining deep learning, web development, and generative AI for preliminary crop health support. By integrating image classification with a conversational assistant, the project provides a foundation for exploring agricultural technology while recognizing the importance of model validation, expert verification, and responsible use.
