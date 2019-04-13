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
- `kubectl rollout status deployment DEPLOYMENT-NAME --watch --timeout=30s` : Run this right after the deployment is started. It'll return with a zero exit code if the deployment finishes with success in the specified `--timeout` time frame, otherwise returns with a non zero exit code.
  - Instead of specifying the `DEPLOYMENT-NAME` you can also use the file definition of the deployment. This only works if there's no other resource in the file! To use this just replace `deployment DEPLOYMENT-NAME` with `-f ./path/to/deployment.yaml`
    - E.g.: `kubectl rollout status -f ./deployment.yaml --watch --timeout=30s`
- `kubectl rollout history deployment DEPLOYMENT-NAME` : View deployment/rollout history.
- `kubectl rollout history deployment DEPLOYMENT-NAME --revision=1` : View details of a specific revision, e.g. which docker image was used.
- `kubectl rollout undo deployment DEPLOYMENT-NAME` : Rollback with one, to the previous revision.
- `kubectl rollout undo deployment DEPLOYMENT-NAME --to-revision=1` : Rollback to the specified revision.

Ingress:

- `kubectl get ingress INGRESS-OBJECT-NAME` : Check details of the ingress item `INGRESS-OBJECT-NAME`, this includes the IP/ADDRESS of the load balancer.

Secrets:

- `kubectl create secret generic name-of-secret --from-file=./key1 --from-file=./key2`: (https://kubernetes.io/docs/concepts/configuration/secret/#use-case-pods-with-prod-test-credentials)
  - **Make sure to delete the secret file after applying!**
  - Then you can reference these in a `secretKeyRef` with `name: name-of-secret` and `key: key1` & `key: key2` if you expose these as environment variables (https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables)
  - It's also possible to pass the secret value directly in the command **but this will expose the secret value in your shell history, so instead use the file option or make sure you delete the secret from your shell history!**
