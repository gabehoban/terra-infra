# Initial Setup for RPI Hosts (Ubuntu 24.10)

1. Provision a non-default priviledged user:
```bash
sudo adduser <username>
sudo usermod -aG sudo <username>
sudo usermod -aG adm <username>
sudo usermod -aG dialout <username>
```

2. Switch to the new user
```bash
sudo su - <username>
```

3. Import authorized keys from github
```bash
ssh-import-id gh:gabehoban
```

4. Run the intial system package upgrade
```bash
sudo apt update
sudo apt upgrade -y
sudo apt dist-upgrade -y
sudo apt autoremove -y

sudo reboot
```

5. Remove the default 'ubuntu' user account
```bash
deluser --remove-home ubuntu
```

6. Set system hostname
```bash
sudo hostnamectl set-hostname <hostname>
```

7. Enable Ubuntu Pro features
```bash
# Full command at https://ubuntu.com/pro/dashboard
sudo pro attach <token>
```

8. Run the host-specific ansible playbook (verify no errors in playbook output)
```bash
ansible-playbook playbooks/<hostname>.yaml
```

9. Sanity check that services are running as expected
```bash
# For DNS servers, run a dns lookup against the host IP address
dig @<host_ip> github.com

# For NTP servers, query the server with chrony
sudo chronyc ntpdata <host_ip>
```
