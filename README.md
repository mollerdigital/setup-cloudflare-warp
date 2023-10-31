# setup-cloudflare-warp
[![Cloud-Team](https://img.shields.io/badge/CloudTeam-black.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/orgs/mollerdigital/teams/cloud-team) <br />
This action sets up Cloudflare Warp and allows the workflow to connect to Møller private resources in both Azure and On-Premise.

## Pre-requisites
This action currently only supports Linux and macOS. Your repository must also have the option `enable_cloudflare_warp` set to `true`. See Cloud-Applications for more information.

Example:
```yaml
uses: mollerdigital/setup-cloudflare-warp@v1.0.0
with:
  organization: moller
  auth_client_id: ${{ secrets.CLOUDFLARE_AUTH_CLIENT_ID }}
  auth_client_secret: ${{ secrets.CLOUDFLARE_AUTH_CLIENT_SECRET }}
```
You can specify the version of Cloudflare WARP to install:
```yaml
uses: mollerdigital/setup-cloudflare-warp@v1.0.0
with:
  version: 2023.1.133
  organization: moller
  auth_client_id: ${{ secrets.CLOUDFLARE_AUTH_CLIENT_ID }}
  auth_client_secret: ${{ secrets.CLOUDFLARE_AUTH_CLIENT_SECRET }}
```

## Inputs
- `version` - (optional) The version of Cloudflare WARP to install. Defaults to the latest version.
- `organization` - (required) The name of your Cloudflare Zero Trust organization.
- `auth_client_id` - (required) The service token client id.
- `auth_client_secret` - (required) The service token client secret.

## Troubleshooting
- Unable to connect: `Status update: Unable to connect. Reason: Registration Missing` errors
  - Check that the service token is valid and not expired.
  - Check that the service token has the appropriate permissions to connect.
  - Cancel and restart the job, sometimes there's an issue on Cloudflare's end that causes this error.

## Disclaimer
This is not an official Cloudflare product nor is it endorsed by Cloudflare. This project is a fork from the `Boostport/setup-cloudflare-warp`.
Most code is identical in this repository besides from the examples and some Møller specific setup that is required for this to work
in our tenant and setup.