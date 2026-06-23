# my-dabs-app-test
## DABs application creation and redeployment test
## Structure

'''text
.
├── databricks.yml
├── resources/app.yml
└── src/app/
    ├── app.py
    ├── app.yaml
    └── requirements.txt
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
'''
