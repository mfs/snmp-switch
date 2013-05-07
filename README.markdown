# snmp-switch

## Description

snmp-switch is a simple command line utility to pull information out of snmp
capable network switches. At the moment it returns the name, description and
uptime along with per port information including status, speed and octets in and
out.

## Usage

snmp-switch &lt;host&gt;

## Example Output

    mfs@workstation $ ./snmp-switch 192.168.0.128
    Name        : J9803A
    Description : HP 1810-24G, PL.1.5, eCos-3.0, 1_12_8-customized-h
    Uptime      : 10 days, 6:26:23.310000

    Description               Status  Speed  Octs In (64)  Octs Out (64)
    --------------------------------------------------------------------
    Port:  1 Gigabit - Level  up       100M           16G             2G
    Port:  2 Gigabit - Level  up         1G           51G            13G
    Port:  3 Gigabit - Level  up         1G           21M            76M
    Port:  4 Gigabit - Level  down        0             0              0
    Port:  5 Gigabit - Level  down        0             0              0
    Port:  6 Gigabit - Level  down        0             0              0
    Port:  7 Gigabit - Level  down        0             0              0
    Port:  8 Gigabit - Level  down        0             0              0
    Port:  9 Gigabit - Level  down        0             0              0
    Port: 10 Gigabit - Level  down        0             0              0
    Port: 11 Gigabit - Level  down        0             0              0
    Port: 12 Gigabit - Level  down        0             0              0
    Port: 13 Gigabit - Level  up         1G          535M            29G
    Port: 14 Gigabit - Level  down        0          864k             4M
    Port: 15 Gigabit - Level  up       100M          814M            24G
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

Return switching table. With a MAC-to-hostname lookup table
could also show hosts reachable for each port.

## Requirements

* Python 3 - http://www.python.org/
* pysnmp - https://pypi.python.org/pypi/pysnmp
* pysnmp-mibs - https://pypi.python.org/pypi/pysnmp-mibs

