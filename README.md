# Commands

- Basic run command
```ansible-playbook 1-basic-ftp -i inventory/1-base.txt``` 

- Variables can be modified during run with -e
```ansible-playbook playbook.yml -i inventory -e "package=postgres"``` 


### Other Notes
- General
.yml file is a playbook
It can contain multiple plays.
Every play has multiple tasks

- Variables

Create in a dedicated file or in inventory or in play
Reffer to it via "{{ var_name  }}"

- Include

`include` can be used per Task to add external yaml, split to multiple files
`include_vars` include variables to playbook from external JSON or YAML file


- Facts

Contains discovered info about the host
We can use it for checks when we need to apply some config based on host model/config
Module setup used
```ansible <hostname> -m setup```

Custom config/facts can be added by creating file in /etc/ansible/facts.d with .fact extension file
It will be showned as "ansible_local" part

Filtering output for facts can be done by -a 'filter=...'
```ansible <hostname> -m setup -a filter='ansible_kernel'```

Example:
```
[test@localhost ansible-basics]$ ansible localhost -m setup
localhost | SUCCESS => {
    "ansible_facts": {
        "ansible_all_ipv4_addresses": [
            "172.17.0.1", 
            "192.168.18.153", 
            "192.168.18.135", 
            "192.168.18.134", 
            "192.168.122.1"
        ], 
        "ansible_all_ipv6_addresses": [
            "fe80::9862:51e7:7bca:339", 
            "fe80::73d6:c785:dc28:8a18", 
            "fe80::c966:4f17:86d1:e1fa"
        ], 
        "ansible_apparmor": {
            "status": "disabled"
        }, 
        "ansible_architecture": "x86_64", 
        "ansible_bios_date": "07/29/2019", 
        "ansible_bios_version": "6.00", 
        "ansible_cmdline": {
            "BOOT_IMAGE": "/vmlinuz-3.10.0-957.21.3.el7.x86_64", 
            "LANG": "en_US.UTF-8", 
            "quiet": true, 
            "rd.lvm.lv": "centos/swap", 
            "rhgb": true, 
            "ro": true, 
            "root": "/dev/mapper/centos-root"
        }, 
        "ansible_date_time": {
            "date": "2020-03-31", 
            "day": "31", 
            "epoch": "1585645735", 
            "hour": "11", 
            "iso8601": "2020-03-31T09:08:55Z", 
            "iso8601_basic": "20200331T110855474317", 
            "iso8601_basic_short": "20200331T110855", 
            "iso8601_micro": "2020-03-31T09:08:55.474427Z", 
            "minute": "08", 
            "month": "03", 
            "second": "55", 
            "time": "11:08:55", 
            "tz": "CEST", 
            "tz_offset": "+0200", 
            "weekday": "Tuesday", 
            "weekday_number": "2", 
            "weeknumber": "13", 
            "year": "2020"
        }, 
```
