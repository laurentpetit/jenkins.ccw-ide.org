This repository provides Ansible playbooks to manage Counterclockwise Jenkins server

# Jenkins Server

The Jenkins server is  `jenkins.ccw-ide.org`

`laurentpetit/ccw` github repository has a hook to reach `jenkins.ccw-ide.org` which will trigger builds and deploys (when successful) to `updatesite.ccw-ide.org`

## Jenkins Server provisioning

### Jenkins Server Pre-requisite

- Have an Ubuntu 14.04 server, create a `jenkins.ccw-ide.org` subdomain type A DNS entry pointing to it

- root access during the Ansible configuration (playbook will deny password challenge for root, only accept key challenge, and install your public key)

### Ansible control machine Pre-requisite

You need Ansible ( http://www.ansible.com ) installed on your `Ansible control machine` (e.g. your laptop).

On OS X, you need the `sshpass` program for using ssh with passwords. You can install it via:

    brew install https://raw.github.com/eugeneoden/homebrew/eca9de1/Library/Formula/sshpass.rb

The passlib python library must be installed as well, e.g.

    pip install passlib
    # or
    easy_install passlib


### Provision the Jenkins Server

ansible-vault is used to encrypt some sensible data.

    ansible-playbook -u root -k -i hosts site.yml --vault-password-file /path/to/password-file

