# Steps to provide access to Nordcloud and prepare GCP project

This is an interactive step-by-step walkthrough to prepare and give Nordcloud access to the GCP project. 

##  Start walkthrough

If you're not seeing the Tutorial in the sidebar use the following Cloud shell command to start the walkthrough:

```
cloudshell launch-tutorial -d setup.md
```

## Give access to the automation tooling of Nordcloud

Run the following three commands and change the `[project-name]` to your project name.

```
gcloud nordcloud add-iam-policy-binding [project-name] \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/editor
```

Add the Kubernetes admin

```
gcloud nordcloud add-iam-policy-binding [project-name] \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/container.clusterAdmin
```

Give our Managed Cloud access

```
gcloud nordcloud add-iam-policy-binding [project-name] \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/editor
```

## Disable compute.requireOsLogin

Run the following gcloud command in cloud shell:

```
gcloud compute project-info add-metadata \
    --metadata enable-oslogin=FALSE
```