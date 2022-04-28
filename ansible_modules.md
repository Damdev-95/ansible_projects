## Ansible Modules

![image](https://user-images.githubusercontent.com/71001536/165847594-4c63cdef-da23-469e-9723-294ae4eb8589.png)

```
-
    name: 'Execute script on web servers'
    hosts: web_nodes
    tasks:
        - 
            name: 'execute script'
            script: /tmp/install_script.sh
            
```
![image](https://user-images.githubusercontent.com/71001536/165848579-dd31a8fa-04ce-4da1-921e-dd6d5acdc3d4.png)

```
-
    name: 'Execute a script on all web server nodes'
    hosts: web_nodes
    tasks:
        -
            name: 'Execute a script on all web server nodes'
            script: /tmp/install_script.sh
        
        -
            name: 'Start httpd services'
            service:
                name: httpd
                state: started
```

![image](https://user-images.githubusercontent.com/71001536/165849150-afa0a33f-77a9-4195-a976-aca44d08e6f7.png)

```
-
    name: 'Execute a script on all web server nodes'
    hosts: web_nodes
    tasks:
        -
            lineinfile:
                path: /etc/resolv.conf
                line: 'nameserver 10.1.250.10'  
        -
            name: 'Execute a script'
            script: /tmp/install_script.sh
        -
            name: 'Start httpd service'
            service:
                name: httpd
                state: present
```


![image](https://user-images.githubusercontent.com/71001536/165850046-8bedb4b0-3a65-4621-96a0-dda479b9b685.png)


```
-
    name: 'Execute a script on all web server nodes and start httpd service'
    hosts: web_nodes
    tasks:
        -
            name: 'Update entry into /etc/resolv.conf'
            lineinfile:
                path: /etc/resolv.conf
                line: 'nameserver 10.1.250.10'
        -
            name: 'Create a new user'
            user:
                name: web_user
                uid: 1040
                group: developers
        -
            name: 'Execute a script'
            script: /tmp/install_script.sh
        -
            name: 'Start httpd service'
            service:
                name: httpd
                state: present

```
