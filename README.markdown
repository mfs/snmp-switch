# snmp-switch

## Description

snmp-switch is a simple command line utility to pull information out of snmp
capable network switches. At the moment it returns the name, description and
uptime along with per port information including status, speed, octets in and
out and MACs reachable on each port.

## Usage

snmp-switch &lt;host&gt;

## Example Output

    mfs@workstation $ ./snmp-switch 192.168.0.128
    Name        : J9803A
    Description : HP 1810-24G, PL.1.5, eCos-3.0, 1_12_8-customized-h
    Uptime      : 10 days, 6:26:23.310000

    Description               Status  Speed  Octs In (64)  Octs Out (64)  Hosts
    ---------------------------------------------------------------------------------------
    Port:  1 Gigabit - Level  up       100M           16G             2G  00:1a:11:ff:94:1a
    Port:  2 Gigabit - Level  up         1G           51G            13G  00:1a:11:ef:1f:59
    Port:  3 Gigabit - Level  up         1G           21M            76M  00:1a:11:9a:24:8d
    Port:  4 Gigabit - Level  down        0             0              0
    Port:  5 Gigabit - Level  down        0             0              0
    Port:  6 Gigabit - Level  down        0             0              0
    Port:  7 Gigabit - Level  down        0             0              0
    Port:  8 Gigabit - Level  down        0             0              0
    Port:  9 Gigabit - Level  down        0             0              0
    Port: 10 Gigabit - Level  down        0             0              0
    Port: 11 Gigabit - Level  down        0             0              0
    Port: 12 Gigabit - Level  down        0             0              0
    Port: 13 Gigabit - Level  up         1G          535M            29G  00:1a:11:00:1e:64
    Port: 14 Gigabit - Level  down        0          864k             4M
    Port: 15 Gigabit - Level  up       100M          814M            24G  00:1a:11:5c:3a:0b
    Port: 16 Gigabit - Level  down        0             0              0
    Port: 17 Gigabit - Level  down        0             0              0
    Port: 18 Gigabit - Level  down        0             0              0
    Port: 19 Gigabit - Level  down        0             0              0
    Port: 20 Gigabit - Level  down        0             0              0
    Port: 21 Gigabit - Level  down        0             0              0
    Port: 22 Gigabit - Level  down        0             0              0
    Port: 23 Gigabit - Level  down        0          205k             5M
    Port: 24 Gigabit - Level  down        0           26M            67M
    Port: 25 SFP - Level      down        0             0              0
    Port: 26 SFP - Level      down        0             0              0
    IP Interface              up         1G           13M            15M

## Todo

Error handling could be better. The pysnmp library throws exceptions however the
get commands return errors as variables in a 4 element tuple. Weird.

Clean up code.

Map MACs to hostname via lookup table.

## Requirements

* Python 3 - http://www.python.org/
* pysnmp - https://pypi.python.org/pypi/pysnmp
* pysnmp-mibs - https://pypi.python.org/pypi/pysnmp-mibs

