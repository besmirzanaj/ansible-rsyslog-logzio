Ansible Role: rsyslog-logzio
=========

An Ansible role to configure a CentOS 7 machine to send logs through rsyslog over TLS to logz.io. 
More documentation on the steps involved is here https://app.logz.io/#/dashboard/data-sources/rsyslog-overTLS.
Target OS is CentOS 7.
TODO: Include more than one file in ```rsyslog_logzio_filepath```

Requirements
------------

No requirements are needed for this role in CentOS 7.

Role Variables
--------------

Main variables to define are described in defaults/main.yml. The easiest way to set your variables is to create a variable file in vars/logzio.yml with this content:

```
$ cat vars/logzio.yml
---
# defaults file for ansible-rsyslog-logzio
rsyslog_logzio_filepath: "FILE_TO_READ_FOR_LOGS"
rsyslog_logzio_type: "LOGZ_IO_TYPE"
rsyslog_logzio_api_token: "YOUR_API_CODE_HERE"
```

Include this variables in the playbook with the vars setting:



Dependencies
------------

No dependencies are needed from this role.

Example Playbook
----------------

This is a simple 

```
- name: apply the logz.io rsyslog forwarder
  hosts:
    - all
  vars_files:
    - ./vars/logzio.yml
  roles:
    - { role: besmirzanaj.ansible_rsyslog_logzio } 
```

License
-------

CC-BY-4.0

Author Information
------------------

This role was created in 2020 by [Besmir Zanaj](https://www.cloudalbania.com).
