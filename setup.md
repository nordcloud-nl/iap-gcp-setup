# Steps to provide access to Nordcloud and prepare GCP project

This is an interactive step-by-step walkthrough to prepare and give Nordcloud access to the GCP project. 

**Time to complete**: About 10 minutes

**Prerequisites**: A GCP account

Click the **Continue** button to move to the next step.

##  Start walkthrough

If you're not seeing the Tutorial in the sidebar use the following Cloud shell command to start the walkthrough:

```bash
cloudshell launch-tutorial -d setup.md
```
## Select project to use

<walkthrough-project-setup></walkthrough-project-setup>

## Give access to the automation tooling of Nordcloud

Run the following three commands and change the `[project-name]` to your project name.

```bash
gcloud nordcloud add-iam-policy-binding [project-name] \
    --member group:mce-all@nordcloud.com --role roles/editor
```

Add the Kubernetes admin

```bash
gcloud nordcloud add-iam-policy-binding [project-name] \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/container.clusterAdmin
```

Give our Managed Cloud access

```bash
gcloud nordcloud add-iam-policy-binding [project-name] \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/editor
```

## Disable compute.requireOsLogin

Run the following gcloud command in cloud shell:

```bash
gcloud compute project-info add-metadata \
    --metadata enable-oslogin=FALSE
```

## Setup OAuth consent screen

To setup the oauth consent screen that will be used by the Identity Aware Proxy to use a login screen.

Go to the following link:

[Oauth Consent Screen](https://console.cloud.google.com/apis/credentials/consent)

## Congratulations

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

You're all set!