# 3X UI on Wodby

What Wodby sets up for 3X UI on this service. It runs the upstream `ghcr.io/mhsanaei/3x-ui` image.

- The panel listens on port 2053, the only endpoint of the service. Ports of inbounds created in the panel are not exposed by the manifest.
- The `data` volume is mounted at `/etc/x-ui`, where the panel keeps its database with users, panel settings and inbounds. The `certs` volume is mounted at `/root/cert`.
- On the first start with an empty database the panel creates its default administrator account. The manifest generates no credentials: change the account in the panel.
- Panel settings, including the panel port and path, are stored in the database and changed in the panel, not through environment variables. Keep the panel port at 2053, since the endpoint and the health checks use it.
- The container gets `XUI_ENABLE_FAIL2BAN` and `XRAY_VMESS_AEAD_FORCED` from the Helm chart. Other variables are added on the service and applied by a deployment.
- The manifest declares no links, settings, backups, imports or actions.
