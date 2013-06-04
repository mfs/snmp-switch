# snmp-switch

## Description

snmp-switch is a simple command line utility to pull information out of snmp
capable network switches. At the moment it returns the name, description and
uptime along with per port information including status, speed, octets in and
out and hostnames/MACs reachable on each port. It also returns vlan information.

## Usage

    mfs@workstation $ ./snmp-switch -h
    usage: snmp-switch [-h] [-c CONFIG] host

    query a network switch using snmp.

    positional arguments:
      host                  host to query.

    optional arguments:
      -h, --help            show this help message and exit
      -c CONFIG, --config CONFIG
                            location of config file.

## Example Output

    mfs@workstation $ ./snmp-switch 192.168.0.128
    Name        : J9803A
    Location    :
    Description : HP 1810-24G, PL.1.5, eCos-3.0, 1_12_8-customized-h
    Uptime      : 38 days, 5:17:08.630000

    Name          Status  Speed  Octs In (64)  Octs Out (64)  Hosts
    ---------------------------------------------------------------------------
    Port  1       up       100M        85.86G         21.84G  client1.local
    Port  2       up       100M         1.49T         35.48G  client2.local
    Port  3       up         1G        60.84G          1.43T  server1.local
    Port  4       down        0          0.00           0.00
    Port  5       down        0          0.00           0.00
    Port  6       down        0          0.00           0.00
    Port  7       down        0          0.00           0.00
    Port  8       down        0          0.00           0.00
    Port  9       down        0          0.00           0.00
    Port 10       down        0          0.00           0.00
    Port 11       down        0          0.00           0.00
    Port 12       down        0          0.00           0.00
    Port 13       up         1G         4.45G         96.05G  client3.local
    Port 14       down        0         5.69M         44.32M
    Port 15       up       100M         1.73G         51.06G  00:1a:11:5c:3a:0b
    Port 16       down        0        81.53M        334.37M
    Port 17       down        0          0.00           0.00
    Port 18       down        0          0.00           0.00
    Port 19       down        0          0.00           0.00
    Port 20       down        0          0.00           0.00
    Port 21       down        0          0.00           0.00
    Port 22       down        0          0.00           0.00
    Port 23       down        0       205.62k          5.56M
    Port 24       down        0        26.08M         67.91M
    Port 25       down        0          0.00           0.00
    Port 26       down        0          0.00           0.00
    IP Interface  up         1G        33.18M         37.10M

    Max VLANs : 4096    VLANs : 2

    ID   Name     1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26
    -----------------------------------------------------------------------------------------------------------
    1    default  U  U  U  U  U  U  U  U  U   U   U   U   U   U   U   U   U   U   U   U   U   U   U   U   U   U
    500  storage  T  E  E  E  E  E  E  E  E   E   E   E   E   E   E   E   E   E   E   E   E   E   E   T   E   E


## Todo

Error handling could be better. The pysnmp library throws exceptions however the
get commands return errors as variables in a 4 element tuple. Weird.

Should be able to specify a hostnames per port that always appear in the list of
hosts, even if the host is down.

Clean up code.

## Configuration

Default location for configuration file is ~/.snmp-switch.conf. At the moment
this file just contains a mapping of MACs to hostnames:

    00:1a:11:ff:94:1a client1.local
    00:1a:11:ef:1f:59 client2.local
    00:1a:11:9a:24:8d server1.local
    00:1a:11:00:1e:64 client3.local

## Requirements

* Python 3 - http://www.python.org/
* pysnmp - https://pypi.python.org/pypi/pysnmp
* pysnmp-mibs - https://pypi.python.org/pypi/pysnmp-mibs

