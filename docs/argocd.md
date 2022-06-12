# ArgoCD Sample

In the `argocd` directory you can find a number of resources to deploy these resources in this Tekton Catalog to a Kubernetes/OpenShift cluster.

```bash
oc apply -f argocd/
```

This will create a `tekton-catalog` Namespace, a `tekton-catalog` scoped set of ArgoCD resources, which will start to sync to the local cluster.

## RBAC

Sometimes you may need to extend the RBAC rules of the Operator to allow access to the resources you want to use.  Here's a god-mod equivalent of that:

```yaml
---
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  creationTimestamp: null
  name: openshift-gitops-argocd-cluster-admin
  namespace: openshift-gitops
subjects:
  - kind: ServiceAccount
    name: default
    namespace: openshift-gitops
  - kind: ServiceAccount
    name: openshift-gitops-argocd-application-controller
    namespace: openshift-gitops
  - kind: ServiceAccount
    name: openshift-gitops-applicationset-controller
    namespace: openshift-gitops
  - kind: ServiceAccount
    name: openshift-gitops-argocd-dex-server
    namespace: openshift-gitops
  - kind: ServiceAccount
    name: openshift-gitops-argocd-server
    namespace: openshift-gitops
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
```

