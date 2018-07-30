# Scheduling
There are ways to affect cloud's scheduling process to fullfil various requirements (eg. availability or performance )

## Server groups

Server groups define collections of VM's so that the entire collection can be given specific properties. For example, the policy of a server group may specify that VM's in this group should not be placed on the same physical hardware due to availability requirements.

Server groups are project-specific and cannot be shared across projects.

### Create server group
Use CLI:

```
$ openstack server group create -h
usage: openstack server group create [-h] [-f {json,shell,table,value,yaml}]
                                     [-c COLUMN] [--max-width <integer>]
                                     [--fit-width] [--print-empty]
                                     [--noindent] [--prefix PREFIX]
                                     [--policy <policy>]
                                     <name>

Create a new server group.

positional arguments:
  <name>                New server group name

optional arguments:
  -h, --help            show this help message and exit
  --policy <policy>     Add a policy to <name> ('affinity' or 'anti-affinity',
                        default to 'affinity')
```

- ```affinity``` -> same host

```
$ openstack server group create \
> --policy affinity \
> scaleup_app_siteA
+----------+--------------------------------------+
| Field    | Value                                |
+----------+--------------------------------------+
| id       | 05cab439-7737-4357-b27a-91e9e14690f4 |
| members  |                                      |
| name     | scaleup_app_siteA                    |
| policies | affinity                             |
+----------+--------------------------------------+
```

- ```anti-affinity``` -> different host

```
$ openstack server group create \
> --policy anti-affinity \
> web_servers 
+----------+--------------------------------------+
| Field    | Value                                |
+----------+--------------------------------------+
| id       | 449c76ea-c009-4fe5-af04-89d73cfb0c0a |
| members  |                                      |
| name     | web_servers                          |
| policies | anti-affinity                        |
+----------+--------------------------------------+
```