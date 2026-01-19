# CloudConnexa Network Connector Onboarding Script

This bash script automates the process of launching Network Connectors for CloudConnexa.

## What it does

1. Installs required dependencies (`jq`, `curl`).
2. Installs OpenVPN3 and the connector setup tool if not present.
3. Authenticates with the CloudConnexa API using your credentials.
4. Gets the device's UUID, set this as the Network Name.
5. Creates a new network with a connector.
6. Obtains the connector token and completes the setup.

![](/flowchart.png)

## Prerequisites

- Linux system with `apt` package manager
- `sudo` privileges
- CloudConnexa API Client ID and Secret

## Environment Variables

The script requires the following environment variables:

| Variable | Required | Description |
|----------|----------|-------------|
| `OPENVPN_CLIENT_ID` | Yes | Your CloudConnexa API Client ID |
| `OPENVPN_CLIENT_SECRET` | Yes | Your CloudConnexa API Client Secret |
| `VPNREGION` | No | VPN region ID (default: `us-mia`) |

## Usage

### Option 1: Set environment variables and run

```bash
export OPENVPN_CLIENT_ID='YOUR-CLIENT-ID'
export OPENVPN_CLIENT_SECRET='YOUR-CLIENT-SECRET'
```

Optionally, set a custom VPN region:
```bash
export VPNREGION='us-mia'
```

> **Note:** The default region is `us-mia`. To find available regions, use the [Get Existing Regions](https://openvpn.net/cloud-docs/developer/cloudconnexa-api-v1-0/region/get-existing-regions.html) API endpoint.


Then run the script:
```bash
./connector-onboarding.sh
```

### Option 2: Run directly from GitHub

```bash
sudo wget -qO - https://raw.githubusercontent.com/GabrielPalmar/Simple-CloudConnexa-Onboarding/refs/heads/main/connector-onboarding.sh | bash
```

This will download and execute the script directly from GitHub.

## Notes

- The script includes detailed comments for each step if you need to modify the process