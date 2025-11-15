A simple voice-driven chatbot that listens for a wake word (Alpha), records a spoken question, transcribes it with SpeechRecognition (Google Web Speech), sends the text to Google Gemini (via google-generativeai), and speaks the assistant's reply using pyttsx3.

Features

Wake-word listening (“Alpha”) to start a question.
Records audio to input.wav.
Uses Google Web Speech (via SpeechRecognition) to transcribe audio.
Sends transcriptions to Google Gemini (google-generativeai) to generate answers.
Speaks the generated answer using pyttsx3.

Requirements

Python 3.8+ recommended
Microphone and speakers working on your machine
Internet access (for speech recognition and Gemini API)

Python packages:

google-generativeai
pyttsx3
SpeechRecognition
pyaudio


You can install them with:

pip install google-generativeai pyttsx3 SpeechRecognition pyaudio
Important: Installing pyaudio sometimes fails on Windows. If that happens, install a prebuilt wheel appropriate for your Python version (e.g. from [Unofficial Windows Binaries for Python Extension Packages]) or use pipwin:

pip install pipwin
pipwin install pyaudio


On Debian/Ubuntu:
sudo apt-get install portaudio19-dev python3-pyaudio
pip install pyaudio

Secure API Key Handling (DO NOT hard-code keys)

Do not commit your API key into source files. Instead store it in an environment variable and read it in the script.

Example (Linux / macOS):
export GEMINI_API_KEY="YOUR_GOOGLE_GEMINI_API_KEY"


Windows PowerShell:
$env:GEMINI_API_KEY="YOUR_GOOGLE_GEMINI_API_KEY"


In your Python script:

import os
api_key = os.getenv("GEMINI_API_KEY")
if not api_key:
    raise RuntimeError("Set GEMINI_API_KEY environment variable.")
genai.configure(api_key=api_key)

Quick Start

Create a virtual environment (recommended)

python -m venv venv
source venv/bin/activate   # mac/linux
venv\Scripts\activate      # windows
pip install -r requirements.txt


Set your API key in an environment variable (see above).

Run the script:

python your_chatbot_script.py


Speak into your microphone. The script listens for the wake word Alpha. When you say Alpha, it will prompt you to ask your question, transcribe, call Gemini, and speak the response.

Example requirements.txt
google-generativeai
pyttsx3
SpeechRecognition
pyaudio

Example Usage Flow

Terminal prints: Say 'Alpha' to start recording your question...

You say: Alpha

Program prints: Say your Question

You ask: What's the weather like today? (or any question)

Program prints:

You said: What's the weather like today?
Gemini says: [Assistant response]


System speaks the response aloud.



Acknowledgements

google-generativeai — Google Gemini client

SpeechRecognition — audio transcription helpers

pyttsx3 — cross-platform TTS

pyaudio — microphone interface
