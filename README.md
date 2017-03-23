# Role Name: ceph-mon

A Ansible Role for ceph mon configure.

## Requirements

None.

## Role Variables

### `defaults/main.yml`

* `ceph_cluster_name: "ceph"`
* `ceph_fsid: "80605375-25ef-46b0-afee-97aff959463f"`
* `ceph_openstack_config: False`
* `ceph_pool_pg_num: 128`
* `openstack_glance_pool: "glance"`
* `openstack_cinder_pool: "cinder"`
* `openstack_nova_pool: "nova"`
* `openstack_cinder_backup_pool: "backups"`
* `ceph_openstack_config:`
    ```
      - { name: client.glance, value: "mon 'allow r' osd 'allow class-read object_prefix rbd_children, allow rwx pool={{ openstack_glance_pool }}'" }
      - { name: client.cinder, value: "mon 'allow r' osd 'allow class-read object_prefix rbd_children, allow rwx pool={{ openstack_cinder_pool }}, allow rwx pool={{ openstack_nova_pool }}, allow rx pool={{ openstack_glance_pool }}'"  }
      - { name: client.cinder-backup, value: "mon 'allow r' osd 'allow class-read object_prefix rbd_children, allow rwx pool={{ openstack_cinder_backup_pool }}'" }
    ```

## Dependencies

None.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Install ceph mon.
      hosts: ceph-mon
      roles:
        - role: ansible-role-ceph-mon

## Author Information

z
