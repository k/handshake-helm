# Handshake Helm Charts

This is an unofficial registry of [Handshake](https://handshake.org/) [helm](https://helm.sh/) charts.

## Prerequisites
* [Helm](https://helm.sh/) 3+

## Setup

Add the handshake helm repo:
```
helm repo add handshake https://k.github.io/handshake-helm
helm repo update
```

Then configure a values.yaml for the chart you want to install.

## List of Charts

### [HSD](./charts/hsd)

This is a statefulset of [hsd](https://github.com/handshake-org/hsd) to deploy full nodes of hsd to kubernetes.

### [HSD-Zone-Server](./charts/hsd-zone-server)

Basic Zone Server to host DNS records for your handshake domain. Zone server is https://github.com/Black-Wattle/hsd-zone-server

## Deploy to Github Pages

Deploy requires [`cr`](https://github.com/helm/chart-releaser) tool 

### Package chart

```
helm package charts/<chart-to-package> --destination .deploy
```

### Upload New Release

```
cr upload --config config.yaml --token <deploy-token>
```

### Generate new index
```
cr index --config config.yaml
git add index.yaml
git commit -m "Update index.yaml"
git push
```
