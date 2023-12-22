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

## About The model

For the optical character recognition model we used [google cloud vision api](https://cloud.google.com/vision?hl=en) to detect and recognize text inside a handwritten image. The output of this model will be in the form of a digital text which will be used later on semantic similarity model

The semantic similarity model is a finetuned [IndoBERT](https://indolem.github.io/IndoBERT/) model that we retrained on [Indonesian Translated SNLI Corpus](https://github.com/Wikidepia/indonesian_datasets/tree/master/paraphrase/snli). We trained the model for 10 epoch and achieved 0.63743 loss and around 73% accuracy on test set. The final threshold was obtained when we ran the model on the [Indonesian Query Answering Dataset for Online Essay Test System](https://data.mendeley.com/datasets/6gp8m72s9p/1) dataset. The model was tested on the essay with average score above 70.Thus the final threshold for the essay is true are : "entailment" and similarity>=0.60 or “neutral" and Similarity >= 0.70. The similarity threshold for neutral is increased to compensate for model accuracy
