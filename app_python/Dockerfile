# Use an official Python runtime as a parent image
FROM python:3.9-slim

WORKDIR /app_python

# Copy necessary files
COPY requirements.txt app.py /app_python/
COPY templates/ /app_python/templates/

RUN adduser -D myuser
RUN mkdir /app/app_python /app/visits && chown -R myuser /app/app_python /app/visits


RUN pip3 install --no-cache-dir -r requirements.txt

USER myuser

EXPOSE 5000

# Run app.py when the container launches
CMD ["python3", "app.py"]