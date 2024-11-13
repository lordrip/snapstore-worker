# Snapstore worker installer
This script installs the snapstore worker on a fresh Raspberry PI OS installation.

## Installation
1. Clone this repository
2. Copy the [`inventory.ini-example`](inventory.ini-example) file to `inventory.ini`
```bash
cp inventory.ini-example inventory.ini
```
3. Edit the `inventory.ini` file and set the correct values
```
[raspberry_pi]
# <IP>        ansible_user=<USER>    ansible_ssh_private_key_file=<PATH_TO_SSH_KEY>
192.168.1.184 ansible_user=rmartinez ansible_ssh_private_key_file=~/.ssh/id_rsa
```
4. Enable the `ssh` service on the Raspberry PI
5. Run the [`kiosk_setup.yaml`](kiosk_setup.yaml) playbook
```bash
ansible-playbook -i inventory.ini kios_setup.yaml
```
