# 3X UI service for Kubernetes on Wodby

Run 3X UI as a reusable Kubernetes application service with Wodby.

This repository defines the Wodby service manifests and operational
configuration for 3X UI.

- [Browse Wodby services](https://wodby.com/services)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Wodby stacks using this service

- [3X UI application stack](https://github.com/wodby/stack-3xui)

## Service overview

| Property | Manifest configuration |
| --- | --- |
| Service name | `3xui` |
| Type | Application service |
| Versions | `2.8` by default |
| Workloads | `main` (StatefulSet), primary |
| Containers | `3xui` using `ghcr.io/mhsanaei/3x-ui` |
| Endpoints | `panel`: HTTP 2053 |
| Volumes | Data, 1 GB, Certs, 1 GB |
| Helm | chart `oci://registry-1.docker.io/wodby/3xui`; version `0.1.0` |

## Use this service

Use this service through [3X UI application stack](https://github.com/wodby/stack-3xui), or reference `3xui` from a custom
Wodby stack.

A service is a reusable component and does not deploy by itself. The stack
defines its links, settings, versions, resources, and relationship to the rest
of the application.

## Maintain a custom version

1. Fork this repository.
2. Edit the service manifest and referenced files.
3. Import the repository as a [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference the service from a stack manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time.

Validate the manifests with:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/) and the [managed services index](https://github.com/wodby/services).
