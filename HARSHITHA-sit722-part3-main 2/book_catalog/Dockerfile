# Use the official slim version of Python as the base image
FROM python:slim-buster

# Set the working directory inside the container to /app
WORKDIR /app

# Copy all the files from the local ./app directory to the working directory inside the container
COPY ./app/. ./

# Copy the requirements.txt file to the working directory
COPY requirements.txt ./

# Install the required Python dependencies listed in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Run the application using uvicorn (ASGI server for FastAPI)
# Expose it to all available interfaces (0.0.0.0) and the port provided via the $PORT environment variable
CMD uvicorn main:app --host 0.0.0.0 --port $PORT
