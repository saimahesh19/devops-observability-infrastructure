# Enterprise Observability Platform

A sanitized public portfolio implementation of an enterprise-style Kubernetes observability platform.

> **Disclaimer:** This repository is an independently sanitized/recreated showcase. It contains no production credentials, customer data, internal DNS names, private certificates, proprietary dashboards, or organization-specific identifiers.

## Architecture

```text
                         +----------------------+
                         |   Grafana Enterprise  |
                         +----------+-----------+
                                    |
              +---------------------+----------------------+
              |                     |                      |
              v                     v                      v
        PostgreSQL              Redis HA             Memcached
        (external DB)       (alerting state)        (remote cache)
              |                                            |
              +--------------------+-----------------------+
                                   |
                                   v
                         Grafana Image Renderer

 Application / log sources
            |
            v
         Vector  ---------------------->  ClickHouse / downstream sink

 Metrics / time-series
            |
            v
       VictoriaMetrics Single

 Kubernetes: EKS-style cluster | Helm | HPA | TLS | PVC | ServiceMonitor
```

## Repository layout

```text
enterprise-observability-platform/
├── helm/grafana/values.yaml
├── deployments/
│   ├── grafana-image-renderer/
│   ├── memcached/
│   ├── memcached-exporter/
│   ├── redis/
│   ├── vector/
│   └── vmsingle/
├── kubernetes/
│   ├── namespace.yaml
│   ├── grafana-pvc.yaml
│   ├── grafana-hpa.yaml
│   ├── vector-hpa.yaml
│   ├── grafana-ingress.yaml
│   └── servicemonitor.yaml
├── architecture/
├── docs/
└── README.md
```

## Deployment model

Grafana is represented as a **Helm release** through `helm/grafana/values.yaml`. Supporting workloads are shown as generic Kubernetes Deployments and Services so the repository demonstrates Kubernetes fundamentals without reproducing any production organization's manifests.

## Components

- Grafana Enterprise
- PostgreSQL backend (external dependency)
- Redis for Unified Alerting HA
- Memcached for remote cache
- Memcached exporter
- Grafana Image Renderer
- Vector data pipeline
- VictoriaMetrics Single
- Kubernetes HPA
- TLS/Ingress
- PersistentVolumeClaim
- ServiceMonitor

## Safety

Before using these examples in any environment, replace `example.*` endpoints, secret references, certificates, resource sizes, and image versions with values appropriate for that environment. Do not commit credentials or private keys.
