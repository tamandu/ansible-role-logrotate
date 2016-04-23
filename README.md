# ansible-role-logrotate

This role configures logrotate rules.

## Requirements

None.

## Role Variables

variable       | required | default | choice | comment
-------------- | -------- | ------- | ------ | -------------------
logfile        | yes      |         |        | log file path to rotate, must be defined with list.
option         | no       |         |        | options to rotate, must be defined by list.
firstaction    | no       |         |        | firstaction script, each line of script must be defined by list.
prerotate      | no       |         |        | prerotate script, each line of script must be defined by list.
postrotate     | no       |         |        | postrotate script, each line of script must be defined by list.
lastaction     | no       |         |        | lastaction script, each line of script must be defined by list.

## Dependencies

None.

## Example Playbook

```yml
- hosts: servers
  roles:
    - logrotate
```

*Inside `vars/main.yml`*:  
```yml
logrotate:
  # httpd
  - logfile:
      - /var/log/httpd/*log
    option:
      - daily
      - rotate 30
      - missingok
      - notifempty
      - sharedscripts
      - delaycompress
    postrotate:
      - '/sbin/service httpd reload > /dev/null 2>/dev/null || true'
```

## License

MIT

## Author Information
