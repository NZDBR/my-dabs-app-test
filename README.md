# my-dabs-app-test
## DABs application creation and redeployment test
## Structure

```text
.
├── databricks.yml
├── resources/app.yml
└── src/app/
    ├── app.py
    ├── app.yaml
    └── requirements.txt


databricks.yml - bundle deployment configuration file at the root of the bundle directory,
                 entry point for databricks bundle validate, deploy etc commands

resources/app.yml - optional bundle resource file to keep the bundle configuration modular, read by DABs
                 defines the Databricks App resource; it becomes useful when bundle contains multiple resources:
                 job.yml, pipeline.yml, warehouse.yml

src/app/app.yaml - defines App runtime configuration, and application environment variables 

Deploy
databricks bundle validate --target dev
databricks bundle deploy --target dev
databricks bundle run my_test_app --target dev
If the App was created manually before DABs deployment, bind it first:

databricks bundle deployment bind \
  my_test_app \
  <APP_NAME> \
  --target dev \
  --auto-approve
Redeploy
Update the code, commit and push it, then run:

databricks bundle deploy --target dev
databricks bundle run my_test_app --target dev
The same App should be updated without creating a duplicate or returning an App already exists error.
```
