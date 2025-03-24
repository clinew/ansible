# Overview

## `main.yaml`
Configures automatic backups of my e-mail.
Pulls in a custom package, `isync-backup`, that does most of the set-up, then finalizes the set-up by adding the credentials.

## `hotmail.yaml`
Configures backing up my legacy Microsoft accounts.
This is a manual process that will be done during the migration period.
Requires `email-oauth2-proxy` in order to connect to the remote server.
