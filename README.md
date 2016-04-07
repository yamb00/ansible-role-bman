Role Name
=========

This Role install Backup Manager by fromdual.com

Requirements
------------

MySQL Server for Collection Feature

Role Variables
--------------

Default Variables

brman_tarball: "https://support.fromdual.com/admin/download/fromdual_brman-1.2.2.tar.gz"
brman_install_path: "/usr/local"
brman_symlink: "/usr/local/brman"
brman_bin_symlink: "/usr/local/bin/brman"


percona_repo: "https://repo.percona.com/apt/percona-release_0.1-3.{{ ansible_lsb.codename }}_all.deb"

php_ini: "/etc/php5/cli/php.ini"


Dependencies
------------


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: yamb00.bman }

License
-------

BSD