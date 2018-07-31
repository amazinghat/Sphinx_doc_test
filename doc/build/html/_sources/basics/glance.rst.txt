Glance image services include discovering, registering, and retrieving virtual machine (VM) images. Glance has a RESTful API that allows querying of VM image metadata as well as retrieval of the actual image.

How to use
----------

- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.

::

 $ openstack help image create
 usage: openstack image create [-h] [-f {json,shell,table,value,yaml}]
                               [-c COLUMN] [--max-width <integer>]
                               [--fit-width] [--print-empty] [--noindent]
                               [--prefix PREFIX] [--id <id>]
                               [--container-format <container-format>]
                               [--disk-format <disk-format>]
 ...
                         Image disk format. The supported options are: ami,
                         ari, aki, vhd, vmdk, raw, qcow2, vhdx, vdi, iso,
                         ploop. The default format is: raw
   --min-disk <disk-gb>  Minimum disk size needed to boot image, in gigabytes
   --min-ram <ram-mb>    Minimum RAM size needed to boot image, in megabytes
   --file <file>         Upload image from local file
   --volume <volume>     Create image from a volume

Custom images requirements
--------------------------

- Disk partitions and resize root partition on boot (cloud-init)
- No hard-coded MAC address information
- Ensure ssh server runs
- Disable firewall
- Access instance by using ssh public key (cloud-init)
- Process user data and other metadata (cloud-init)
- Ensure image writes boot log to console

`Detailed requiremetns <https://docs.openstack.org/image-guide/openstack-images.html>`_

Ready images
------------

- CentOS 6 - http://cloud.centos.org/centos/6/images/
- CentOS 7 - http://cloud.centos.org/centos/7/images/
- Ubuntu - http://cloud-images.ubuntu.com/trusty/current/
- Red Hat 6&7 – requires access to RHN.

Resources
---------

- GlanceClient: `Glance CLI <https://docs.openstack.org/python-glanceclient/latest/cli/index.html>`_

