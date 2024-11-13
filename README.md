# Snapstore worker installer
This script installs the snapstore worker on a fresh Raspberry PI OS installation.

## Requirements
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- A Raspberry PI with a fresh Raspberry PI OS installation
- A `ssh` key to connect to the Raspberry PI

## Preparing the installer environment
1. Create a virtual environment
```bash
python3 -m venv .venv
```
2. Activate the virtual environment
```bash
source .venv/bin/activate
```
3. Install pipx
```bash
# Fedora / CentOS Sream / RHEL
sudo dnf install pipx

# Ubuntu / Debian
sudo apt install pipx

# macOS
brew install pipx
```
4. Install ansible
```bash
pipx install --include-deps ansible
```

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
