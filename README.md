# rkhunter

[![Build Status](https://travis-ci.org/maxlareo/ansible-rkhunter.svg?branch=master)](https://travis-ci.org/maxlareo/ansible-rkhunter) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-rkhunter-blue.svg)](https://galaxy.ansible.com/maxlareo/rkhunter/)

Install and configure Rootkit Hunter in Debian-like systems

## Requirements

None

## Role Variables

### About the `/etc/default/rkhunter` file

- `rkhunter_cron_daily_run`: [default: `'true'`]: Set this to yes to enable rkhunter daily runs
- `rkhunter_cron_db_update`: [default: `'true'`]: Set this to yes to enable rkhunter weekly database updates
- `rkhunter_db_update_email`: [default: `'false'`]: Set this to yes to enable reports of weekly database updates
- `rkhunter_report_email`: [default: `root`]: Set this to the email address where reports and run output should be sent
- `rkhunter_apt_autogen`: [default: `'false'`]: Set this to yes to enable automatic database updates
- `rkhunter_nice`: [default: `0`]: Nicenesses range from -20 (most favorable scheduling) to 19 (least favorable)
- `rkhunter_run_check_on_battery`: [default: `'false'`]: Should daily check be run when running on battery, powermgmt-base is required to detect if running on battery or on AC power

### About the `/etc/rkhunter.conf` file

- `rkhunter_rotate_mirrors`: [default: `1`]: `1` to rotate between mirrors, `0` to treat the mirrors list as priority list, use first, if fail use next, etc
- `rkhunter_update_mirrors`: [default: `1`]: `1` to update mirrors list when update, `0` to not update mirrors list
- `rkhunter_mirrors_mode`: [default: `0`]: `0`  to use any mirror, `1` to only use local mirrors, `2` to only use remote mirrors
- `rkhunter_mail_on_warning`: [default: `root@localhost`]: Email a message to this address if a warning is found
- `rkhunter_mail_cmd`: [default: `'mail -s "[rkhunter] Warnings found for ${HOST_NAME}"'`]: The mail command to use if MAIL-ON-WARNING is set
- `rkhunter_bindir`: [default: `"{{ ansible_env.PATH | replace(':',' ')}}"`]: Used to modify the command directory list used by rkhunter to locate commands (that is, its PATH)
- `rkhunter_language`: [default: `en`]: The default language to use
- `rkhunter_logfile`: [default: `/var/log/rkhunter.log`]: The log file pathname
- `rkhunter_append_log`: [default: `0`]: `0` will cause a new log file to be created, `1` the log file is to be appended
- `rkhunter_copy_log_on_error`: [default: `0`]: `0` the log file will not be copied, `1` the log file is to be copied
- `rkhunter_use_syslog`: [default: `NONE`]: Enable the rkhunter check start and finish times to be logged by syslog. Warning messages will also be logged. The value of the option must be a standard syslog facility and priority, separated by a dot
- `rkhunter_allow_ssh_root_user`: [default: `'no'`]: Checked against the SSH configuration file 'PermitRootLogin' option, a warning will be displayed if they do not match
- `rkhunter_enable_tests`: [default: `ALL`]: Determine which tests are to be performed
- `rkhunter_disable_tests`: [default: `suspscan hidden_ports hidden_procs deleted_files packet_cap_apps apps`]: The list of disabled tests is applied to the list of enabled tests
- `rkhunter_hash_cmd`: [default: `SHA256`]: Specify the command to use for the file properties hash value check
- `rkhunter_pkgmgr`: [default: `NONE`]: Tells rkhunter to use the specified package manager to obtain the file property information
- `rkhunter_existwhitelist`: [default: `[]`]: Whitelists files and directories from existing, or not existing
- `rkhunter_attrwhitelist`: [default: `[]`]: Whitelist various attributes of the specified files
- `rkhunter_writewhitelist`: [default: `[]`]: Allow the specified files to have the 'others' (world) permission have the write-bit set
- `rkhunter_scriptwhitelist`: [default: `[]`]: Allow the specified files to be a script
- `rkhunter_immutwhitelist`: [default: `[]`]: Allow the specified file to have the immutable attribute set
- `rkhunter_allowhiddendir`: [default: `[]`]: Allow the specified hidden directory to be whitelisted
- `rkhunter_allowhiddenfile`: [default: `[]`]: Allow the specified hidden file to be whitelisted
- `rkhunter_allowprocdelfile`: [default: `''`]: Allow the specified process to use deleted files. The process name may be followed by a colon-separated list of full pathnames (which have been deleted)
- `rkhunter_allowproclisten`: [default: `[]`]: Allow the specified process to listen on any network interface
- `rkhunter_port_whitelist`: [default: `[]`]: Whitelist network ports, space-separated list of one or more of two types of whitelisting, a 'protocol:port' pair and an asterisk ('*')
- `rkhunter_port_path_whitelist`: [default: `[]`]: Whitelist network ports, specifies one of two types of whitelisting, a pathname to an executable and a combined pathname, protocol and port

## Dependencies

None

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - rkhunter
```

## License

MIT

## Author Information

[Maxime Lareo](https://github.com/maxlareo)

## Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/maxlareo/ansible-rkhunter/issues)! 
