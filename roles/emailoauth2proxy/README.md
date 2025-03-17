# Overview

## `main.yaml`
Installs and configures the latest release of `email-oauth2-proxy` from the git source.
Configures accounts for the proxy that are in the `emails` var.
This is used as part of backing up e-mails from my legacy Microsoft accounts, so only Hotmail e-mails are configured.
Run via: `python3 ~/software/email-oauth2-proxy/emailproxy.py --no-gui --local-server-auth --config-file ~/software/email-oauth2-proxy/emailproxy.config.local`.
