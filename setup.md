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
or
```bash
teachme setup.md
```
## Select project to use

<walkthrough-project-setup key="my-project" ></walkthrough-project-setup>

### Add IAM policy binding to Managed cloud group

Run the following command and change the `[project-name]` to your project name or id.

```bash
gcloud projects add-iam-policy-binding {{project-id}} \
    --member group:mce-all@nordcloud.com --role roles/editor
```

### Add Editor role to IAP provisioner service account

Run the following command and change the `[project-name]` to your project name or id.

```bash
gcloud projects add-iam-policy-binding {{project-id}} \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/editor
```

### Add Kubernetes Clust admin to IAP provisioner

Run the following command and change the `[project-name]` to your project name or id.

```bash
gcloud projects add-iam-policy-binding {{project-id}} \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/container.clusterAdmin
```

### Disable compute.requireOsLogin

Run the following gcloud command in cloud shell:

```bash
gcloud compute project-info {{project-id}} add-metadata \
    --metadata enable-oslogin=FALSE
```

### Setup OAuth consent screen

To setup the oauth consent screen that will be used by the Identity Aware Proxy to use a login screen.

Go to the following link and reopen cloud shell and run `teachme oauth.md`:

[Oauth Consent Screen](https://console.cloud.google.com/apis/credentials/consent?project={{project-id}})

## Congratulations

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

You're all set!