# Runbook

## Service

- Name: `docker-workflow-api`
- Team: `Platform Engineering`
- Owner: `mooref068@gmail.com`
- Cost center: `platform-engineering`

## First Checks

```bash
kubectl get rollout docker-workflow-api -n docker-workflow-api-dev
kubectl get pods -l app.kubernetes.io/name=docker-workflow-api -n docker-workflow-api-dev
kubectl logs -l app.kubernetes.io/name=docker-workflow-api -n docker-workflow-api-dev
```

## Health

```bash
curl https://docker-workflow-api.dev.platform.ohanyere.internal/healthz
curl https://docker-workflow-api.dev.platform.ohanyere.internal/readyz
curl https://docker-workflow-api.dev.platform.ohanyere.internal/livez
```

## Rollback

```bash
kubectl argo rollouts undo docker-workflow-api -n docker-workflow-api-dev
```

Escalate to `Platform Engineering` through `mooref068@gmail.com` if rollback does not restore service.
