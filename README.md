procmem
=========

An Ansible role to calculate memory used by a remote process.

There are many times that I've needed to know how much memory one or two key processes are taking on a server.
This Ansible role is made to make that simple.  Add the role to your playbook and it will install a script on
the server.  Then run ansible from the command line to run the script with the name of any process and it will
give you the results.

Requirements
------------

Currently the role has only been tested on Ubuntu 14.04.

Role Variables
--------------

    hiteshjasani_procmem_dest_dir: "/usr/local/bin" # script install directory

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Installation

Install the role from [ansible galaxy](https://galaxy.ansible.com/hiteshjasani/procmem/)

    % ansible-galaxy install hiteshjasani.procmem

### Example Playbook

To set up the script on the server, add the following to your playbook.  By default, the script will be
installed in `/usr/local/bin`.

    - hosts: servers
      roles:
         - { role: hiteshjasani.procmem }

It can also be installed to a custom location.

    - hosts: servers
      roles:
         - { role: hiteshjasani.procmem, hiteshjasani_procmem_dest_dir: "/opt/local/bin" }

### Usage

After the script is installed, you can invoke it as follows from the command line:

    % ansible servers -m shell -a "/usr/local/bin/procmem.sh apache2"
    11 processes using (MB): 434.094
    avg process size (MB): 39.4631

    % ansible servers -m shell -a "/usr/local/bin/procmem.sh mysqld"
    1 processes using (MB): 74.1094
    avg process size (MB): 74.1094

License
-------

BSD

Author Information
------------------

Hitesh Jasani

