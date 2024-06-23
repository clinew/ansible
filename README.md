## LibreCMC
TODOs:

 * Migrate configuration to Ansible
 * Enable better host key algorithm on router

### Upgrade steps

 1. Check the [release notes](https://gogs.librecmc.org/libreCMC/libreCMC/wiki/Releases)
 1. Download the [latest release](https://gogs.librecmc.org/libreCMC/libreCMC/releases)
 1. Set the following in menuconfig
    * `Subtarget`: `Devices with small flash`
    * `Target Profile`: `TP-Link TL-WR841N/ND v8`
    * Disable IPv6: `Global Build Settings -> Enable IPv6 support in packages` (`CONFIG_IPV6`)
 1. Set the following via `make kernel_menuconfig`
 1. TODO: Fill out rest of this -- got waylaid due to [an issue downloading the kernel on v1.5.15](https://gogs.librecmc.org/libreCMC/libreCMC/issues/190)

### Configuration backup & restore
Adapted from the [OpenWrt Wiki: Backup and restore page](https://openwrt.org/docs/guide-user/troubleshooting/backup_restore#command-line_instructions)

 1. Create backup file: `sysupgrade -b /tmp/backup.tar.gz`
 1. Copy backup file onto another machine (remember `scp`'s `-O` flag)
 1. Update as usual

### Troubleshooting

#### `ash: /usr/libexec/sftp-server: not found`
As per [this OpenWrt Forum post](https://forum.openwrt.org/t/ash-usr-libexec-sftp-server-not-found-when-using-scp/125772) `scp` is trying to use STFP when it needs to use SCP.
Use `-O` when invoking `scp` in order to fix this issue.

### See also

 * [LibreCMC Releases](https://gogs.librecmc.org/libreCMC/libreCMC/releases)
