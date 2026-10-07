# Deployment notes

## Grafana

Grafana is represented as a Helm-managed workload. The main configuration is in `helm/grafana/values.yaml`.

## Supporting workloads

The remaining components are intentionally generic Kubernetes manifests:

- `grafana-image-renderer`: renders dashboard panels/images for Grafana.
- `memcached`: provides a lightweight remote cache.
- `memcached-exporter`: exposes Memcached metrics for Prometheus-compatible monitoring.
- `redis`: backing service used by the example Unified Alerting HA configuration.
- `vector`: example data pipeline workload. The sink is deliberately a demo console sink rather than a company-specific destination.
- `vmsingle`: example VictoriaMetrics Single workload.

These manifests demonstrate deployment/service patterns rather than reproducing a production installation.
