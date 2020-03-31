# Commands

- Basic run command
```ansible-playbook 1-basic-ftp -i inventory/1-base.txt``` 

- Variables can be modified during run with -e
```ansible-playbook playbook.yml -i inventory -e "package=postgres"``` 


### Other Notes
- Facts

Contains discovered info about the host
We can use it for checks when we need to apply some config based on host model/config
Module setup used
```ansible <hostname> -m setup```


