Cinder - block storage service
------------------------------

Cinder is an OpenStack project to provide “block storage as a service”.

How to use
----------

- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.

::

 $ openstack help volume create
 usage: openstack volume create [-h] [-f {json,shell,table,value,yaml}]
                                [-c COLUMN] [--max-width <integer>]
                                [--fit-width] [--print-empty] [--noindent]
                                [--prefix PREFIX] [--size <size>]
                                [--type <volume-type>]
                                [--image <image> | --snapshot <snapshot> | --source <volume> | --source-replicated <replicated-volume>]
                                [--description <description>] [--user <user>]
                                [--project <project>]
                                [--availability-zone <availability-zone>]
                                [--consistency-group consistency-group>]
                                [--property <key=value>] [--hint <key=value>]
                                [--multi-attach] [--bootable | --non-bootable]
                                [--read-only | --read-write]
                                <name>
 
 
 Create new volume
 
 positional arguments:
   <name>                Volume name
 
 optional arguments:
   -h, --help            show this help message and exit
   --size <size>         Volume size in GB (Required unless --snapshot or
                         --source or --source-replicated is specified)
   --type <volume-type>  Set the type of volume
   --image <image>       Use <image> as source of volume (name or ID)
   --snapshot <snapshot>
                         Use <snapshot> as source of volume (name or ID)
   --source <volume>     Volume to clone (name or ID)

Resources
---------
| `API Reference <https://developer.openstack.org/api-ref/block-storage/>`_
| `CLI Docs <https://docs.openstack.org/cinder/latest/cli/index.html>`_

