Role Name
========

[Ansible](http://www.ansible.com) role to install [OpenDJ](http://opendj.forgerock.org/) LDAP v3 server.

This role downloads and installs the latest nightly build of OpenDJ. If you prefer to install a stable 
release, or if for some reason the nightly build is not available, you [must download a copy of the OpenDJ](http://forgerock.com/download-stack/)  zip file 
and update the variable *opendj_url* in defaults/main.yml to a location where the guest can access the zip file. Alternatively,
you can copy the OpenDJ zip file to the *download_dir* location. 

Requirements
------------

Requires Java SDK (1.7 or later) installed on the target.


This role requires ansible 1.4 or higher 


Role Variables
--------------

Default Variables (see defaults/main.yml for a more complete list)

- install_root (/opt). Where OpenDJ will be installed
- opendj_url. A URL where the OpenDJ can be downloaded from. Defaults to the ForgeRock Jenkins server.
- download_dir (/var/tmp/) . Where the OpenDJ binary is downloaded to
- opendj_ldap_port (389) LDAP port to listen on
- opendj_ldaps_port (636). LDAP SSL port to listen on
- opendj_admin_port (4444). Admin port
- opendj_jmx_port: (1689). JMX monitoring port
- opendj_basedn (dc=example,dc=com).  The default base DN for the directory
- opendj_service_name (opendj). The name of the service for starting/stopping OpenDJ


Example
-------

Configure two instances of OpenDJ on the same server (different ports)

    - hosts: ldap
      roles:
          - { role: opendj, install_root: "/opt/a" }
          - { role: opendj, install_root: "/opt/b", opendj_admin_port: 1444, opendj_ldap_port: 2389,
              opendj_ldaps_port: 2636 , opendj_jmx_port: 2689, opendj_service_name: "opendj2" }

Dependencies
------------

None

License
-------

MIT

Author Information
------------------

Warren Strange. 

