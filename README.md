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
5. Clone this repository
6. Copy the [`inventory.ini-example`](inventory.ini-example) file to `inventory.ini`
```bash
cp inventory.ini-example inventory.ini
```
7. Edit the `inventory.ini` file and set the correct values
```
[raspberry_pi]
# <IP>        ansible_user=<USER>    ansible_ssh_private_key_file=<PATH_TO_SSH_KEY>
192.168.1.184 ansible_user=rmartinez ansible_ssh_private_key_file=~/.ssh/id_rsa
```
8. Install ansible-galaxy dependencies
```bash
ansible-galaxy install -r requirements.yaml
```

## Installation on the Raspberry PI
1. Enable the `ssh` service on the Raspberry PI
2. Run the [`kiosk_setup_linux.yaml`](kiosk_setup_linux.yaml) playbook
```bash
ansible-playbook -i inventory.ini kios_setup_linux.yaml
```

## Installation on Windows
1. Install openssh server on Windows
```powershell
winget install OpenSSH.Server
```
2. Run the [`kiosk_setup_windows.yaml`](kiosk_setup_windows.yaml) playbook
```bash
ansible-playbook -i inventory.ini kios_setup_windows.yaml
```
