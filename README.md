Harden WordPress
=========

Hardens existing WordPress installations for multiple installations on a host following the [[security guidelines]](https://codex.wordpress.org/Hardening_WordPress#Website_Hosts).

Creates backups of files that are modified.

***WARNING***: This role modifies files and may break your site.

Requirements
------------

* The various files modified must be writable by the SSH user.  `become` is not used.
* For the `.htaccess` modifications to have any effect, the server must Apache and `AllowOverride` must be enabled.

Role Variables
--------------

    wp_harden_root: True

WordPress install location

    wp_harden_block_uploads_php: True

Block PHP execution in uploads directory.
See https://codex.wordpress.org/Hardening_WordPress#WP-Content.2FUploads

    wp_harden_block_wpconfig: True

Block access to wp-config.php.
See https://codex.wordpress.org/Hardening_WordPress#WP-Config.php

    wp_harden_disable_file_edits: True

Disable file editing.
See https://codex.wordpress.org/Hardening_WordPress#Disable_File_Editing

    wp_harden_block_include_only_files: True

Block access to include-only files.
See https://codex.wordpress.org/Hardening_WordPress#WP-Includes

    wp_harden_block_log_files:l True

Block access to some log files.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: kentr.harden-wordpress, installations: list_of_installations }

License
-------

BSD 3-Clause

Author Information
------------------

Kent Richards, https://kentrichards.net
