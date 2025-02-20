## Model deployment
[Tutorial](https://cloud.google.com/bigquery-ml/docs/export-model-tutorial)
### Steps

# Authenticate using the service account key:
gcloud auth activate-service-account --key-file=/mnt/c/Users/harry/Desktop/研究所/碩二上/Job/DE/data-engineering-zoomcamp-LCK/Week3/service-account.json 


- gcloud auth login


- bq --project_id kestra-sandbox-450206 extract -m zoomcamp.tip_model gs://harry-kestra-de-zoomcamp-bucket/tip_model

- mkdir /tmp/model

- gsutil cp -r gs://harry-kestra-de-zoomcamp-bucket/tip_model /tmp/model

- mkdir -p serving_dir/tip_model/1

- cp -r /tmp/model/tip_model/* serving_dir/tip_model/1

- docker pull tensorflow/serving

- docker run -p 8501:8501 --mount type=bind,source="/mnt/c/Users/harry/Desktop/研究所/碩二上/Job/DE/data-engineering-zoomcamp-LCK/Week3/serving_dir/tip_model",target=/models/tip_model -e MODEL_NAME=tip_model -t tensorflow/serving &


- curl -d '{"instances": [{"passenger_count":1, "trip_distance":12.2, "PULocationID":"193", "DOLocationID":"264", "payment_type":"3","fare_amount":20.4,"tolls_amount":0.0}]}' -X POST http://localhost:8501/v1/models/tip_model:predict

- http://localhost:8501/v1/models/tip_model