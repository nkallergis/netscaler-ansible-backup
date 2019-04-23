# netscaler-ansible-backup
## Automatic backup/restore of Citrix NetScalers to/from an SCP server

Most tasks are run through REST API (ansible's _uri_ module). Exporting/importing the file is done via _ssh_citrix_adc_ because no similar API functionality exists currently.

# Usage
## Backup
```ansible-playbook -i <inventory_filename> backup.yml```
- *<inventory_filename>* is the name of the hosts file to be used

**NOTE:** By default, backup files are named following the *YYYYMMDD_HHMMSS_HOSTNAME_full.auto.tgz* pattern.

## Restore
```ansible-playbook -i <inventory_filename> restore.yml -e "bkp_filename=<bkp_filename> ns_target=<ns_target>"```
- *<inventory_filename>*: hosts file to be used
- *<bkp_filename>*: backup file to restore as it exists in the SCP server
- *<ns_target>*: target NetScaler node as it exists in the inventory

**NOTE:** Other values that may be overridden:
- *bkp_user*: user that NetScaler uses to connecto to SCP server
- *bkp_server*: hostname/IP address of the SCP server
- *bkp_server_path*: path in the SCP server where backups are stored (same for all NS nodes)
