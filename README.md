# CheckUp AI

This is a small AI healthcare assistant I built that takes a patient's spoken symptoms along with a photo of the affected area, and gives back preliminary medical guidance — also spoken back to the user.

The idea was to explore how multimodal LLMs (text + image + voice) could be used in a healthcare assistant style application.

# How it works

1. User describes their symptoms by speaking into the mic
2. The audio gets transcribed to text using Groq's Whisper model
3. The transcribed text + an uploaded medical image are sent to LLaMA-4 Scout Vision (via Groq API)
4. The model analyzes both and generates a response with possible guidance
5. That response is converted back into speech using gTTS / ElevenLabs
6. Everything runs through a simple Gradio interface

# Tech used

 - Python
- Groq API for running the LLM
- LLaMA-4 Scout Vision (Meta) — handles both image and text understanding
- Whisper for speech-to-text
- gTTS and ElevenLabs for text-to-speech
- Gradio for the UI

# Files

- `brain_of_the_doctor.py` — handles the image encoding and sends the query + image to the LLM
- `voice_of_the_patient.py` — records the patient's voice and converts it to text
- `voice_of_the_doctor.py` — converts the AI's response back into speech
- `gradio_app.py` — connects everything into one working app with a UI

# Running it

Install the dependencies:

pip install -r requirements.txt

Add your API keys in a `.env` file:

GROQ_API_KEY=your_key_here
ELEVEN_API_KEY=your_key_here

Then run:

python gradio_app.py

## Note

This was built as a learning project. It's not meant to replace an actual doctor — just an experiment in combining voice, vision, and LLMs into one assistant.




