# GCP Deployment Github Action

This action allows you to deploy a directory of static files to a Google Cloud Storage bucket.

Example usage:
```yaml
name: Deploy my super cool project
  jobs:
    deploy:
      runs-on: ubuntu-latest
      steps:
        - uses: codymikol/gcp-deploy@v1
          with:
            before_run: 'npm run build'
            dist_directory: './dist'
            after-run: 'echo "I'd send an email to let you know the build is done, but an echo will have to do ;o"'
            project_id: ${{ secrets.GCP_PROJECT_ID }}
            credentials_json: ${{ secrets.GCP_CREDENTIALS }}
            bucket_name: ${{ secrets.GCP_BUCKET_NAME }}
```

### Secrets

* `project_id` This is your GCP project id, you can find this on the projects page of GCP, each should have a unique id.
* `credentials_json` This is the JSON credentials file that you can download from GCP. This is used to authenticate the deployment.
* `bucket_name` This is the name of the bucket you want to deploy to.

### Inputs

* `dist_directory` This is the directory that you want to deploy to your GCP bucket.
* `before_run` This is a command that will be run before the deployment. This is useful for building your project.
* `after_run` This is a command that will be run after the deployment. This is useful for sending notifications or cleaning up.
