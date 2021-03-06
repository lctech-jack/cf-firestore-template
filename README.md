# cf-firestore-template

## Architecture
Please follow the below format to name custom cloud functions.
```
.
├── README.md
├── .env.yaml
├── .gcloudignore
├── cmd
│   └── main.go
├── deploy.sh
├── init.go
├── cf_{funcName}_{trigger}.go
├── cf_{funcName}_{trigger}_{option}.go
├── cf_{funcName}_{trigger}_test.go
├── ...
├── go.mod
├── go.sum
└── vendor
```

## Quick Start

## Deployment
- How to customize
  - Modify ```custom_func_name```,```projectid```,```entry_point```
  - Modify and select firestore trigger ```{create_trigger | update_trigger | delete_trigger | write_trigger}```
  - Modify ```doc_path``` or customize other path
```shell
gcloud functions deploy ${runmode}-{custom_func_name} \
  --project="${projectid}" \
  --region=asia-east1\
  --service-account firebase-adminsdk-dyqdv@lcwp-jack.iam.gserviceaccount.com \
  --entry-point {entry_point} \
  --runtime go116 \
  --trigger-event ${delete_trigger} \
  --trigger-resource "projects/${projectid}/databases/(default)/documents/{doc_path}" \
  --allow-unauthenticated \
  --memory 128
```
- Local deploy
```shell
sh ./deploy.sh
```
