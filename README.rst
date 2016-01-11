TurnKey Core - Common Base for All Appliances
=============================================

The common base system on top of which all TurnKey Linux appliances are
built. It includes custom automated backup and migration software, a web
management interface, automatic daily security updates, live installer,
configuration console, and all other common features. Take a look at
some `screenshots`_.

Features:

- **Base distribution**: Debian 8 (Jessie).
- **Build formats**: Deploys on bare metal, virtual machines (e.g.,
  OpenStack, VMWare, VirtualBox, OpenVZ, KVM, Xen) and in the cloud.
   
  - `ISO images`_: Generic installable Live CD. Installs anywhere.
  - `Virtual Machine images`_: Optimized for virtualized hardware,
    pre-installed and ready to run.
  - `Amazon Machine Image (AMI)`_: Best launched via the `TurnKey
    Hub`_.

- **Smart backups** (`TKLBAM`_): Automated backup and restore, with
  system migration capabilities.
- **Secure and easy to maintain**: `Auto-updated`_ daily with latest
  security patches.
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

Logging in for Administration
-----------------------------

**No default passwords**: For security reasons there are no default
passwords. All passwords are set at system initialization, which happens
either at:

1) First login for `headless build types`_ (e.g., EC2, OpenStack, Xen)
2) First boot for non-headless build types (ISO, VM, VMDK)

**Ignore SSL browser warning**: browsers don't like self signed SSL
certificates, but this is the only kind that can be generated
automatically without paying a commercial Certificate Authority. 

**Username for OS system administration**:

  Login as **root** except on `AWS marketplace`_ which uses username
  **admin**.

  1) Point your browser to:

     - https://12.34.56.789:12321/ - Web management interface 
     - https://12.34.56.789:12320/ - AJAX web terminal
       
  2) Login with SSH client::
  
      ssh root@12.34.56.789

     Special case for AWS marketplace::

      ssh admin@12.34.56.789 
      
  \* Replace 12.34.56.789 with a valid IP or hostname.
  
.. link to read more

.. _AWS marketplace: https://aws.amazon.com/marketplace
.. _screenshots: https://www.turnkeylinux.org/screenshots/148
.. _headless build types: https://www.turnkeylinux.org/docs/builds#builds-table
.. _ISO images: https://www.turnkeylinux.org/docs/builds#iso
.. _Virtual Machine images: https://www.turnkeylinux.org/docs/builds#vm
.. _Amazon Machine Image (AMI): https://www.turnkeylinux.org/docs/ec2
.. _TurnKey Hub: https://hub.turnkeylinux.org
.. _AMI codes: https://www.turnkeylinux.org/docs/ec2/ami
.. _TKLBAM: https://www.turnkeylinux.org/tklbam
.. _Auto-updated: https://www.turnkeylinux.org/docs/automatic-security-updates
.. _HubDNS: https://www.turnkeylinux.org/dns
.. _LVM: http://tldp.org/HOWTO/LVM-HOWTO/
.. _shellinabox: https://github.com/shellinabox/shellinabox
.. _Webmin: http://webmin.com/
.. _confconsole: https://github.com/turnkeylinux/confconsole
.. _inithooks: https://github.com/turnkeylinux/inithooks
.. _shell hooks: https://www.turnkeylinux.org/blog/generic-shell-hooks
