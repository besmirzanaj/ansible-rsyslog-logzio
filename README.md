Ansible Role: rsyslog-logzio
=========

An Ansible role to configure a CentOS 7 machine to send logs through rsyslog over TLS to logz.io. 
More documentation on the steps involved is here https://app.logz.io/#/dashboard/data-sources/rsyslog-overTLS.

TODO: Include more than one file to be sent in logz.io in the variable ```rsyslog_logzio_filepath```.

Requirements
------------

Selinux default configuration does not allow for rsyslog to forward meesages to a remote host. Adopt selinux policies or set it to ```permissive``` for this role to work in CentOS 7.

Role Variables
--------------

Main variables to define are described in defaults/main.yml. The easiest way to set your variables is to create a variable file in vars/logzio.yml with this content:

To get the API token use the Token variable from the [General Setting](https://app.logz.io/#/dashboard/settings/general) site in Logz.io.

To get an idea on the logz.io types see [here](https://support.logz.io/hc/en-us/articles/210205985-Which-log-types-are-preconfigured-on-the-Logz-io-platform-). 
 

```
$ cat vars/logzio.yml
---
# defaults file for ansible-rsyslog-logzio
rsyslog_logzio_filepath: "FILE_TO_READ_FOR_LOGS"
rsyslog_logzio_type: "LOGZ_IO_TYPE"
rsyslog_logzio_api_token: "YOUR_API_CODE_HERE"
```

Include these variables in the playbook with the vars setting in the role. See below an example. Role will not work without these variables


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
