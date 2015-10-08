## RFFI deployment at MS Azure

Manifests / modules to help the deploy our apps on CentOS 7.1 with either Ansible

## Usage

### Development:

    $ vagrant up
    $ vagrant provision # For updates

Open: https://192.168.0.44/

SSH: `$ vagrant ssh`

### Azure:

    $ ansible-playbook azure.yml

**Example vars**:
You can support it with [Direnv](https://github.com/zimbatm/direnv) or similar tool.

    AZURE_SUBSCRIPTION_ID="SOMELONGID"
    AZURE_SSH_PEM="/path/to/ssh.pem"
    AZURE_VM_NAME="VMNAME"
    AZURE_VM_USER="VMUSER"
    AZURE_VM_BLOB="https://someurl.blob.core.windows.net/vhds"

    export AZURE_SUBSCRIPTION_ID AZURE_SSH_PEM AZURE_VM_NAME AZURE_VM_USER AZURE_VM_BLOB

### Production:

For the first time if we need login as `root`:

    $ ansible-playbook playbook.yml -i production --extra-vars="init=y"

Next time, when root access will be restricted:

    $ ansible-playbook playbook.yml -i production

Open: https://YOUR_PRODUCTION_SERVER/

SSH: `$ ssh SERVER_ADMIN_USER@production.host.com -i PATH_TO_YOUR_KEY_OR_ADD_DOMAIN_TO_CONFIG`
