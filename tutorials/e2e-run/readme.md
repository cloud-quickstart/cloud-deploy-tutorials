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
    
    
gcloud projects \
    add-iam-policy-binding \
    clouddeploy-ol \
    --member=serviceAccount:$(gcloud \
    projects describe \
    clouddeploy-ol \
    --format="value(projectNumber)")@cloudbuild.gserviceaccount.com \
    --role="roles/logging.logWriter"
    
    
gcloud projects \
    add-iam-policy-binding \
    clouddeploy-ol \
    --member=serviceAccount:$(gcloud \
    projects describe \
    clouddeploy-ol \
    --format="value(projectNumber)")-compute@developer.gserviceaccount.com \
    --role="roles/clouddeploy.jobRunner"

gcloud projects \
    add-iam-policy-binding \
    clouddeploy-ol \
    --member=serviceAccount:$(gcloud projects describe clouddeploy-ol --format="value(projectNumber)")-compute@developer.gserviceaccount.com \
    --role="roles/run.developer"
    
gcloud iam service-accounts \
    add-iam-policy-binding $(gcloud projects describe clouddeploy-ol --format="value(projectNumber)")-compute@developer.gserviceaccount.com \
    --member="serviceAccount:$(gcloud projects describe clouddeploy-ol --format="value(projectNumber)")-compute@developer.gserviceaccount.com" \
    --role="roles/iam.serviceAccountUser"
    
step 3 of 17
    
ERROR: (gcloud.iam.service-accounts.add-iam-policy-binding) Error parsing [service_account].
The [serviceAccount] resource is not properly specified.
Failed to find attribute [project]. The attribute can be set in the following ways:
- set the property `core/project`
- provide the argument `--project` on the command line

checking ok
michael@cloudshell:~/clouddeploy-ol/cloud-deploy-tutorials (clouddeploy-ol)$ gcloud projects describe clouddeploy-ol --format="value(projectNumber)"
205973482280

should be projectId not projectNumber for first gcloud call
gcloud iam service-accounts add-iam-policy-binding $(gcloud projects describe clouddeploy-ol --format="value(projectId)")-compute@developer.gserviceaccount.com --member="serviceAccount:$(gcloud projects describe clouddeploy-ol --format="value(projectNumber)")-compute@developer.gserviceaccount.com" --role="roles/iam.serviceAccountUser"

or
gcloud iam service-accounts add-iam-policy-binding clouddeploy-ol --member="serviceAccount:$(gcloud projects describe clouddeploy-ol --format="value(projectNumber)")-compute@developer.gserviceaccount.com" --role="roles/iam.serviceAccountUser"

export PROJECT_NUMBER=$(gcloud projects describe clouddeploy-ol --format="value(projectNumber)")
gcloud iam service-accounts add-iam-policy-binding clouddeploy-ol --member="serviceAccount:$PROJECT_NUMBER-compute@developer.gserviceaccount.com" --role="roles/iam.serviceAccountUser"

```
<img width="1848" alt="Screenshot 2023-02-09 at 11 07 42" src="https://user-images.githubusercontent.com/24765473/217868879-ef363453-c689-4511-9def-0a5717650db9.png">
to


```

```
