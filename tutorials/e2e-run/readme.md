# Instructions are from the official cloud deploy documentation
- https://cloud.google.com/deploy/docs/tutorials

# gcloud history
```
git clone https://github.com/cloud-quickstart/cloud-deploy-tutorials.git
cd cloud-deploy-tutorials/
cd tutorials/e2e-run
./setup.sh

gcloud projects \
    add-iam-policy-binding \
    clouddeploy-ol \
    --member=serviceAccount:$(gcloud \
    projects describe \
    clouddeploy-ol \
    --format="value(projectNumber)")-compute@developer.gserviceaccount.com \
    --role="roles/logging.logWriter"
    
    
```
