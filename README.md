# GPT-2 FastAPI Docker Hub

A lightweight FastAPI application that loads a GPT-2 model and exposes a text generation API. The project is containerized with Docker and automatically published to Docker Hub through GitHub Actions.

[![Build & Push to Docker Hub](https://github.com/Muhammadyousafrana/huggingfae-DockerHub-acr/actions/workflows/main.yml/badge.svg)](https://github.com/Muhammadyousafrana/huggingfae-DockerHub-acr/actions/workflows/main.yml)

## Overview

This repository demonstrates how to:

- create a Python FastAPI service
- integrate a GPT-2 model using Hugging Face `transformers`
- package the app in a Docker container
- build and push the container image to Docker Hub with GitHub Actions

## Features

- FastAPI app with a root endpoint and text generation endpoint
- GPT-2 text generation via Hugging Face pipeline
- Dockerized deployment
- CI/CD automation for Docker Hub publishing

## Project Structure

```text
.
├── .github/
│   └── workflows/
│       └── main.yml
├── Dockerfile
├── LICENSE
├── README.md
├── main.py
├── requirements.txt
└── .gitignore
```

## Requirements

- Python 3.10+
- pip
- Docker (optional, for containerized usage)

## Local Setup

1. Clone the repository:

```bash
git clone https://github.com/Muhammadyousafrana/huggingfae-DockerHub-acr.git
cd huggingfae-DockerHub-acr
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# .venv\Scripts\activate  # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Start the FastAPI app:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

5. Open the Swagger UI:

```text
http://localhost:8000/docs
```

## API Endpoints

### GET /

Returns a welcome message.

### POST /generate

Generates text based on the input body.

Example request:

```bash
curl -X POST "http://localhost:8000/generate" \
  -H "Content-Type: application/json" \
  -d '{"text": "Once upon a time"}'
```

Example response:

```json
{
  "generated_text": "Once upon a time, there was a young developer who built a Docker image..."
}
```

## Docker Usage

Build the image:

```bash
docker build -t your-dockerhub-username/gpt2-fastapi-dockerhub:latest .
```

Run the container:

```bash
docker run -p 8000:8000 your-dockerhub-username/gpt2-fastapi-dockerhub:latest
```

Then open:

```text
http://localhost:8000/docs
```

## GitHub Actions for Docker Hub

This repository includes a workflow in `.github/workflows/main.yml` that:

- checks out the code
- sets up Docker Buildx
- logs in to Docker Hub using GitHub secrets
- builds the Docker image
- pushes the image to Docker Hub

Required GitHub secrets:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

## Recommended Repository Name

The current name is functional, but the most appropriate and cleaner name for this project would be:

```text
gpt2-fastapi-dockerhub
```

This name is more descriptive, professional, and aligned with the actual purpose of the project.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
