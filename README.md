<<<<<<< HEAD
# gitops-sample-nodejs

Desired Kubernetes state for [sample-nodejs](https://github.com/eliranbt-commits/sample-nodejs). **Argo CD watches this repo only.**

| Repo | Role |
| --- | --- |
| [sample-nodejs](https://github.com/eliranbt-commits/sample-nodejs) | App source, Dockerfile, GitHub Actions (build / scan / push) |
| **this repo** | Helm chart + image tag. CI commits the new tag; Argo CD syncs |

CI never runs `kubectl apply`. After a green image scan it copies the chart from the app repo and pins `image.tag` in `helm/sample-nodejs/values-gitops.yaml`.

```text
.
└── helm/sample-nodejs/     # chart Argo CD deploys
    ├── Chart.yaml
    ├── values.yaml         # local/kind defaults
    ├── values-gitops.yaml  # Docker Hub repository + tag (CI overwrites)
    └── templates/
```

Argo CD Application (applied from the app repo bootstrap) uses:

- `repoURL: https://github.com/eliranbt-commits/gitops-sample-nodejs`
- `path: helm/sample-nodejs`
- value files: `values.yaml` + `values-gitops.yaml`
=======
# gitops-sample-nodejs
>>>>>>> origin/main
