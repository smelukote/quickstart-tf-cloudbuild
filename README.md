## Configuring your **dev** environment

Just for demostration, this step will:
 1. Configure an apache2 http server on network '**dev**' and subnet '**dev**-subnet-01'
 2. Open port 80 on firewall for this http server 

```bash
cd ../environments/dev
terraform init
terraform plan
terraform apply
terraform destroy
```

## Promoting your environment to **production**

Once you have tested your app (in this example an apache2 http server), you can promote your configuration to prodution. This step will:
 1. Configure an apache2 http server on network '**prod**' and subnet '**prod**-subnet-01'
 2. Open port 80 on firewall for this http server 

```bash
cd ../prod
terraform init
terraform plan
terraform apply
terraform destroy
```

CICD using terraform-cloudbuild-GKE
gcloud config set project [PROJECT_ID]
gcloud services enable container.googleapis.com \
    cloudbuild.googleapis.com \
    sourcerepo.googleapis.com \
    containeranalysis.googleapis.com
gcloud container clusters create hello-cloudbuild \
    --num-nodes 1 --zone us-central1-b
git config --global user.email "[YOUR_EMAIL_ADDRESS]"
git config --global user.name "[YOUR_NAME]"
git config --global credential.helper gcloud.sh -- only if you are using cloud repos.
files needed to test - app.py, Dockerfile for app, cloudbuild.yaml for cloudbuild.
need GKE cluster for deployment - CD
CD - 
IAM permission needed for cloudbuild SA
PROJECT_NUMBER="$(gcloud projects describe ${PROJECT_ID} --format='get(projectNumber)')"
gcloud projects add-iam-policy-binding ${PROJECT_NUMBER} \
    --member=serviceAccount:${PROJECT_NUMBER}@cloudbuild.gserviceaccount.com \
    --role=roles/container.developer
