ansible-xtrabackup-role
=========

Ansible role to handle database backups via Percona XtraBackup for Percona MySQL 8 on Debian

Requirements
------------

None

Role Variables
--------------

```YAML
# Enable xtrabackup
percona_xtrabackup_enabled: false

percona_xtrabackup_mysql_version: 8.0

# Packages mode
percona_xtrabackup_packages_mode: latest

##
# Backup config
##
percona_xtrabackup_user: root
percona_xtrabackup_dir: /backup/mysql
percona_xtrabackup_days_to_keep: 2

percona_xtrabackup_binary_log_dir: /var/log/mysql

##
# Default crontab settings
##

# Backups starting at midnight every day
percona_xtrabackup_cron:
  minute: "0"
  hour: "0"
  day: "*"
  month: "*"
  weekday: "*"

# Removal of old backups at 6 AM every day
percona_xtrabackup_cleanup_cron:
  minute: "0"
  hour: "6"
  day: "*"
  month: "*"
  weekday: "*"

# Backup binary logs every 5 minutes
percona_xtrabackup_binlog_backup_cron:
  minute: "*/5"
  hour: "*"
  day: "*"
  month: "*"
  weekday: "*"


```

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: methorz.xtrabackup }

License
-------

BSD

Author Information
------------------

https://twitter.com/methor_z
