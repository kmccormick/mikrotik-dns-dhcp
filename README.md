mikrotik-dns-dhcp
=================

Tool to syncronise DHCP lease names with DNS hostnames on Mikrotik routers.

* dns-dhcp-onlease - Primary script, fires from the lease-script event on the
  DHCP server. Adds DNS records for the current DHCP lease, and cleans up
  when the lease goes away.
* dns-dhcp-add - backup, because sometimes the onlease one isn't perfect.
  Makes sure all current DHCP leases have DNS names.
* dns-dhcp-gc - backup, because sometimes the onlease one isn't perfect.
  Makes sure all DNS names with the "special" TTL have valid DHCP leases.
* mikrotik-dns-dhcp - the original, legacy script


Each script has 2 local variables that must be kept in sync across all 3
scripts:
* ZONE - the DNS zone to be appended to the DHCP host-name
* TTL - a unique TTL which will be used exclusively for these scripts
