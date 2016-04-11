## yamb00 - bman

This Role install Backup Manager by fromdual.com
http://fromdual.com/mysql-backup-manager-mysql_bman

#### Requirements

MySQL Server for Collection Feature

#### Platforms

Currently it's been developed for, and tested on Ubuntu. It is assumed to work on other Debian distributions as well.

#### Role Variables

##### Default Variables

- `brman_tarball` - bman tarball url
- `brman_install_path` - install path
- `brman_symlink` - symlink folder
- `brman_bin_symlink` - symlink in /usr/local/bin

- `php_ini` - location of cli php.ini
- `bman_config_path` - path of config files

- `bman_log_path` - location of logfiles for logrotation
- `bman_log_rotation` - rotation count before being removed

##### Config Files

```yml
bman_config:
  - file:
      name: full.cfg
      policy: daily
      target: root/@127.0.0.1:3306
      type: full
      compress: 9
      backupdir: /srv/backup
      mode: physical
      catalog: root/@127.0.0.1:3306
      instance-name: fullbackup
  - file:
      name: cleanup.cfg
      policy: daily
      type: cleanup
      retention: 7
```
##### Cronjobs

```yml
bman_crons:
  - name: full backup
    config_file: full.cfg
    hour: 2
    minute: 00
  - name: cleanup
    config_file: cleanup.cfg
    hour: 0
    minute: 15
```

### Example Playbook


Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```yml
- hosts: servers
  roles:
     - { role: yamb00.bman }
```
License
-------

BSD
