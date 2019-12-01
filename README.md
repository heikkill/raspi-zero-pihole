# raspi-zero-pihole
Ansible playbook(s) for setting up pi-hole, dnscrypt-proxy and pioled, running on Docker on Raspbian on Raspberry Pi Zero.

## Configuration
Modify content of these files accordingly and remove .template-postfix:
* [hosts.ini.template](hosts.ini.template): IP of RasPi0
* [secrets.vault.yml.template](group_vars/secrets.vault.yml.template): Passwords
  * Use [ansible-vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html#encrypting-unencrypted-files) to encrypt the secrets

Modify hostname, timezone & locale:
* [raspi.yml](group_vars/raspi.yml)

## How to prepare SD card with Raspbian Lite & network access
* Download [Raspbian Buster Lite image](https://downloads.raspberrypi.org/raspbian_lite_latest)
* Flash the image to an SD card with [Balena etcher](https://www.balena.io/etcher/)
* Add WiFi configuration if using Raspberry Pi Zero W
  * TODO: wpa_supplicant.conf, ssh
* Insert SD card to the RasPi0 and boot
* Connect to RasPi0 using default credentials
* Add your SSH public key in /home/pi/.ssh/authorized_keys

## How to run Pi-hole with dnscrypt-proxy on Docker on Raspberry Pi Zero
* Prepare SD card & Ansible configuration
* Run Ansible playbook:<br/>
    `ansible-playbook pihole.yml --ask-vault-pass --key-file "/path/to/ssh/private/key"`

## How to run Pi-hole with dnscrypt-proxy & pioled on Docker on Raspberry Pi Zero
* Prepare SD card & Ansible configuration
* Run Ansible playbook:<br/>
    `ansible-playbook pihole-pioled.yml --ask-vault-pass --key-file "/path/to/ssh/private/key"`
