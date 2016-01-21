TurnKey Core - Debian GNU/Linux with Batteries Included
=======================================================

TurnKey Core is the base operating system which all TurnKey GNU/Linux
solutions share in common. It is commonly deployed standalone as a
convenient starting point for custom system integrations. Benefits
include automatic daily security updates, 1-click backup and restore, a
web control panel, and preconfigured system monitoring with optional
email alerts.

Features:

- **Base Operating System**: Debian GNU/Linux 8 (Jessie).

- **Build formats**: Deploys on bare metal, virtual machines (e.g.,
  OpenStack, VMWare, VirtualBox, OpenVZ, KVM, Xen) and in the cloud.
   
  - `ISO images`_: Generic installable Live CD. Installs anywhere.
  - `Virtual Machine images`_: Optimized for virtualized hardware,
    pre-installed and ready to run.
  - `Amazon Machine Image (AMI)`_: Best launched via the `TurnKey
    Hub`_.

- **Free as in speech**: `free software`_ with `full source code`_ and a
  `powerful build system`_. Free of hidden backdoors, free from
  restrictive licensing and free to learn from, modify and distribute.

- **Secure and easy to maintain**: `Auto-updated daily`_ with latest
  Debian security patches. Optional monitoring and email notification of
  `system alerts`_.

- **1-click backup and restore** (`TKLBAM`_): smart backup and data
  migration software saves changes to files, databases and package
  management to encrypted storage which a system can be automatically
  restored from.
  
- **Dynamic DNS** (`HubDNS`_): Associates your IP with a custom domain
  or the free \*.tklapp.com domain.

- **Logical Volume Management** (`LVM`_): Instead of installing to a
  fixed size partition, a Logical Volume is first created by default,
  and this may later be expanded, even across multiple physical devices.

- **AJAX web shell** (`shellinabox`_) - secure command line access from
  any web browser.

- **Web management interface** (`Webmin`_):
   
  - Listens on port 12321 (uses SSL).
  - Mac OS X themed.
  - Network modules:
     
    - Firewall configuration (with example configuration).
    - Network configuration.

  -  System modules:
     
     - Backup and migration (TKLBAM).
     - Configure time, date and timezone.
     - Configure users and groups.
     - Manage software packages.
     - Change passwords.
     - System logs.

  -  Tool modules:
     
     - Text editor.
     - Shell commands.
     - Simple file upload/download.
     - File manager (needs support for Java in browser).
     - Custom commands.

  -  Hardware modules:
     
     - Partitions on local disks.
     - Logical volume management.

- **Simple configuration console** (`confconsole`_):
   
  - Displays basic usage information.
  - Configure networking.

- **First boot initialization** (`inithooks`_):
   
  - Prompt user for passwords.
  - Regenerates SSL and SSH cryptographic keys.
  - Installs latest security updates, unless user chooses to defer this
    for later.

- **Command line power tools**
   
  - Smart, programmable bash shell completion: helps you get more done
    with fewer keystrokes.
  - Support for $HOME/.bashrc.d `shell hooks`_
  - Persistent environment variables (see $HOME/.bashrc.d/penv)::

       penv-set pydoc /usr/share/doc/python2.6/html
       exit
       # later...
       cd $pydoc

- **Automatic time synchronization with NTP**

- Take a look at some `screenshots`_.

Credentials *(passwords set at first boot)*
-------------------------------------------

-  Webmin, SSH, Shellinabox: username **root**

.. _free software: https://www.turnkeylinux.org/license
.. _full source code: https://github.com/turnkeylinux-apps
.. _powerful build system: https://www.turnkeylinux.org/tkldev
.. _system alerts: https://www.turnkeylinux.org/docs/automatic-security-alerts
.. _screenshots: https://www.turnkeylinux.org/screenshots/148
.. _headless build types: https://www.turnkeylinux.org/docs/builds#builds-table
.. _ISO images: https://www.turnkeylinux.org/docs/builds#iso
.. _Virtual Machine images: https://www.turnkeylinux.org/docs/builds#vm
.. _Amazon Machine Image (AMI): https://www.turnkeylinux.org/docs/ec2
.. _TurnKey Hub: https://hub.turnkeylinux.org
.. _AMI codes: https://www.turnkeylinux.org/docs/ec2/ami
.. _TKLBAM: https://www.turnkeylinux.org/tklbam
.. _Auto-updated daily: https://www.turnkeylinux.org/docs/automatic-security-updates
.. _HubDNS: https://www.turnkeylinux.org/dns
.. _LVM: http://tldp.org/HOWTO/LVM-HOWTO/
.. _shellinabox: https://github.com/shellinabox/shellinabox
.. _Webmin: http://webmin.com/
.. _confconsole: https://github.com/turnkeylinux/confconsole
.. _inithooks: https://github.com/turnkeylinux/inithooks
.. _shell hooks: https://www.turnkeylinux.org/blog/generic-shell-hooks
