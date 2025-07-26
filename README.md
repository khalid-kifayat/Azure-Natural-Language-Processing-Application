# Azure-Natural-Language-Processing-Application

Azure AI NLP Project
This project provides a web-based application leveraging Azure Cognitive Services for various Natural Language Processing (NLP) tasks. It features a FastAPI backend that integrates with Azure AI services and a responsive HTML/JavaScript frontend for an interactive user experience.

Table of Contents
Azure AI NLP Project

Table of Contents

Key Features

Architecture

Prerequisites

Azure Setup

1. Create Azure Cognitive Services Resources

2. Obtain API Keys and Endpoints

Local Development Setup

1. Clone the Repository

2. Backend Setup (FastAPI)

3. Frontend Setup (HTML/JavaScript)

Usage

Deployment (High-Level)

Contributing

License

Key Features
This application covers the following NLP functionalities:

Backend (FastAPI):
Text Analysis:

Opinion Mining: Advanced sentiment analysis with aspect-based sentiment detection.

Key Phrase Extraction: Identifies important concepts and phrases from text.

Language Detection: Automatically detects the language of input text.

OCR (Optical Character Recognition): Extracts text from images using Azure's high-accuracy Read API, preserving line breaks.

Text-to-Speech Conversion: Synthesizes natural-sounding speech from text with customizable voices and languages.

Frontend (HTML/JavaScript):
Interactive web interface with Bootstrap styling for a modern and responsive design.

Real-time processing of all NLP services with dynamic display of results.

File upload capabilities for images (for OCR).

Audio playback for generated speech.

Progress indicators and basic error handling for a smooth user experience.

Complete Implementation:
Modular service architecture for easy maintenance and scalability.

Comprehensive API endpoints for each NLP task.

Seamless Azure Cognitive Services integration using appropriate SDKs.

Robust error handling and input validation.

Docker deployment configuration (conceptual, not fully implemented in this README but part of the project design).

Security best practices (e.g., environment variables for keys).

Architecture
The project follows a decoupled architecture:

Backend: Built with FastAPI (Python) to expose RESTful APIs. It acts as an intermediary, handling requests from the frontend and communicating with Azure Cognitive Services.

Frontend: A static web application using HTML, CSS (Bootstrap), and JavaScript. It provides the user interface and interacts with the FastAPI backend via asynchronous API calls.

graph TD
    User --> Frontend(HTML/JS Web App)
    Frontend --> Backend(FastAPI Application)
    Backend --> AzureLanguageService(Azure Language Service)
    Backend --> AzureVisionService(Azure Computer Vision Service)
    Backend --> AzureSpeechService(Azure Speech Service)
    AzureLanguageService -- Text Analysis, Language Detection --> Backend
    AzureVisionService -- OCR --> Backend
    AzureSpeechService -- Text-to-Speech --> Backend
    Backend -- Audio Stream --> Frontend

Prerequisites
Before running this application, ensure you have the following installed:

Python 3.9+: For the FastAPI backend.

Download Python

pip: Python's package installer (usually comes with Python).

Git: For cloning the repository.

Download Git

An Azure Account: With an active subscription.

Azure Setup
You need to provision and configure Azure Cognitive Services resources.

1. Create Azure Cognitive Services Resources
Go to the Azure Portal and create the following resources:

Language Service: For Text Analysis (Opinion Mining, Key Phrase Extraction, Language Detection).

Computer Vision Service: For OCR.

Speech Service: For Text-to-Speech.

2. Obtain API Keys and Endpoints
For each service you create:

Navigate to its resource page in the Azure Portal.

Go to the "Keys and Endpoint" section (usually under "Resource Management").

Copy one of the Keys and the Endpoint URL.

For the Speech Service, also note the Region where you deployed it (e.g., eastus, westus2).

Keep these values handy; you'll need them for the backend configuration.

Local Development Setup
Follow these steps to get the application running on your local machine.

1. Clone the Repository
First, clone this GitHub repository to your local machine:

git clone <repository-url> # Replace <repository-url> with the actual URL
cd azure-nlp-app

2. Backend Setup (FastAPI)
The backend handles all the Azure AI service integrations.

Navigate to the backend directory:

cd backend

Create and activate a Python virtual environment (recommended):

python -m venv venv
# On Windows:
.\venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

Install Python dependencies:

pip install -r requirements.txt

