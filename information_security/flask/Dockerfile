# Base image is Python 3.9
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt requirements.txt

# Install the required packages
RUN apt-get update -qq && apt-get install libgomp1
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Copy the model and application code into the container
COPY ["lgb_model.pkl", "main.py", "./"] .

# Run the app using gunicorn
ENTRYPOINT ["gunicorn", "--bind=0.0.0.0:8989", "main:app"]
