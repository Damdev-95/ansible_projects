## Ansible Loops

![image](https://user-images.githubusercontent.com/71001536/166870396-fa1c9f8a-21e8-40bd-8373-3455f1a61446.png)

```
-
    name: 'Print list of fruits'
    hosts: localhost
    vars:
        fruits:
            - Apple
            - Banana
            - Grapes
            - Orange
    tasks:
        -
            command: 'echo "{{ item }}"'
            with_items: '{{ fruits }}'

```

![image](https://user-images.githubusercontent.com/71001536/166871187-a4c77cf4-5573-46ec-8157-620e7fed02e2.png)

```
-
    name: 'Install required packages'
    hosts: localhost
    vars:
        packages:
            - httpd
            - binutils
            - glibc
            - ksh
            - libaio
            - libXext
            - gcc
            - make
            - sysstat
            - unixODBC
            - mongodb
            - nodejs
            - grunt
    tasks:
        -
            yum:
                name: '{{ item }}'
                state: present
            with_items: '{{ packages }}'

```
