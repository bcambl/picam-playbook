# Pi Motion Playbook

Automate the installation and configuration of raspberrypi `motion` cameras

### Ensure the following set via `raspi-config`
- camera enabled
- video memory split to `128` MB

### Requirements

Ansible must be installed to use ansible playbooks

```
sudo easy_install pip
sudo pip install ansible
```

---

### Instructions

1. Edit the `hosts` file with the IP address of each raspberry pi

2. Ensure you have an ssh key setup to each raspberry pi

    From workstation terminal, do the following for each raspberry pi
    ie:
    ```
    ssh-copy-id pi@192.168.X.X
    ```
    The above command will prompt for your password

3. Install:
    ```
    ansible-playbook -i hosts picam.yml --tags install
    ```

### Modifying motion settings

Modify motion settings in `settings.yml` then execute

```
ansible-playbook -i hosts picam.yml --tags configure
```
The `motion` service will be restarted after the configurations have been updated.
