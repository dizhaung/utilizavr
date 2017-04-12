Utilizavr
=========

Let's say you want to check interface utilization of a switch port to which
your PC connected. What you gonna do? Spin up a full flavoured NMS like
Cacti or Zabbix? For just one interface? Or may be you want to do some
reporting about traffic go high/low. That utility just for that.

Utilizavr poll an interface for _ifHCXOctets_, compare it to last run
and show you an estimate of interface utilization and percent usage. To
store last run numbers it create files for every pair 'host-interface'
in __tempdir__ (which you can set explicitly, otherwise ~/.utlizavr will be
used). Script gona write log into /tmp/utilizavr.log.

__NOTE__ On first run script can't count difference, obviously, because it
hasn't previous values.

__USAGE__ _utilizavr_ HOST IFINDEX COMMUNITY [OPTIONS]

You can provide options such:
    * -d, --dir         directory to store files in (it will use 
                            ~/.utilizavr by default)
    * -t, --threshold   throughput limit of that interface (it will query
                            interface with ifHighSpeed by default)

__IMPORTANT__ That screept works only with version __2c__ of SNMP.

__DEPENDENCIES__ You will need that apps to use utilizavr:
    * bash
    * tee
    * mkdir
    * snmpget
    * date
    * awk
    * bc

Spot a typo? Have a suggestion to made script better? Or you think my code
is shit? Feel free to contact me at yman at protonmail dot ch. Or open an
issue righ here on GitHub.
