FROM python:3.11-slim

# Set environment variables to ensure logs show up immediately
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Set working directory
WORKDIR /app

# Clean up to keep size small
RUN apt-get update && \
    rm -rf /var/lib/apt/lists/*

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy all files from current directory to /app
COPY . .

# Expose the Flask port
EXPOSE 5000

# Run sync_service in background (&) and app.py in foreground
CMD ["sh", "-c", "python sync_service.py & python app.py"]