# Role Name

I needed a role that didn't rely on yum to install Oracle JDK. It's not pretty but sometimes I need multiple JAVA_HOMES. This role allows that. Additionally it can install the JCE, as well as set the alternatives, latest, and default symlinks.

Finally, it can set the entropy fix for running on virtualized hardware.

NOTE: This is just for RHEL, CentOS, EL. 

## Role Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Install the Oracle JCE:

    java_install_jce: false

Sets the entropy source, securerandom.source=file:/dev/./urandom

    java_entropy_fix: false

Sets the default install location for RHEL

    java_install_dir: /usr/java

Clean up after yourself?

    java_remove_download: yes

Pull the files from Oracle? Implies you have accepted the license agreement.

    java_download_from_oracle: yes

Where to locate the files on the local machines. Also where the files need to be if not downloaded. Set the 'java_download_from_oracle' flag if you have the correct files already placed.

    java_download_path: /usr/local/src

Which version of course. Look to the defaults in the role for the dictionary of latest versions.

    java_version: 8u91

Set the default symlink? Also fires off the alternatives routine.

    java_set_as_default: true

set the latest symlink?

    java_set_as_latest: true

## Dependencies

No dependencies on other roles.

IMPORTANT: Using this role implies that you have accepted the Oracle license agreement to download the Oracle JDK and JCE. If you don't agree, don't use this role please.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      become: yes
      become_user: root
      vars:
        java_install_jce: yes
        java_entropy_fix: yes
        java_remove_download: yes
        java_download_from_oracle: yes
        java_version: 8u74
        java_set_as_default: yes
        java_set_as_latest: yes
      roles:
        - role: staylorx.oracle-jdk

## License

MIT

