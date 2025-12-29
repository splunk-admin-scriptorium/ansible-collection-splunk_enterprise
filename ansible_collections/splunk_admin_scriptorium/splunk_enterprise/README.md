# Ansible Collection - splunk_admin_scriptorium.splunk_enterprise

Collection contains roles for installing and managing and instance of Splunk Enterprise.

Collection Variables
--------------

|Name|Default|Description|
|---|---|---|
|splunk_enterprise_user|splunk|OS user for Splunk|
|splunk_enterprise_group|splunk|OS group for Splunk|
|splunk_enterprise_home|/opt/splunk|Path for installing Splunk (home)|
|splunk_enterprise_service_name|splunkd|Systemd service name for Splunk|
|splunk_enterprise_dbpath|/var/opt/splunk/data/|Path for Splunk data storage (indexes, etc.)|
|splunk_enterprise_backup_user|root|User to own backups created in the process of Splunk install/upgrade|
|splunk_enterprise_backup_group|root|Group to own backups created in the process of Splunk install/upgrade|
|splunk_enterprise_service_limit_memory|8G|Default memory limit for Splunk service|
|splunk_enterprise_service_limit_nofile|64000|NOFILE limit for Splunk service|
|splunk_enterprise_service_limit_nproc|16000|NPROC limit for Splunk service|
|splunk_enterprise_service_limit_fsize|infinity|FSIZE limit for Splunk service|
|splunk_enterprise_service_limit_tasks|2048|TASKS limit for Splunk service|