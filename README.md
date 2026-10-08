# Fortinet VPN connect
GitHub action to connect to Fortinet VPN

```
name: VPN

on:
  workflow_dispatch:

jobs:
  vpn:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Connect to Fortinet VPN
        uses: mszewcz/fortinet-vpn-connect@1.0.0
        with:
          VPN_HOST: ${{ secrets.VPN_HOST }}
          VPN_PORT: ${{ secrets.VPN_PORT }}
          VPN_USER: ${{ secrets.VPN_USER }}
          VPN_PASSWORD: ${{ secrets.VPN_PASSWORD }}
          VPN_TRUSTED_CERT: ${{ secrets.VPN_TRUSTED_CERT }}

      - name: Do your stuff

      - name: Disconnect VPN
        if: always()
        run: sudo pkill -SIGTERM openfortivpn || true
```
