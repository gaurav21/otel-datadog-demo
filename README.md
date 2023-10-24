# OpenTelemetry Demo Helm Chart

This helm chart installs the [OpenTelemetry Demo](https://github.com/open-telemetry/opentelemetry-demo)
in a kubernetes cluster and sends telemetry data to Datadog Backend using either ingest mode (datadog agent) or
exporter mode (otel collector + datadog exporter).

## Prerequisites

- Helm 3.0+

## Installing the Chart

Clone the chart:

```console
git clone git@github.com:DataDog/opentelemetry-helm-charts.git
cd opentelemetry-helm-charts/opentelemetry-demo-datadogv2
```

Create a secret with your datadog api key (alternatively you may update the secret in
agent-ingest.yaml/collector-exporter.yaml or --set it when installing):
```console
kubectl create secret generic datadog-secrets --from-literal api-key=<YOUR_KEY_HERE>
```

To install the chart with the release name my-otel-demo using ingest mode, run the following command:
```console
helm install my-otel-demo --values ./agent-ingest.yaml .
```

Alternatively, you may run the following command to install the chart using exporter mode:
```
helm install my-otel-demo --values ./collector-exporter.yaml .
```
# otel-datadog-demo
