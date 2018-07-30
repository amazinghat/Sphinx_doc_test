Neutron is an OpenStack project to provide “network connectivity as a service” between interface devices (e.g., vNICs) managed by other OpenStack services (e.g., nova).

How to use
----------

- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.

::

 $ openstack help network create
 usage: openstack network create [-h] [-f {json,shell,table,value,yaml}]
                                 [-c COLUMN] [--max-width <integer>]
                                 [--fit-width] [--print-empty] [--noindent]
                                 [--prefix PREFIX] [--share | --no-share]
                                 [--enable | --disable] [--project <project>]
                                 [--description <description>]
                                 [--project-domain <project-domain>]
                                 [--availability-zone-hint <availability-zone>]
                                 [--enable-port-security | --disable-port-security]
 ...
 
 Create new network
 
 positional arguments:
   <name>                New network name
 
 optional arguments:
   -h, --help            show this help message and exit
   --share               Share the network between projects
   --no-share            Do not share the network between projects
   --enable              Enable network (default)
   --disable             Disable network
   --project <project>   Owner's project (name or ID)
   --description <description>

Resources
---------

`CLI Reference <https://docs.openstack.org/neutron/queens/cli/index.html>`_
`Neutron API Reference <https://developer.openstack.org/api-ref/network/>`_

