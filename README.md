## Summary

This Vangrant file creates the minimum number of VMs, with appropriate hostnames, to use as a lab environment for the Red Hat DO180 course "Red Hat OpenShift Administration I -
Managing Containers and Kubernetes."

For the configure.yml playbook to work, you need to create a vault.yml file that contains the variables rh_user and rh_pw that are an active redhat developer account in order to register the rhel 9 vms with Red Hat repositories.

Or the variables can be set directly in the configure.yml playbook.

For convenience, if using an ansible vault file, consider adding the vault password to a dotfile and the following line in an ansible.cfg file in the directory with the playbook:

ansible.cfg:
---
[defaults]
vault_password_file=/path/to/password/in/a/file

## Registry

This course requires a registry container to hold images used by the OpenShift node. Deploying a quay.io repository is probably the closest substitute to RH's own repository. The instructions are [here](https://github.com/quay/quay/blob/master/docs/quick-local-deployment.md) and should be run on the registry node.



