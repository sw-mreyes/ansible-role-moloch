# Ansible role for Moloch 
This basic Ansible role is used to setup [Moloch](https://molo.ch) on a single server instance. The motivation to create this role was to create an automated setup of a Malware Analysis Lab in conjunction with the [Cuckoo Sandbox](https://cuckoosandbox.org/).

## Compatibility
This role was only tested on Ubuntu 18.04, but should work on all Debian based systems which are supported by Moloch.

## Role variables 

The following variables are available:  

```
moloch_deb_url: "https://files.molo.ch/builds/ubuntu-18.04/moloch_1.5.3-1_amd64.deb" 
moloch_interface: eth0
moloch_password: SomeRandomString
moloch_admin_password: SomeOtherRandomString
```

### moloch_deb_url 
Change the URL which is used to get the deb package for Moloch if you require a different version or if you are installing it on another OS than Ubuntu 18.04.  

### moloch_interface 
The interface Moloch will listen for traffic  

### moloch_password
The password which is used to encrypt S2S and other things.

### moloch_admin_password
The admin users's password

## Example Playbook
```
-
  hosts: sandboxes
  roles:   
    -
      role: ansible-role-moloch
      tags: role-moloch
```

## How to use it

1. Configure the role variables in your group or host vars
2. Put the role into a playbook
3. Run the playbook
4. Access the web interface on http://<your-server>:8005 with user "admin" and the password defined in `moloch_admin_password`