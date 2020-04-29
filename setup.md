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

## Add IAM policy binding to Managed cloud group

The command will setup up the GCP project for Nordcloud
- Add Editor role to IAP provisioner service account
- Add Kubernetes Admin to IAP provisioner
- Add IAM policy binding to Managed cloud group

Run the following command:

```bash
gcloud projects add-iam-policy-binding {{project-id}} \
    --member group:mce-all@nordcloud.com --role roles/editor && \
gcloud projects add-iam-policy-binding {{project-id}} \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/editor && \
gcloud projects add-iam-policy-binding {{project-id}} \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/resourcemanager.projectIamAdmin && \
gcloud projects add-iam-policy-binding {{project-id}} \
    --member serviceAccount:provisioner-org@iap-service-508592859782.iam.gserviceaccount.com --role roles/container.clusterAdmin
```

### Disable compute.requireOsLogin (OPTIONAL)

Run the following gcloud command in cloud shell:

```bash
gcloud beta resource-manager org-policies disable-enforce --project {{project-id}} constraints/compute.requireOsLogin
```

### Setup OAuth consent screen 

To setup the oauth consent screen that will be used by the Identity Aware Proxy to use a login screen.

Go to the following link and reopen cloud shell and run `teachme oauth.md`:

[Oauth Consent Screen](https://console.cloud.google.com/apis/credentials/consent?project={{project-id}}&cloudshell=true&cloudshell_tutorial=oauth.md&cloudshell_git_repo=https://github.com/nordcloud-nl/iap-gcp-setup.git)

## Congratulations

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

You're all set!