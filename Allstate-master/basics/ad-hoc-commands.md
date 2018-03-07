Syntax
#### ansible host-pattern -i <inventoryfile> -m <module> -a <arguments> 

Default module is command
module_name = command

```sh
ansible <hosts> -m command -a '/usr/bin/hostname'
ansible <hosts> -m command -a '/usr/bin/hostname' -o # Single Line Output
```

```sh
#### command module will not be able to access shell variables, redirection and piping 
ansible <hosts> -m command -a set # fails
ansible <hosts> -m shell -a set # success
ansible <host> -m shell -a 'echo $TERM'
ansible <hosts> -m copy -a "src=/etc/hosts dest=/tmp/hosts"
ansible <hosts> -m file -a "dest=/tmp/hosts mode=600"
ansible <hosts -m file -a "dest=/tmp/hosts mode=600 owner=student group=student"
ansible <hosts> -m file -a "dest=/tmp/cts mode=755 owner=student group=student state=directory"
ansible <hosts> -m file -a "dest=/tmp/cts state=absent"
ansible <hosts> -m apt -a "name=apache2 state=present"
ansible <hosts> -m apt -a "name=tree state=latest"
ansible <hosts> -m apt -a "name=tree state=absent"
ansible <hosts> -m user -a "name=test password=ansibletest
ansible <hosts> -m shell -a 'id'
ansible <hosts> -m shell -a 'id' -u <other_remote_user>
ansible <hosts> -m copy -a 'content="Managed by Ansible\n' dest=/etc/motd' -u <other_remote_user>
ansible <hosts> -m copy -a 'content="Managed by Ansible\n' dest=/etc/motd' -u <other_remote_user> --become --become_user root
ansible <hosts> -m shell -a 'cat /etc/motd' -u <other_remote_user>
ansible <hosts> -m service -a "name=httpd state=started"
```

####Pull a git repo using ansible ad-hoc commands
```sh
ansible localhost -m yum -a "name=git"
ansible localhost -m git -a "repo=https://github.com/rgodishela/Allstate.git dest=/tmp/Allstate clone=yes"
```
