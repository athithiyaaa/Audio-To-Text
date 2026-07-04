# Whisper Speech-to-Text

A simple Python project demonstrating two ways to transcribe audio using OpenAI's Whisper library.

## Features

* Automatic speech-to-text transcription
* Automatic language detection
* Manual decoding using Whisper's low-level API

---

## Requirements

* Python 3.9+
* OpenAI Whisper
* PyTorch
* FFmpeg (required for audio processing)

Install the required packages:

```bash
pip install openai-whisper
pip install torch
```

### Install FFmpeg

## Project Structure

```
.
├── Recording.m4a
├── app.py
├── convert.py
└── README.md
```

---

# Method 1 – Direct Audio Transcription

This method automatically detects the language and converts the entire audio into text.

Refer app.py

### How it works

1. Loads the Whisper **base** model.
2. Reads the audio file.
3. Automatically detects the spoken language.
4. Converts speech into text.
5. Prints the transcription.

### Run

```bash
python app.py
```

---

# Method 2 – Language Detection + Manual Decoding

This method exposes Whisper's internal processing steps, including language detection.
Refer convert.py

### How it works

1. Loads the Whisper model.
2. Reads the audio file.
3. Pads or trims the audio to the required length.
4. Converts the audio into a Mel spectrogram.
5. Detects the spoken language.
6. Decodes the speech into text.
7. Prints both the detected language and transcription.

### Run

```bash
python convert.py
```

---

## Sample Output

```
Detected language: en

Hello everyone, welcome to the Whisper speech recognition demonstration.
```

---

## Whisper Model Options

You can replace `"base"` with any available model depending on your speed and accuracy requirements.

| Model  | Speed   | Accuracy |
| ------ | ------- | -------- |
| tiny   | Fastest | Lowest   |
| base   | Fast    | Good     |
| small  | Medium  | Better   |
| medium | Slow    | High     |
| large  | Slowest | Best     |

Example:

```python
model = whisper.load_model("small")
```

---

## Notes

* `fp16=False` is recommended when running on a CPU.
* For GPU users with CUDA support, `fp16=True` can improve performance.
* Ensure `Recording.m4a` is placed in the project directory or provide its full file path.
* Whisper supports many audio formats including `.mp3`, `.wav`, `.m4a`, `.flac`, and `.ogg`.

---

## References

* OpenAI Whisper: https://github.com/openai/whisper
* PyTorch: https://pytorch.org/
* FFmpeg: https://ffmpeg.org/

---

## License

This project is intended for educational and learning purposes.
