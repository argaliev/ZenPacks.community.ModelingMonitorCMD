======================================
ZenPacks.community.ModelingMonitorCMD
======================================


Description
===========

!!! DEPRECATED !!! New version available at https://github.com/argaliev/ZenPacks.community.ModelingMonitor.
This ZenPack using command plugin to get information about modeling status,
but lack of perfomance with distributed collectors and number of devices more than hundred.
Zenpack check last modelling time of device and number of component classes, that must be presented in device.

Requirements & Dependencies
===========================

    * Zenoss Versions Supported: > 4.0
    * External Dependencies: 
    * ZenPack Dependencies:
    * Installation Notes: zenhub and zopectl restart after installing this ZenPack.
    * Configuration: 

Installation
============
Normal Installation (packaged egg)
----------------------------------
Copy the downloaded .egg to your Zenoss server and run the following commands as the zenoss
user::

   * zenpack --install <package.egg>
   * zenhub restart
   * zopectl restart

Developer Installation (link mode)
----------------------------------
If you wish to further develop and possibly contribute back to this 
ZenPack you should clone the git repository, then install the ZenPack in
developer mode::

   * zenpack --link --install <package>
   * zenhub restart
   * zopectl restart

Configuration
=============

Tested with Zenoss 4.2.5 

zProperties
-----------
- **zCompClassCount** - number of class components that expected to appear in device
- **zExpiryDaysPast** - number of days when last modeling time become outdated

Monitoring Templates
-----------
- **/Devices/Server/rrdTemplates/ModelingMonitor**

Event Classes
-----------
- **/Status/Modeling**
- **/Status/Modeling/ComponentMismatch**
- **/Status/Modeling/ModelTimeExpired**

Scripts ./libexec/
-----------
- **get_device_comps_count.zendmd** - script that compare number of device components classes with given number from zProperty zCompClassCount
- **get_device_last_model_time.zendmd** - script that compare last model time of device with given days ago from zProperty zExpiryDaysPast
