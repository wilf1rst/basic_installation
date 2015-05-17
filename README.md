Deploying Basic Configuration using Ansible Playbooks.
------------------------------------------------------

These playbooks require Ansible 1.2.

Place you servers IP or FQDN in the hosts file in the root of the playbook.

You can use the following command to deploy to all hosts:

        ansible-playbook -i hosts site.yml

If you want to limit to a particular server you have to use: 

	ansible-playbook -i hosts site.yml --limit <IP/FQDN DEFINED IN HOST FILE>

If you want to limit to a particular step you can use:

	ansible-playbook -i hosts sites.yml --tags <TAGS OF THE STATE>

All the following step tags are available:
	- basic : install updated sources.list / install basic packages (ntp, vim, fail2ban, htop, iotop, subversion, git)
	- ntp : start the ntp service and usure it's running
	- nrpe : install, configure and start nrpe for nagios 
	- sshkey : copy ssh public key of sshroot in the authorized_keys file
	- vim : configure vim with pathogen packages, add vim-airline bar, use syntax & auto-indent

You can combine the command like:

        ansible-playbook -i hosts sites.yml --tags <TAGS OF THE STATE> --limit <IP/FQDN DEFINED IN HOST FILE>

Or use group instead of single host. Please report to the ansible documentation for further informations:

	http://docs.ansible.com 
