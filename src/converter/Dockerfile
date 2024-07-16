# Use the specified base image
FROM python:3.12.2-slim-bullseye

# Update package lists, use a specific mirror, and install necessary packages
RUN sed -i 's|http://deb.debian.org/debian|http://ftp.us.debian.org/debian|' /etc/apt/sources.list \
  && apt-get update \
  && apt-get install -y --no-install-recommends --no-install-suggests \
  build-essential ffmpeg pkg-config \
  || apt-get install -y --no-install-recommends --no-install-suggests --fix-missing \
  build-essential ffmpeg pkg-config \
  && pip install --no-cache-dir --upgrade pip

# Set the working directory
WORKDIR /app

# Copy the requirements file
COPY ./requirements.txt /app

# Install the Python dependencies
RUN pip install --no-cache-dir --requirement /app/requirements.txt

# Copy the rest of the application code
COPY . /app

# Set the default command to run the application
CMD ["python3", "consumer.py"]
