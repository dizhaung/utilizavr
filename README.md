# Utilizavr

Let's say you want to check interface utilization of a switch port to which
your PC connected. What you gonna do? Spin up a full flavoured NMS like
Cacti or Zabbix? For just one interface? Or may be you want to do some
reporting about traffic go high/low. That utility just for that.

Utilizavr poll an interface for _ifHCXOctets_, compare it to last run
and show you an estimate of interface utilization and percent usage. To
store last run numbers it create files for every pair 'host-interface'
in __tempdir__ (which you can set explicitly, otherwise ~/.utlizavr will be
used). Script gonna write log into /tmp/utilizavr.log.

__NOTE__ On first run script can't count difference, obviously, because it
hasn't previous values.

## USAGE 

_utilizavr_ HOST IFINDEX COMMUNITY [OPTIONS]

You can provide options such:
*   -d, --dir         directory to store files in (it will use 
                            ~/.utilizavr by default)
*   -t, --threshold   throughput limit of that interface (it will query
                            interface with ifHighSpeed by default)

__IMPORTANT__ That script works only with version __2c__ of SNMP.

## DEPENDENCIES 
You will need that apps to use utilizavr:
*   bash
*   tee
*   mkdir
*   snmpget
*   date
*   awk
*   bc
*   getopt
*   shunit2 __(for testing only)__

## TESTS
For running tests you need to provide correct path to shunit2 in last line 
of *unit_tests* file. You also may want to change temporary directory used 
by tests. For that purpose change _TMPDIR_ variable in _oneTimeSetUp_ 
function. But tests gonna delete that folder after run anyway.

## PS
That script is inspired in some way by 
[Check SNMP Cisco Traffic](https://exchange.nagios.org/directory/Plugins/Hardware/Network-Gear/Cisco/Check-SNMP-Cisco-Traffic/details)
plugin for Nagios by Michael Boehm, but I like to try to do somewhat similar
by myself.

Spot a typo? Have a suggestion to made script better? Or you think my code
is shit? Feel free to contact me at yman at protonmail dot ch. Or open an
issue right here on GitHub.

## AUTHOR
Written by Yakov Shiryaev (yman) in 2017.
