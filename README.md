maas-libvirt
=========

Creates user `maas_libvirt` and adds public key of each rack controller's `maas` user to the `maas_libvirt` user's authorized keys.

Requirements
------------

 * MAAS
 * Libvirt

Role Variables
--------------

    maas_libvirt_user_name: maas_libvirt
    maas_libvirt_user_groups: 'libvirt, libvirt-qemu'
    maas_libvirt_target_group_name: maas_libvirt
    maas_libvirt_source_group_name: maas_rack_controller
    maas_libvirt_log_keys: false

Example Playbook
----------------

Host file:

    [maas_rack_controller]
    maas-rack1.example.com
    maas-rack2.example.com

    [maas_libvirt]
    compute1.example.com
    compute1.example.com 


Playbook:

    - name: Manages compute resource hosts
      hosts: maas_rack_controller
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
