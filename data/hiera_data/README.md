# Hiera Data

This directory contains all the default data that will be accessible via hiera. Hiera has a lookup order which is specified in /etc/puppet/hiera.yaml on the build server. While your deployment may vary slightly, the order will generally follow a form like this:

    
    # For overriding things on a specific host
    hostname/%{hostname}
    
    # For things specific to your environment, like your passwords or proxy address
    user

    # If you are deploying with multiple scenarios, you can use this to differentiate between the two
    user.%{scenario}

    # This contains some defaults that are used to test this repository. 
    user.common

    # The entries below user.common are used when developing scenarios and should generally not be modified by the user

Users should generally add changes they want to user.yaml, unless it is host/scenario specific. User.yaml resides in /etc/puppet/data/hiera\_data/user.yaml, though it will not exist on install. Take a look at user.common.yaml and common.yaml to see the default required settings - any of these can be overridden by putting different values into user.yaml. Here is a quick reference for the most common features that can be added to user.yaml that aren't in either of the common.yaml files, for the roles in the 2\_role scenario:

## Config for all nodes

The following parameters will affect all nodes:

### Mandatory config

    # Set the name of the build node - this can be an IP or a resolvable hostname
    coe::base::build_node_name: 192.168.100.10

    # Set the hostname of the control node
    coe::base::controller_hostname: controller_name

    # Set the IP address of the control node
    coe::base::controller_node_internal: 192.168.100.20

### Optional Config

    # Configure which repository to get packages from. Can be 'cisco_repo' or 'cloud_archive'
    # The former is an apt repo maintained by Cisco and the latter is the Ubuntu Cloud Archive
    coe::base::package_repo: 'cisco_repo'

    # Which Openstack release to install - can be 'grizzly' or 'havana'. Other versions currently untested.
    coe::base::openstack_release: 'havana'

    # If cisco_repo is used, the mirror location can be configured as either ftp or http:
    coe::base::openstack_repo_location: 'ftp://ftpeng.cisco.com/openstack'
    coe::base::openstack_repo_location: 'http://openstack-repo.cisco.com/openstack'

    # Cisco maintains a supplemental repo with packages that aren't core to Openstack, but
    # are frequently used, such as ceph and mysql-galera. It can be enabled using ftp or http
    coe::base::supplemental_repo: 'ftp://ftpeng.cisco.com/openstack/cisco_supplemental'
    coe::base::supplemental_repo: 'http://openstack-repo.cisco.com/openstack/cisco_supplemental'

    # If you are using the ubuntu repo, you can change from 'main' (default) to 'updates'
    coe::base::ubuntu_repo: 'updates'

    # Set a proxy server
    coe::base::proxy: '192.168.100.100'

    # Set a gateway server
    coe::base::node_gateway: '192.168.100.101'

## Config for the build node



### Mandatory Config
## Config for the control node
### Mandatory Config
## Config for compute nodes
### Mandatory Config

