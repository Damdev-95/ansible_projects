## Ansible Inventory
```
# Web Servers
web1 ansible_host=server1.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web2 ansible_host=server2.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web3 ansible_host=server3.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!

# Database Servers
db1 ansible_host=server4.company.com ansible_connection=winrm ansible_user=administrator ansible_password=Password123!

[web_servers]
web1
web2
web3

[db_servers]
db1


#group servers for both web and db
[all_servers:children]
web_servers
db_servers

```

![image](https://user-images.githubusercontent.com/71001536/165075877-15b55064-454e-41d2-ba2a-56b3afab4586.png)

![image](https://user-images.githubusercontent.com/71001536/165075958-aec1330e-4eff-4c39-a718-a4dec19b3284.png)


## Sample Inventory file
```
# DB Servers
sql_db1 ansible_host=sql01.xyz.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Lin$Pass
sql_db2 ansible_host=sql02.xyz.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Lin$Pass

# wEB servers
web_node1 ansible_host=web01.xyz.com ansible_connection=winrm ansible_user=administrator ansible_password=Win$Pass
web_node2 ansible_host=web02.xyz.com ansible_connection=winrm ansible_user=administrator ansible_password=Win$Pass
web_node3 ansible_host=web03.xyz.com ansible_connection=winrm ansible_user=administrator ansible_password=Win$Pass


# Group for db servers
[db_nodes]
sql_db1
sql_db2

# Group for web servers
[web_nodes]
web_node1
web_node2
web_node3

# Group for servers in Boston
[boston_nodes]
sql_db1
web_node1

# Group for servers in Dallas
[dallas_nodes]
sql_db2
web_node3
web_node2

# Group for servers in United States
[us_nodes:children]
boston_nodes
dallas_nodes
```
