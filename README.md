# Holds private information for the ce-provision setup
This is a template repository intended as a starting point for new ce-provision installations. It contains sane defaults and example configurations for more complex infrastructures and all the configuration required for Ansible to work out of the box.

[Find out more about ce-provision here.](https://github.com/codeenigma/ce-provision/wiki)

# Using AWS EC2 inventory discovery
If you intend to use AWS as one of your hosting providers and you want to enable AWS inventory support, first in `ansible.cfg`. The default config file looks like this:

```conf
[inventory]
# enable inventory plugins, default: 'host_list', 'script', 'yaml', 'ini', 'auto'
enable_plugins = yaml, ini
# uncomment the below line and comment the above for AWS EC2 inventory discovery
#enable_plugins = amazon.aws.aws_ec2, yaml, ini
```

Change it to look like this:

```conf
[inventory]
# enable inventory plugins, default: 'host_list', 'script', 'yaml', 'ini', 'auto'
enable_plugins = amazon.aws.aws_ec2, yaml, ini
```

Then edit `hosts/aws_ec2.yml` and set it up how you wish.

# Using SOPS for variable encryption
SOPS is loaded in by default, however to use it you will need to add the PGP key fingerprint of any team member who needs to be able to encrypt and decrypt SOPS variables to `.sops.yml` in this repository.

[The SOPS documentation is here.](https://github.com/getsops/sops/blob/main/README.rst)

# Files and directories
Although ce-provision is fairly flexible, this is a list of supplied files and directories and what they are generally used for. It provides a model for potentially organising your Ansible configuration.

## Directories
These are the provided directories which are not linked into ce-provision.

### plays
This is a space where you can optionally keep playbooks that are unique to your organisation.

### roles
This is where we recommend you keep any roles that are unique to your organisation, for example they might contain configurations you do not wish to share or they might be simply of no use to the wider product. For example, we keep roles for managing our LDAP directory server in this directory. It is automatically included in Ansible's roles path in the provided `ansible.cfg`.

## Linked files
These files are obligatory in the config repository and are linked into ce-provision in the required places to make Ansible function as expected.

### hosts
This will be symlinked to the `hosts` directory in the root of your Ansible installation.

### files
This will be symlinked to the `files` directory in the root of your Ansible installation.

We have included a file called `galaxy-requirements.yml` which provides optional extra Ansible Galaxy roles and collections to be installed. You can alter this or remove it as you see fit.

### templates
This will be symlinked to the `templates` directory in the root of your Ansible installation.

### ansible.cfg
This will be symlinked into the root of your Ansible installation.

More information:
* https://codeenigma.github.io/ce-provision-docs/2.x/roles/debian/ce_provision/
* https://github.com/codeenigma/ce-provision/blob/2.x/roles/debian/ce_provision/tasks/main.yml#L96-L132
