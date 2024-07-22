# Overview
Currently just documentation for InspIRCd.
TODO: Install & configure InspIRCd server.

# Checklists

## Renew server certificate

  * `cd /var/lib/afr/cotss`
  * `afr refresh-service`
  * `cat root/certs/service.pem root/certs/root.pem > certs.pem`

## Upgrade ebuild

  * Read release notes, document needed ebuild changes
  * Update CotSS ebuild
    * `cd ~/inspircd`
    * `git fetch origin`
    * `git checkout cotss`
    * `git rebase ${TAG}`
    * `git format-patch ${TAG}..HEAD`
    * Move patches into ebuild
    * `ebuild ${EBUILD} manifest`
  * Run SSL tests
  * Update Gentoo ebuild
  * Submit PR upstream
    * `GIT_SSH_COMMAND="ssh -o ServerAliveInterval=60"` if push timeouts
  * Create calendar item to submit stabilization request in 5 weeks
  * Merge changes into CotSS ebuild
  * Deploy
  * Update MotD
