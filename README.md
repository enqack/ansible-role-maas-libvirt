Role Name
=========

Creates user `maas_libvirt` and adds public key of each rack controller's `maas` user to the `maas_libvirt` user's authorized keys.

Requirements
------------

MAAS
Libvirt

Role Variables
--------------

    maas_libvirt_user_name: maas_libvirt
    maas_libvirt_user_groups: 'libvirt, libvirt-qemu'
    maas_libvirt_target_group_name: maas_libvirt
    maas_libvirt_source_group_name: maas_rack_controller

Example Playbook
----------------

Host file:

    [computehosts]
    maas-rack1.example.com
    maas-rack2.example.com

    [maas_libvirt]
    compute1.example.com
    compute1.example.com 


Playbook:

    - name: Manages compute resource hosts
      hosts: computehosts
      become: yes

      roles: 
        - role: enqack.maas-libvirt
          tags: [ 'role::maas-libvirt' ]

License
-------

BSD

Author Information
------------------

Steve Verhelle (enqack) enqack@gmail.com
