# Publish System Performance Data to MQTT
This service monitors the system performance data from files in Linux's
`/proc` file system data, mostly by the Python **psutil** module and
publishes them to a MQTT server.  From there the statistics are recorded
into an **InfluxDB** database.

This program is an experiment.  It is similar to the data collection
capabilities of [collectd](http://www.collectd.org) and
[Monitorix](http://www.monitorix.org).  These programs are sinks and
have limitied capabilities to act on the data as it is collected.

## License
This program is released under a MIT [license](./LICENSE).

## Implementation
The program was developed and tested on **Arch Linux**
systems running on ARM processors and a CentOS 7 system
running an Intel i7 processor.  It has also been tested
and a Marvel ARMADA 388 processor running Armbian 5.9.1.

The program is written in Python 3 and require that the
following modules be installed:

## Installation
* Install and configure a MQTT server or use a public service.
* Install the Python MQTT Client
	* `pip install psutil`
	* `pip install paho-mqtt`
	* `pip install mdstat`
* Copy the program to the desired directories or run `makepkg` and
install with **pacman**.
* Modify the **system_monitor** configuation file and place in
`/etc/sensor/system_monitor.conf`
* Enable the services:
	* `systemctl enable system_monitor`

## Performance
While not as high performance as `collectd` the actual data collection
takes about 80 milliseconds on an original Raspberry Pi B.  Not an
excessive amount of overhead with an collection interval of 15 seconds.
On an Intel i7 processor the collection takes about 3 milliseconds. 
## Things To Do
* Change running user to non-root.
* Support MQTT authentication
* Support secure MQTT connections
* Better documentation.
* Publish the data from each data source into its own MQTT message.
* Selectively control which data sources are to be published via
the configuration file.
