# snmp-switch

## Description

snmp-switch is a simple command line utility to pull information out of snmp
capable network switches. At the moment it returns the name, description and
uptime along with per port information including status, speed and octets in and
out.

## Usage

snmp-switch &lt;host&gt;

## Todo

Error handling could be better. The pysnmp library throws exceptions however the
get commands return errors as variables in a 4 element tuple. Weird.

Return switching table. With a MAC-to-hostname lookup table
could also show hosts reachable for each port.

Use 64 bit counters if available. Not sure how common these are. The HP 1810-24G
has them.

## Requirements

* Python 3 - http://www.python.org/
* pysnmp - https://pypi.python.org/pypi/pysnmp
* pysnmp-mibs - https://pypi.python.org/pypi/pysnmp-mibs

