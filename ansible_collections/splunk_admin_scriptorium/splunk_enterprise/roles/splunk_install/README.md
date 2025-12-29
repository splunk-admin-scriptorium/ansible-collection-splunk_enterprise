splunk_install
=========

Installs and upgrades Splunk Enterprise.
Applies `splunk_apps` and `splunk_service_config` roles.

For upgrade a `splunk_install_version` must be set properly.

Role Variables
--------------

|Name|Collection Var|Default|Description|
|---|---|---|---|
|splunk_install_user|splunk_enterprise_user|splunk|OS user for Splunk|
|splunk_install_group|splunk_enterprise_group|splunk|OS group for Splunk|
|splunk_install_home|splunk_enterprise_home|`/opt/splunk`|Path for installing Splunk (home)|
|splunk_install_service_name|splunk_enterprise_service_name|splunkd|Systemd service name for Splunk|
|splunk_install_dbpath|splunk_enterprise_dbpath|`/var/opt/splunk/data/`|Path for Splunk data storage (indexes, etc.)|
|splunk_install_backup_user|splunk_enterprise_backup_user|root|User to own backups created in the process of Splunk install/upgrade|
|splunk_install_backup_group|splunk_enterprise_backup_group|root|Group to own backups created in the process of Splunk install/upgrade|
|splunk_install_systemd|-|true|Use systemd for Splunk service|
|splunk_install_type|-|tgz|Install from TGZ or RPM|
|splunk_install_package_path|-|`opt/splunk_install/splunk-10.0.2-e2d18b4767e9-linux-amd64.tgz`|Path to Splunk install package on the controller|
|splunk_install_backup_path|-|`/var/opt/splunk/backup/`|OS group for Splunk|
|splunk_install_backup_apps|-|false|Should the role backup applications during install?|
|splunk_install_backup_full|-|false|Should the role make a full Splunk home backup during install?|
|splunk_install_remote_pkg_path|-|`/root/splunk_install_pkg`|Path on remote host where install package wil be stored|
|splunk_install_dirs|-|['splunk_install_dbpath']|Paths to be owned by Splunk after install|
|splunk_install_version|-|-|Target Splunk version|
|splunk_install_bindip|-|-|Set SPLUNK_BINDIP in splunk-launch.conf|
|splunk_install_fips|-|-|Set SPLUNK_FIPS in splunk-launch.conf|
|splunk_install_python_https_verify|-|-|Set PYTHONHTTPSVERIFY in splunk-launch.conf|
|splunk_install_python_utf8|-|-|Set PYTHONUTF8 in splunk-launch.conf|
|splunk_install_python_dont_escape_printable|-|-|Set SPLUNK_PYTHON_DONT_ESCAPE_PRINTABLE in splunk-launch.conf|
|splunk_install_enable_cpushares|-|-|Set ENABLE_CPUSHARES in splunk-launch.conf|

Example Playbook
----------------

```yaml
- name: Splunk Host
  hosts: splunk_test_host
  become: true
  become_method: sudo
  tasks:
    - ansible.builtin.systemd:
        name: "splunkd"
        state: "stopped"
    - include_role:
        name: splunk_admin_scriptorium.splunk_enterprise.splunk_install
    - ansible.builtin.systemd:
        name: "splunkd"
        state: "started"
```

License
-------

AGPLv3