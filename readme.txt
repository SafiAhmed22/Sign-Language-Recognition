Sign Language Recoginition
A real-time sign language recognition system that converts hand gestures in videos/images/webcam to natural language sentences with multilingual audio output.
🔄 Pipeline Overview
Video Input → Hand Detection → Gesture Recognition → Creative Sentence Generation → Audio Output
                   ↓                ↓                      ↓                    ↓
  	       MediaPipe       ML Model           Gemini AI API        English + Chinese
               Landmarks      Predictions        Natural Sentence         TTS Audio
✨ Key Features

Smart Frame Sampling: Processes predictions every 2 seconds to capture meaningful gestures while reducing noise
Creative AI Writing: Uses Google Gemini to transform disconnected sign predictions into natural, grammatically correct sentences
Multilingual Output: Generates audio in both English (Google TTS) and Chinese (Edge TTS)
Real-time Processing: Live hand tracking with confidence scoring and visual feedback

🎯 Core Concept
Frame-per-2-Second Strategy
Instead of processing every frame (which creates noisy predictions), the system:

Collects predictions over 2-second windows
Finds the most common gesture in each window using Counter
Stores only the dominant prediction, creating a clean sequence

Creative Sentence Generation
The pipeline doesn't just output raw predictions like "HELLO, YOU, GOOD, HOW". Instead:

Feeds predictions to Gemini AI with emotional intelligence prompts
Generates natural sentences (8-12 words) that capture the intent behind gestures
Produces grammatically correct output with proper punctuation

🚀 Quick Start
python# Set your paths and API key
VIDEO_PATH = "/path/to/your/video.MOV"
GEMINI_API_KEY = "your-gemini-api-key"

# Run the pipeline
python main.py
📊 Output Files

output_video.MOV - Processed video with gesture annotations
prediction_from_video.csv - Clean predictions (every 2 seconds)
sentence_en.mp3 - Generated sentence in English
sentence_zh.mp3 - Generated sentence in Chinese
generated_sentences.txt - Final text output

💡 How It Works

Load Models: Pre-trained gesture recognition model + MediaPipe hands
Process Video: Extract hand landmarks, predict gestures with confidence filtering (≥80%)
Smart Sampling: Store dominant prediction every 2 seconds
AI Generation: Transform predictions into natural language using Gemini
Audio Creation: Generate bilingual TTS audio files