RHVoice Docker

This repository contains the Docker setup for RHVoice, a speech synthesis system.

Prerequisites

- Docker installed on your system

Getting Started

Clone the Repository

First, clone the repository to your local machine:

git clone https://github.com/abdulazizsalimov/rhvoice-docker.git
cd rhvoice-docker

Build the Docker Image

Build the Docker image using the provided Dockerfile:

docker build -t rhvoice .

Run the Docker Container

Run the Docker container, mapping the internal port 8080 to an external port (8080 in this example):

docker run -it --rm -p 8080:8080 rhvoice

Test the Service

Open your browser and navigate to the following URL to test the service:

http://localhost:8080/say?text=Hello%20World&voice=dilnavoz&format=mp3

API Endpoints

/say

Description

Synthesizes speech from text.

Parameters

- text (required): The text to be synthesized.
- voice (optional): The voice to use for synthesis. Default is dilnavoz.
- format (optional): The format of the output audio file. Supported formats are wav, mp3, opus, flac. Default is mp3.
- rate (optional): The speed of the speech synthesis (0-100).
- pitch (optional): The pitch of the speech synthesis (0-100).
- volume (optional): The volume of the speech synthesis (0-100).

Example

http://localhost:8080/say?text=Hello%20World&voice=dilnavoz&format=mp3&rate=50&pitch=50&volume=50

/rhasspy (POST)

Description

Accepts raw text data for synthesis, primarily intended for use with the Rhasspy voice assistant.

Parameters

- text (required): The text to be synthesized.

Example

curl -X POST -d "Hello World" http://localhost:8080/rhasspy

Environment Variables

- CHUNKED_TRANSFER: Enable chunked transfer encoding if set.

Configuration

Configuration settings can be adjusted in the app.py file if necessary. The service is set to run on port 8080 by default.

Contributing

Feel free to open issues or submit pull requests for any improvements or bug fixes.
