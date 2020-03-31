# Commands

- Basic run command
```ansible-playbook 1-basic-ftp -i inventory/1-base.txt``` 

- Variables can be modified during run with -e
```ansible-playbook playbook.yml -i inventory -e "package=postgres"``` 

