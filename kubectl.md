# Kubectl (Kubernetes CLI)

Official cheat sheet: https://kubernetes.io/docs/reference/kubectl/cheatsheet/

Config/context:

- `kubectl config get-contexts` : List all configured contexts.
- `kubectl config current-context` : Show the current context (if you use more than one, e.g. one for GKE and one for local `minikube`).

Basics:

- `kubectl get nodes` : Get nodes.
- `kubectl get nodes --output wide` : Get nodes with IP listed.
- `kubectl apply -f kubernetes/` : Create/apply all kubernetes yaml files in the specified directory (or if the path is a file apply only that).
- `kubectl get pods` : Get the list of Pods.

Deployments:

- `kubectl rollout status deployment DEPLOYMENT-NAME` : Check the status of the `DEPLOYMENT-NAME` deployment. If it's still in progress the command will "tail" / keep fetching the status.
- `kubectl rollout history deployment DEPLOYMENT-NAME` : View deployment/rollout history.
- `kubectl rollout history deployment DEPLOYMENT-NAME --revision=1` : View details of a specific revision, e.g. which docker image was used.
- `kubectl rollout undo deployment DEPLOYMENT-NAME` : Rollback with one, to the previous revision.
- `kubectl rollout undo deployment DEPLOYMENT-NAME --to-revision=1` : Rollback to the specified revision.

Ingress:

- `kubectl get ingress INGRESS-OBJECT-NAME` : Check details of the ingress item `INGRESS-OBJECT-NAME`, this includes the IP/ADDRESS of the load balancer.

Secrets:

- `kubectl create secret generic name-of-secret --from-literal=key1=value1 --from-literal=key2=value2`: (https://kubernetes.io/docs/concepts/configuration/secret/#use-case-pods-with-prod-test-credentials)
  - Then you can reference these in a `secretKeyRef` with `name: name-of-secret` and `key: key1` & `key: key2` if you expose these as environment variables (https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables)
