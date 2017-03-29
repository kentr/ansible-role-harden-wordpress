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

### WordPress install location

The role takes a list of installations to harden, in the variable `installations`:

    installations:
      - root: Required. Absolute path to the item's root web folder.  No default.
        uploads_dir: Optional. Path to uploads directory, relative to the item's root.  Defaults to "wp-content/uploads".

### Global hardening options:

Disable PHP execution in uploads directory.
See https://codex.wordpress.org/Hardening_WordPress#WP-Content.2FUploads

    wordpress_harden_disable_uploads_php: True

Deny access to wp-config.php.
See https://codex.wordpress.org/Hardening_WordPress#WP-Config.php

    wordpress_harden_deny_wpconfig_access: True

Disable file editing.
See https://codex.wordpress.org/Hardening_WordPress#Disable_File_Editing

    wordpress_harden_disable_file_edits: True

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
