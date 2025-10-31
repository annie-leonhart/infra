# infra

Purpose: infrastructure configuration managed by DevOps for Annie Leonhart project.

Managed here:
- Argo CD (bootstrap/config)
- Envoy Gateway controller and Gateway API resources (dev/staging/prod)
- Prometheus (alerts)
- Grafana (dashboards)

Rules:
- No application source code here.
- No microservice Helm charts here.
- No plaintext secrets. Use the secret workflow in `secrets/README.md`.

Quick start:
1. Install Argo CD (bootstrap manually once or let Argo CD manage itself).
2. Create namespaces: `argocd`, `envoy-gateway`, `monitoring`.
3. In Argo CD, create the applications listed under `argocd-apps/<env>/` or let Argo CD pick them up if you manage Argo CD from Git.
4. Sync `argocd-controller` -> `envoy-controller` -> `gateway-resources` -> monitoring apps.
