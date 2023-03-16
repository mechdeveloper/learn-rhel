```
ansible RHEL001 -m ping -i inventory.ini -e ansible_password='{{ lookup("env","AZURE_USER_PWD")}}'
```

```
ansible-playbook playbook.yml -i inventory.ini -e ansible_password='{{ lookup("env","AZURE_USER_PWD")}}'
```