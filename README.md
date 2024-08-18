# GCP Deployment Github Action

This action allows you to deploy a directory of static files to a Google Cloud Storage bucket.

Example usage:
```yaml
name: Deploying my wonderful website
on:
  push:
    branches: [ main ]
jobs:
  deploy:
      uses: codymikol/gcp-deploy/.github/workflows/gcp_bucket_rsync.yml@v1
      with:
        dist_directory: './public'
      secrets:
        project_id: ${{ secrets.GCP_PROJECT_ID }}
        bucket_name: ${{ secrets.GCP_BUCKET_NAME }}
        credentials_json: ${{ secrets.GCP_SERVICE_ACCOUNT_KEY }}
```

### Secrets

* `project_id` This is your GCP project id, you can find this on the projects page of GCP, each should have a unique id.
* `credentials_json` This is the JSON credentials file that you can download from GCP. This is used to authenticate the deployment.
* `bucket_name` This is the name of the bucket you want to deploy to.

### Inputs

* `dist_directory` This is the directory that you want to deploy to your GCP bucket.
* `before_run` This is a command that will be run before the deployment. This is useful for building your project.
* `after_run` This is a command that will be run after the deployment. This is useful for sending notifications or cleaning up.
