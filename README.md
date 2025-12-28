# ansible-starter-kit

<img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/65c3ab8b-1fa4-4934-ab72-4caad1713f85" />

A minimal Ansible starter project. Clone it, update the inventory, and run a playbook in minutes.

## Project Structure 
```
ansible-starter-kit/
├── ansible.cfg
├── inventory.ini
├── group_vars/
│   └── group_a.yml
├── playbooks/
│   └── ping.yml
└── roles/
    └── ping/
        ├── defaults/
        │   └── main.yml
        └── tasks/
            └── main.yml
```

## Requirements

- Linux machine as the controller (where you run Ansible)
- Target Linux servers reachable via SSH

## Setup

### 1.Install Ansible (Ubuntu/Debian)
```
sudo apt update
sudo apt install -y ansible
```
SSH key setup

### 2.Set up SSH keys

Generate an SSH key pair on the controller:
```
ssh-keygen -t ed25519
```

Add your public key to each target server:
- Place it in: `/home/ubuntu/.ssh/authorized_keys`

### 3.Edit inventory.ini

Register your target servers:
```
ubuntu@Ansible:~/ansible-cp$ cat inventory.ini
[group_a]
test1 ansible_host=192.168.1.2 ansible_user=ubuntu
test2 ansible_host=192.168.1.3 ansible_user=ubuntu
test3 ansible_host=192.168.1.4 ansible_user=ubuntu
```

### 4.Dry run
```
ansible-playbook -l group_a playbooks/ping.yml -C
```

### 5.Run

```
ansible-playbook -l group_a playbooks/ping.yml 
```

## References

[Ansible Official Documentation](https://docs.ansible.com/)
