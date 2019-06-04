ansible-xtrabackup-role
=========

Ansible role to handle database backups via xtrabackup.

Requirements
------------

None

Role Variables
--------------

```YAML
# Enable xtrabackuo
percona_xtrabackup_enabled: false

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
# Set up cron jobs for backup, cleanup and binlog rsync
##

# Create xtrabackup cron job
percona_xtrabackup_cron:
  minute: "0"
  hour: "4"
  day: "*"
  month: "*"
  weekday: "*"

# Create cleanup for backups cron job
percona_xtrabackup_cleanup_cron:
  minute: "0"
  hour: "6"
  day: "*"
  month: "*"
  weekday: "*"

# Create binlog rsync backup
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