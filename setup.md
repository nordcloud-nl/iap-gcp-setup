# Steps to provide access to Nordcloud and prepare GCP project

## Give access to the automation tooling of Nordcloud

```
echo hello world
```

## Disable compute.requireOsLogin

Run the following gcloud command in cloud shell:

```
gcloud compute project-info add-metadata \
    --metadata enable-oslogin=FALSE
```