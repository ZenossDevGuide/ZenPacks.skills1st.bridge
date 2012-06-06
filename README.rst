=========================
ZenPacks.skills1st.bridge
=========================


Description
===========

This ZenPack queries the BRIDGE MIB in a switch to provide some Layer 2 topology information.  A separate tab is created for switches showing  port numbers and the remote MAC, IP address and hostname of the device connected to the port.  The standard Status tab of a switch device is augmented to show the base bridge MAC address against the Serial # field and the number of ports is displayed as the Tag #.

Switch devices need to support the BRIDGE MIB as defined by  RFCs 1493 and 4188.

The ZenPack includes the new device class of BridgeMIB as a subclass of /Devices/Network/Switch.  It includes standard MIB-2 MIBs and the BRIDGE MIB and also includes two performance templates for port performance data.

So far, this has only been tested on Cisco Catalyst 1900 and 2900 switches.

The ZenPack has now been updated to work reasonably well with Zenoss 3 (tested with 3.1 but feedback and comments are still welcome.  I attach the 1.0.4 version of the ZenPack here, pending it being included in the standard Zenoss sources.  

The real purpose of this ZenPack is as an example to help illustrate the paper on developing ZenPacks.  The original, Zenoss 2 paper is at Creating Zenoss ZenPacks , whilst the updated version is at http://community.zenoss.org/docs/DOC-10268 


Requirements & Dependencies
===========================

    * Zenoss Versions Supported: 3.0
    * External Dependencies: 
    * ZenPack Dependencies:
    * Installation Notes: zenhub and zopectl restart after installing this ZenPack.
    * Configuration: 

Limitations
===========

I have seen 2 quirks with the 1.0.4 version and I don't know whether it is this ZenPack, Zenoss, or my testing environments.  One was installing the 2.4 version on Zenoss 2.5.2.  I installed with a zenpack--install command, bounced zenhub and zopectl and everything was fine.  Went to view it through the Zenoss GUI and it didn't show - in fact it had been completely de-installed!  Did it again and everything was fine.

Second quirk was with a Zenoss 3 where devices installed into the BridgeMIB class didn't pick up the BridgeInterface relationship (no Bridge Interface menu under Components).  I moved the device to /Network/Switch and back to /Network/Switch/BridgeMIB and everything was fine ere after.

Input on these two quirks would also be appreciated.

Download
========
Download the appropriate package for your Zenoss version from the list
below.

* Zenoss 3.0+ `Latest Package for Python 2.6`_

Installation
============
Normal Installation (packaged egg)
----------------------------------
Copy the downloaded .egg to your Zenoss server and run the following commands as the zenoss
user::

   zenpack --install <package.egg>
   zenhub restart
   zopectl restart

Developer Installation (link mode)
----------------------------------
If you wish to further develop and possibly contribute back to this 
ZenPack you should clone the git repository, then install the ZenPack in
developer mode::

   zenpack --link --install <package>
   zenhub restart
   zopectl restart

Configuration
=============

Tested with Zenoss 3.1 

Change History
==============
    * 1.0 initial release
    * 1.0.1 minor fix for loading warning
    * 1.0.2 Changes to display the information a little differently.
    * 1.0.3 Zenoss 3.0 support
    * 1.0.4 Zenoss 3.0 version has single Bridge Interface submenu under Components with graphs and details
    * 1.0.5 updated for new github procedures
    * 1.0.6 updated to include code to delete components


Screenshots
===========
|bridge_zenpack_doc_3|
|bridge_zenpack_doc_4|


.. External References Below. Nothing Below This Line Should Be Rendered

.. _Latest Package for Python 2.6: https://github.com/jcurry/ZenPacks.skills1st.bridge/blob/master/dist/ZenPacks.skills1st.bridge-1.0.5-py2.6.egg?raw=true

.. |bridge_zenpack_doc_3| image:: http://github.com/jcurry/ZenPacks.skills1st.bridge/raw/master/screenshots/bridge_zenpack_doc_3.jpg
.. |bridge_zenpack_doc_4| image:: http://github.com/jcurry/ZenPacks.skills1st.bridge/raw/master/screenshots/bridge_zenpack_doc_4.jpg

                                                                        

