Azure AI NLP Project
This project is a web-based application that leverages Azure Cognitive Services for various Natural Language Processing (NLP) tasks. It consists of a FastAPI backend and an HTML/JavaScript frontend.

Key Features
Text Analysis: Opinion Mining (sentiment) and Key Phrase Extraction.

Language Detection: Identifies the language of input text.

OCR (Optical Character Recognition): Extracts text from images, preserving line breaks.

Text-to-Speech: Converts text into natural-sounding speech.

Technologies Used
Backend: FastAPI (Python)

Frontend: HTML, CSS (Bootstrap), JavaScript

Azure Cognitive Services: Language, Computer Vision, Speech

Local Development Setup
To run this application locally, follow these steps:

1. Azure Setup
Create Resources: In the Azure Portal, create instances of Azure Language Service, Azure Computer Vision Service, and Azure Speech Service.

Get Keys & Endpoints: Obtain the API keys and endpoint URLs for each service. Note the Region for your Speech Service.

2. Backend Setup
Clone the repository:

git clone <repository-url>
cd azure-nlp-app/backend

Install dependencies:

python -m venv venv
source venv/bin/activate # or .\venv\Scripts\activate on Windows
pip install -r requirements.txt

(Ensure requirements.txt includes: fastapi, uvicorn[standard], python-multipart, azure-ai-textanalytics, azure-cognitiveservices-vision-computervision, azure-cognitiveservices-speech, msrest)

Set Environment Variables: Replace placeholders with your actual Azure credentials.

# Example for macOS/Linux
export AZURE_LANGUAGE_KEY="YOUR_LANGUAGE_KEY"
export AZURE_LANGUAGE_ENDPOINT="YOUR_LANGUAGE_ENDPOINT"
export AZURE_VISION_KEY="YOUR_VISION_KEY"
export AZURE_VISION_ENDPOINT="YOUR_VISION_ENDPOINT"
export AZURE_SPEECH_KEY="YOUR_SPEECH_KEY"
export AZURE_SPEECH_REGION="YOUR_SPEECH_REGION"

Run the backend:

uvicorn main:app --reload

The backend will run on http://127.0.0.1:8000.

3. Frontend Setup
Navigate to the frontend directory:

cd ../frontend

Open index.html in your web browser.

Usage
With both the backend and frontend running, you can:

Analyze text for sentiment and key phrases.

Detect the language of text.

Extract text from uploaded images.

Convert text to speech.

License
This project is open-source under the MIT License.