The requirements.txt should contain:

fastapi
uvicorn[standard]
python-multipart
azure-ai-textanalytics==5.3.0
azure-cognitiveservices-vision-computervision==0.9.0
azure-cognitiveservices-speech==1.38.0
msrest

Set Azure Environment Variables:
This is crucial. Replace YOUR_AZURE_LANGUAGE_KEY, YOUR_AZURE_LANGUAGE_ENDPOINT, etc., with the actual keys and endpoints you obtained from Azure.

On macOS/Linux (Bash/Zsh):

export AZURE_LANGUAGE_KEY="YOUR_AZURE_LANGUAGE_KEY"
export AZURE_LANGUAGE_ENDPOINT="YOUR_AZURE_LANGUAGE_ENDPOINT"
export AZURE_VISION_KEY="YOUR_AZURE_VISION_KEY"
export AZURE_VISION_ENDPOINT="YOUR_AZURE_VISION_ENDPOINT"
export AZURE_SPEECH_KEY="YOUR_AZURE_SPEECH_KEY"
export AZURE_SPEECH_REGION="YOUR_AZURE_SPEECH_REGION" # e.g., "eastus"

On Windows (Command Prompt):

set AZURE_LANGUAGE_KEY="YOUR_AZURE_LANGUAGE_KEY"
set AZURE_LANGUAGE_ENDPOINT="YOUR_AZURE_LANGUAGE_ENDPOINT"
set AZURE_VISION_KEY="YOUR_AZURE_VISION_KEY"
set AZURE_VISION_ENDPOINT="YOUR_AZURE_VISION_ENDPOINT"
set AZURE_SPEECH_KEY="YOUR_AZURE_SPEECH_KEY"
set AZURE_SPEECH_REGION="YOUR_AZURE_SPEECH_REGION"

On Windows (PowerShell):

$env:AZURE_LANGUAGE_KEY="YOUR_AZURE_LANGUAGE_KEY"
$env:AZURE_LANGUAGE_ENDPOINT="YOUR_AZURE_LANGUAGE_ENDPOINT"
$env:AZURE_VISION_KEY="YOUR_AZURE_VISION_KEY"
$env:AZURE_VISION_ENDPOINT="YOUR_AZURE_VISION_ENDPOINT"
$env:AZURE_SPEECH_KEY="YOUR_AZURE_SPEECH_KEY"
$env:AZURE_SPEECH_REGION="YOUR_AZURE_SPEECH_REGION"

Note: These environment variables are session-specific. If you close your terminal, you'll need to set them again. For persistent development, consider using a .env file and python-dotenv (not included in current code but a common practice).

Run the FastAPI application:

uvicorn main:app --reload

The backend will start running, typically at http://127.0.0.1:8000. Keep this terminal window open.

3. Frontend Setup (HTML/JavaScript)
The frontend is a simple HTML file that runs directly in your browser.

Navigate to the frontend directory:

cd ../frontend # If you are still in the backend directory
# Or if you are in the main project directory:
# cd frontend

Open index.html in your web browser:
Simply double-click the index.html file in your file explorer, or drag it into your browser.

Usage
Once both the backend (FastAPI) and frontend (index.html) are running:

Text Analysis: Enter text into the "Text Analysis" textarea and click "Analyze Text" to see sentiment and key phrases.

Language Detection: Enter text into the "Language Detection" textarea and click "Detect Language".

OCR: Click "Choose File" under "OCR", select an image (e.g., a screenshot with text), and click "Perform OCR" to extract text.

Text-to-Speech: Enter text into the "Text-to-Speech" textarea, select a voice, and click "Generate Speech" to hear the synthesized audio.

The results will appear in the respective result boxes below each section.

Deployment (High-Level)
For production deployment, consider the following:

Backend: Deploy the FastAPI application to Azure App Service or Azure Container Apps, potentially using Docker containers.

Frontend: Deploy the static index.html and associated assets to Azure Static Web Apps or Azure Blob Storage (configured for static website hosting).

CI/CD: Implement Continuous Integration/Continuous Deployment pipelines (e.g., Azure DevOps, GitHub Actions) to automate builds and deployments.

Security: Utilize Azure Key Vault for managing API keys and Azure Managed Identities for secure authentication between Azure services.

Contributing
Contributions are welcome! Please feel free to open issues or submit pull requests.

License
This project is open-source and available under the MIT License.
