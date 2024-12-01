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
    * `git checkout -b cotss-${TAG}`
    * `git rebase ${TAG}`
    * `git format-patch ${TAG}..HEAD`
    * Move patches into ebuild
    * `ebuild ${EBUILD} manifest`
  * Test updated ebuild
    * Set-up config
      * `cd /etc`
      * `rm -rf inspircd`
      * `cp -rvp inspircd3 inspircd`
    * Build: `FEATURES="ccache" emerge -av inspircd`
    * Update config `etc-update`
    * Run InspIRCd tests
    * Save config
      * `rm -rf inspircd3`
      * `cp -rvp inspircd inspircd3`
  * Update Gentoo ebuild
    * Add patch to gentoo-distfiles
    * Update ebuild
    * Build
    * Commit: `pkgdev commit`
    * Scan: `pkgcheck scan --commits --net`
    * Push: `GIT_SSH_COMMAND="ssh -o ServerAliveInterval=60" git push github`
  * Submit PR upstream
  * Wait for merge
  * Create calendar item to submit stabilization request in 5 weeks
  * Merge any changes into CotSS ebuild
  * Deploy on CotSS
  * Update MotD

## Stabilize ebuild

  * File a bug on [Gentoo Bugzilla](https://bugs.gentoo.org/)
  * Product: Gentoo Linux
  * Component: Stabilization
  * Summary: net-irc/inspircd-${VERSION}: stabilization request
  * Description: Stabilization request
  * Keywords: CC-ARCHES
  * Submit Bug
  * Package list: =net-irc/inspircd-${VERSION}
  * Save Changes
  * Wait for stabilization
  * Drop old ebuild (if applicable)
