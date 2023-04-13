# Linode DNS Configuration

- Purchase Domain name
- Configure Domain name to point to Linode DNS servers (ns1-ns5.linode.com)
- Generate Linode API token with Domain Access
- Deploy ExternalDNS


## External DNS

- Set Linode API token

```LINODE_API_TOKEN=....```

- Using Helm, add bitnami repo

```helm repo add bitnami https://charts.bitnami.com/bitnami```

- Install External DNS with Helm

```
helm upgrade --install external-dns bitnami/external-dns \
  --namespace external-dns --create-namespace \
  --set provider=linode \
  --set linode.apiToken=$LINODE_API_TOKEN
```

### Service binding

- Annotate service (Nginx as example) to expose it with a DNS record

```
kubectl annotate service web \
  external-dns.alpha.kubernetes.io/hostname=nginx.example.com
```