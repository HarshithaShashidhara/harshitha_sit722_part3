# Start with the official Python slim-buster image as the base
# The slim-buster variant is smaller, which helps reduce the size of the final image.
FROM python:slim-buster

# Set the working directory inside the container to /app
# All subsequent commands will be run in this directory.
WORKDIR /app

# Copy all files from the local `app` directory into the current directory of the container (i.e., /app)
# This will ensure your application code is available inside the container.
COPY ./app/. ./

# Copy the requirements.txt file to the working directory
# This file contains a list of all the Python dependencies required by your app.
COPY requirements.txt ./

# Install Python dependencies from the requirements.txt file
# The --no-cache-dir flag ensures pip doesn't cache the installation files, reducing image size.
RUN pip install --no-cache-dir -r requirements.txt

# Expose the application on all network interfaces (0.0.0.0) and on the port specified by the $PORT environment variable.
# This enables dynamic port assignment, which is useful when deploying the container to environments like Heroku or Kubernetes.
# Uvicorn is used to run FastAPI or other ASGI-based apps.
CMD uvicorn main:app --host 0.0.0.0 --port $PORT
