# gcloud (Google Cloud CLI)

- `gcloud auth activate-service-account --key-file /path/to/account.json` : Auth with the specified Service Account.
- `gcloud container clusters get-credentials GKE-CLUSTER-NAME --zone us-central1-a --project GCP-PROJECT-ID` : Configure `kubectl` for the `GKE-CLUSTER-NAME` kubernetes GKE cluster, in the specified zone and project.
- `gcloud auth configure-docker` : Auth into Google Container Registry (GCR) for Docker image push/pull (registry).
