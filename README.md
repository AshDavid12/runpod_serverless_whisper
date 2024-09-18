# Whisper Streaming Ivrit-AI

This project is built on the **ivrit-ai serverless model** and **Whisper Streaming** for real-time Hebrew transcription using a modified setup. The key change is that the transcription model is wrapped inside the `FasterWhisperASR` class, available in the `whisper_online` module.

## Project Overview

- **Model**: ivrit-ai's Hebrew transcription model.
- **Deployment**: Serverless infrastructure on **Runpod** using a custom Docker image.
- **Customization**: `infer.py` is updated to wrap the transcription model with `FasterWhisperASR` for faster and more efficient streaming transcription.

## Setup and Deployment

1. **Docker Image**: A custom Docker image is built using a **GitHub Actions** workflow. The `Dockerfile` builds and pushes the image to Runpod.
2. **Runpod Deployment**: After building the Docker image, deploy it on Runpod using the following steps:
   - Use the provided `runpod.yaml` template.
   - Adjust container settings, including disk size and worker settings as needed.
   - Deploy the Docker image using: `yairlifshitz/faster-whisper-v2-d4:v1.0`.
   
### Docker Build Steps

1. Clone the repository:
    ```bash
    git clone <repo-url>
    ```
2. Build and push the Docker image using the provided GitHub Actions workflow (`docker-image.yaml`).
3. Deploy the Docker image on Runpod by following the instructions in the `runpod.yaml` template.

## Usage

To start transcription in real-time using the serverless model:
1. Provide audio input via a WAV file or microphone.
2. The transcription will stream in real-time to the client, leveraging the Hebrew transcription model.

