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

# Linked files

## hosts
This will be symlinked to the `hosts` directory in the root of your Ansible installation.

## files
This will be symlinked to the `files` directory in the root of your Ansible installation.

## templates
This will be symlinked to the `templates` directory in the root of your Ansible installation.

## ansible.cfg
This will be symlinked into the root of your Ansible installation.

More information:
* https://codeenigma.github.io/ce-provision-docs/2.x/roles/debian/ce_provision/
* https://github.com/codeenigma/ce-provision/blob/2.x/roles/debian/ce_provision/tasks/main.yml#L96-L132
