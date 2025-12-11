# How to install Ansible and start the inventory
## Preliminary steps
- Update and upgrade the maschine
  ```
  sudo apt update && sudo apt upgrade
  ```
- Update pip and then install Ansible
  ```
  python -m pip install --upgrade pip
  pip install ansible
  ```
- Add the directory (the one is given on the output) to the PATH on the last line. Then reload the file.
  ```
  nano ~/.bashrc 
  source ~/.bashrc
  ```
- Use SSH to connect to the machines
  ```
  Create a key on your host: ssh-keygen -t ed25519 -C "message"
  Copy the public key (.pub) on the remote machine: ~/.ssh/authorized_keys
  Try it with: ssh [user]@[ip/hostname]
  ```
- Create a folder for Ansible
  ```
  mkdir ansible && cd ansible
  ```
- Create an inventary-file inside the folder
  ```
  vim inventory.ini
  then >
    [myhosts]
    IP_of_the_machine
  ```
- Verify inventory and ping the hosts
  ```
  ansible-inventory -i inventory.ini --list
  ansible myhosts -m ping -i inventory.ini -u ansible
  ---> ansible is a user I created before, make sure you use a user that exists on your remote machine!
  ```