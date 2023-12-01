# ansible

Ansible is a configuration management tool which works both on push and pull mechanisms.

### Ansible is very famous and is widely used in the industry and it's quite popular!!! Want to know the PROS's of it it ?

```
    1) Ansible is an agent-less software !!!
    2) Ansible uses SSH as a default mechanism to communicate to other servers (port number : 22 )
    3) The only thing that Ansible Node expects is, communication to other servers that needs CM!
    4) Ansible works both with PUSH & PULL Mechanism. 
    5) Common credentails across the board (Ansible server should be able to ssh to any of the server )
    6) Ansible goes by declarative approach and their documentation is really vast and good
    7) Operations are parallel with Ansible ( Multiple cM's are doable )
    8) Code dones't need to be on the top of a local server !!!

```

### Important Points To Be Notes :

```
    1) Ansible in the backend uses python !!!!
    2) When you install ansible, by default it installs "ansible version2 which is from python2".
    3) Python2 is sunset on Jan 2020.
    4) Lates verison of Ansible or versions of ansible after 2 are python3 based. ( So to install Ansible >2 , you need to have python3 )
    5) By default on all AWS AMI's , you will have python2 by default.

```

### Ansible Documentation Reference : 

```
    https://docs.ansible.com/ansible/latest/index.html
```

Ansible -----> Redhat ----> IBM   ( IBM is a RedHat product now and still it's openSource )


### INVENTORY File

```
 Inventory is nothing but the list of machine ip or dns names that you want ansible to be managed.
```

### How can we operate Ansible  ?

```
Ansible can be operated in 2 ways :
    
    1) Manual Approach       ( You can execute one action at a time )
    2) Automated Approach    ( You can execute multiple actions parallely using Playbook )

```

## Manual Approach

```
    $ ansible -i inv all -e ansible_user=centos  -e ansible_password=DevOps321  -m shell -a uptime

```

### One of the most widely asked interview question,

```
    How to know the list of machines mentioned in the inventory are up or not ?

    $ ansible -i inv all -e ansible_user=centos -e ansible_password=DevOps321 -m ping
```


### What is playbook ?

```
    On a high-level, playbook is an ansible script to execute things parallely 

    A playbook is a list of plays . . . 
    
    A Play is a list of tasks . . . 

    A task is an action that you want to execute!
```

### What is the language used by Playbook ?

```
    YAML is the language used by ANSIBLE to write playbooks.
```

### YAML : Yet Another Markup Lanugated !

```
 YAML is indendation specific
```

### What is a Marupup Languate ? 

```
    Markup Language is a Presentation Languate !!!!

        Ex: html , xml 
```


### YAML is all about 3 ways of representing data that's based on the datatype.

```
    1) Dictionary : a key value pair 
    
            ex: 
                course: devops
                 (key)  (value)

    2) List       : a key wity multiple values

            ex: 
                course: 
                    - devops
                    - aws
                    - gcp
```


### How to run ansible-playbooks ?

```
    $ ansible-playbook -i inv  -e ansible_user=centos  -e ansible_password=DevOps321 playBookName.yaml
```


### When to use quotes for variables in an ansible playbook ?

```
    Ansible supports quotes for Variables!

    When you're just using the variable only, then you don't need to place quotes instead use it directly {{ENV}}

     When you're variables in between the lines ,then ensure you place them in quotes instead use it directly "Name of the environment is {{ENV}}" 


```

Ansible always suggests to organize the files , tasks and variables in a standard format using ROLES. 

    > Roles play a very important role in Ansible

### Role directory structure :

An Ansible role has a defined directory structure with eight main standard directories. You must include at least one of these directories in each role. You can omit any directories the role does not use. For example:

```
    roles/
        frontend/             # this hierarchy represents a "role"
            tasks/            #
                main.yml      #  <-- tasks file can include smaller files if warranted
            handlers/         #
                main.yml      #  <-- handlers file
            templates/        #  <-- files for use with the template resource
                ntp.conf.j2   #  <------- templates end in .j2
            files/            #
                bar.txt       #  <-- files for use with the copy resource
                foo.sh        #  <-- script files for use with the script resource
            vars/             #
                main.yml      #  <-- variables associated with this role
            defaults/         #
                main.yml      #  <-- default lower priority variables for this role
            meta/             #
                main.yml      #  <-- role dependencies

```