# Tekton Asset Catalog

## ClusterTasks

- [buildah-package](tasks/buildah-package/) - Use buildah to pull/mount/tar a container image
- [upload-to-artifactory](tasks/upload-to-artifactory) - Upload a file to Artifactory as an Artifact

## Deploy & Sync with ArgoCD

You can sync this Tekton Catalog with ArgoCD by running the following command:

```bash
oc apply -n openshift-gitops -f argocd/
```

Or if using ArgoCD in a different namespace, such as `argocd`:

```bash
oc apply -n argocd -f argocd/
```
