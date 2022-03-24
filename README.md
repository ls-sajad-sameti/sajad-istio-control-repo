# Miku control repository
Control repository for git based operations. Argo-CD listens for changes on a control repository to apply manifests which are driving the desired state of the a Miku cluster.

## Structure
```
.
├── Chart.yaml
├── README.md
├── apps
│   └── hello-world
│       └── hello-world-deployment.yaml
├── templates
│   └── hello-world.yaml
└── values.yaml
```

### Chart.yaml
Chart.yaml is boilerplate.

### values.yaml
This file will provide basic values to override when rendering manifests.

### Templates
This directory contains `Application` custom resource definitions for ArgoCD. See [cluster bootstrapping](https://argoproj.github.io/argo-cd/operator-manual/cluster-bootstrapping/)

### Apps
This directory contains sub-directories for each applications. Each sub-directories contains rendered manifest to deploy.

## Usage
Example files are already in the directories for references

### New application
1. Check out the control directory
2. Create a new sub-directory in `app/my-new-app` to host the rendered manifest
3. Push rendered kubernetes manifests in the new directory
4. Push a new `Application` custom resource definition in the `templates` directory to declare a new application in argo-cd
5. Log in argo-cd to sync and deploy the application or let the auto-sync feature deploy the application automatically

### Existing applications
1. Check out the control directory
2. Modify your files to your needs. Update the manifest files.
3. Push modifications back to the repository
4. Log in argo-cd to sync and deploy the application or let the auto-sync feature deploy the application automatically