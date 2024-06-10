# FROM ubuntu

# WORKDIR /app

# COPY requirements.txt /app
# COPY devops /app

# RUN apt-get update && \
#     apt-get install -y python3 python3-pip && \
#     pip install -r requirements.txt && \
#     cd devops

# ENTRYPOINT ["python3"]
# CMD ["manage.py", "runserver", "0.0.0.0:8000"]


FROM ubuntu:latest

# Install required packages
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3-venv

# Create a working directory
WORKDIR /app

# Copy the requirements file
COPY requirements.txt .

# Create and activate a virtual environment, then install dependencies
RUN python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

# Copy the rest of the application code
COPY . .

# Set the entrypoint to use the virtual environment's Python
ENTRYPOINT ["venv/bin/python"]

# If you have a specific script to run, you can add it here
CMD ["manage.py", "runserver", "0.0.0.0:8000"]






