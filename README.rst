TurnKey Core - Common Base for All Appliances
=============================================

The common base system on top of which all TurnKey Linux appliances are
built. It includes custom automated backup and migration software, a web
management interface, automatic daily security updates, live installer,
configuration console, and all other common features. Take a look at
some `screenshots`_.

Features:

- **Base distribution**: Debian 6.0.7 (Squeeze).
- **Build formats**: deploys on bare metal, virtual machines (e.g.,
  VMWare, VirtualBox, KVM, Xen) and in the cloud.
   
   - `ISO images`_: Generic installable Live CD. Installs anywhere.
   - `Virtual Machine images`_: Optimized for virtualized hardware.
     Pre-installed and ready to run.
   - `Amazon Machine Image (AMI)`_: best launched via the `TurnKey
     Hub`_.

- **Smart backups** (`TKLBAM`_): automated backup and restore, with
  system migration capabilities.
- **Secure and easy to maintain**: `auto-updated`_ daily with latest
  security patches
- **Dynamic DNS** (`hubdns`_): associates your IP with a custom domain
  or the free \*.tklapp.com domain
- **Logical Volume Management** (`LVM`_): instead of installing to a
  fixed size partition, a Logical Volume is first created by default,
  and this may later be expanded, even across multiple physical devices.
- **AJAX web shell** (`shellinabox`_) - secure command line access from
  any web browser.
- **Web management interface** (`Webmin`_):
   
   - Listens on port 12321 (uses SSL)
   - Mac OS X themed
   - Network modules
      
      - Firewall configuration (with example configuration).
      - Network configuration.

   -  System modules
      
      - Backup and migration (TKLBAM).
      - Configure time, date and timezone.
      - Configure users and groups.
      - Manage software packages.
      - Change passwords.
      - System logs.

   -  Tool modules
      
      - Text editor.
      - Shell commands.
      - Simple file upload/download.
      - File manager (needs support for Java in browser).
      - Custom commands.

   -  Hardware modules
      
      - Partitions on local disks.
      - Logical volume management.

-  **Simple configuration console** (`confconsole`_)
   
   - Displays basic usage information.
   - Configure networking.

- **First boot initialization**
   
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

-  **Automatic time synchronization with NTP**

.. _screenshots: http://www.turnkeylinux.org/screenshots/148
.. _ISO images: http://www.turnkeylinux.org/docs/builds#iso
.. _Virtual Machine images: http://www.turnkeylinux.org/docs/builds#vm
.. _Amazon Machine Image (AMI): http://www.turnkeylinux.org/docs/ec2
.. _TurnKey Hub: https://hub.turnkeylinux.org
.. _AMI codes: http://www.turnkeylinux.org/docs/ec2/ami
.. _TKLBAM: http://www.turnkeylinux.org/tklbam
.. _auto-updated: http://www.turnkeylinux.org/docs/automatic-security-updates
.. _hubdns: http://www.turnkeylinux.org/dns
.. _LVM: http://tldp.org/HOWTO/LVM-HOWTO/
.. _shellinabox: http://code.google.com/p/shellinabox/
.. _Webmin: http://webmin.com/
.. _confconsole: http://code.turnkeylinux.org/confconsole/docs/
.. _shell hooks: http://www.turnkeylinux.org/blog/generic-shell-hooks
