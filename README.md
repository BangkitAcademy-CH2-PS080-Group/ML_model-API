# ML-model-API for Bangkit Capstone Project

## Prerequisite

- Python 3

## Setup

- Clone Repo

```
git clone https://github.com/BangkitAcademy-CH2-PS080-Group/ML_model-API.git
cd ML_model-API
```
  
- Install depedencies

```
pip install -r requirements.txt
```

- Run API

```
uvicorn main:app --port 8000
```

## Deploy to Google Cloud Run

```
docker build -t <API-NAME>:<API-VERSION> .
docker tag <API-NAME>:<API-VERSION> gcr.io/<PROJECT-ID>/<API-NAME>:<API-VERSION> 
docker push gcr.io/<PROJECT-ID>/<API-NAME>:<API-VERSION> 
gcloud run deploy --source .
```

## Endpoint to acces API

- POST /process_image
