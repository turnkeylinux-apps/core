===============================
Locking Down Networked Services
===============================

Here we describe 2 methods for locking down networked services so they can only
be accessed from a specific IP address.

In both the below examples we will restrict access of webmin to a single IP
address. Note it is especially important you take care when performing the
webmin route as it is possible to accidently lock yourself out of webmin.


Webmin
======

Everything described below happens within the webmin console accessible from your
turnkey server on port 12321 (e.g. https://www.example.com:12321)

1. 
    Open the ``Linux Firewall`` section under the ``Networking Tab``

 .. image:: webmin_1.png

2.
    In the center of this page you will see a list of rules, click the item which's
    condition says ``If protocol is TCP and destination port is 12321``
    (this is the port of webmin)
 
 .. image:: webmin_2.png

3.
    At the top of the ``Condition details`` section you should see the text
    ``Source address or network`` next to this is a dropdown, change this dropdown
    to ``equals`` and then in the box to the right type in the ip address you want
    to be able to access webmin from.

 .. image:: webmin_3.png

4.
    Click the green ``Save`` button at the bottom of the page. Webmin will then
    redirect back to the ``Linux Firewall`` page

5.
    Click the blue ``Apply Configuration`` button near the bottom of the page then
    tick ``Yes`` next to ``Activate at boot`` also near the bottom of the page.


Command Line
============


1.
    First we should check the current iptable rules for port 12321 to do this type
    the following:
    
    .. code:: bash

        iptables -S INPUT | grep -- '--dport 12321'

    With default turnkey config you should get the following as output:

    .. code:: bash

        -A INPUT -p tcp -m tcp --dport 12321 -j ACCEPT

2.
    Next run:

    .. code:: bash

        iptables -L INPUT --line-numbers

    this will give you a listing of all iptable rules in the chain INPUT.
    Find the line which mentions 12321 (it should be on the right-most column),
    then find the line number associated with it (on the leftmost column).

    In my case I get:::

        Chain INPUT (policy DROP)
        num  target     prot opt source               destination         
        1    ACCEPT     all  --  anywhere             anywhere            
        2    ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
        3    ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
        4    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
        5    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
        6    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
        7    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:12320
        8    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:12321
        9    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:12322

    Which means the line number I need to remember is 8.

3.
    Now we replace entry number 8 in the INPUT chain with a similar entry that only
    allows a single IP address, to do this we take the options we got from step 1
    and insert ``-s <the.ip.we.want.to.allow>`` and remove the ``-A INPUT`` prefix.
    It should look as follows assuming you're running a clean turnkeylinux installation.

    .. code:: bash

        -s 1.2.3.4 -p tcp -m tcp --dport 12321 -j ACCEPT


    now we need to tell iptables to replace entry number 8, so we pass the arguments
    we just constructed to iptables as follows:

    .. code:: bash

        iptables -R INPUT 8 -s 1.2.3.4 -p tcp -m tcp --dport 12321 -j ACCEPT

4.
    Lastly we need to ensure these settings will persist after a reboot. To do so
    run the following:
   
    .. code:: bash

        iptables-save > /etc/iptables.up.rules
