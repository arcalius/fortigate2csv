# FortiGate to CSV Converter

FortiGate web UI has no easy way to export a CSV, unless you also use FortiManager, so this script can be used to fetch JSON data over the REST API and export it as CSV.

Some common objects are included, but it should be easy to modify and extend to your requirements.

Forked from danwalkeruk to suit my environments with additional items(users, group & fortitoken).

## Usage

Command line arguments

* `-f` - Firewall IP/FQDN
* `-p` - Firewall console port *(optional)*. Defaults to 443 if not set
* `-u` - Username
* `-v` - VDOM
* `-i` - Items *(interface, policy, snat, address, service, dnat, pool, users, fortitoken, groups)*
* `-o` - CSV Outfile *(optional)*

### Example

```bash

#python3 fortigate2csv.py -f 1.2.3.4 -p 8443 -u dan -v root -i interface -o interfaces.csv
Connecting to 1.2.3.4 (root) as dan
Received CSRF token
Successfully logged in as dan
Fetching data...
Logging out of firewall
Saving to interfaces.csv
Done!
```

Output:

```
name,alias,description,type,is_vdom_link,is_system_interface,is_vlan,status,role,ipv4_addresses,vlan_interface,vlan_id,mac_address,visibility,comments
any,,,,,,,,,,,,,,
mgmt2,FMG,FMG,physical,,True,,up,undefined,172.17.10.22/24,,,00:09:0f:09:4d:01,,
port1,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:02,,
port2,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:03,,
port3,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:04,,
port4,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:05,,
port5,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:06,,
port6,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:07,,
port7,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:08,,
port8,,,physical,,True,,up,undefined,,,,00:09:0f:09:4d:09,,
...
```
