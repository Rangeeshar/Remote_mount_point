# A Remote Directory Mounting Script
- The deploy_mount.yml is a script which will allow you to deploy sshfs mount point to multiple remote servers.

### Dependencies:
- install ansible using following code:
1. Using apt manager:
```
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible
```
2.Using python pip
- `sudo pip install ansible`

### How to run the script:
- Clone this repository after installing above dependencies and replace below given values in `deploy_mount.yml`:
    - `<Directory>` - directory which you want to bind the mount point. ex: /example_mount
    - `<User>` - User for whom you want give permission to access mount point. ex: john
    - `<Server-DNS>` - Server which you want to bind the above directory to. ex: remote@machine2.servers.hetz.com:/home/data

- Add the DNS of hosts on each line to make the script deploy the mount points to each one of them. ex: machine1.servers.hetz.com

- After changing the above values run the below command on the folder which contains deploy_mount.yml and hosts:
    `ansible-playbook --become --ask-become-pass -i hosts deploy_mount.yml`

- It will prompt for sudo password for changing file permission so enter it and that's it done.
