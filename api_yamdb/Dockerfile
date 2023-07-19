FROM python:3.7-slim AS builder
WORKDIR /app
COPY api_yamdb/requirements.txt .
RUN pip3 install -r requirements.txt --no-cache-dir
FROM python:3.7-slim
WORKDIR /app
COPY . .
CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000"]