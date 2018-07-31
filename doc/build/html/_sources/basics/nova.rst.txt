Nova is the OpenStack project that provides a way to provision compute instances (aka virtual servers).

It requires the following additional OpenStack services for basic function:

- Keystone: This provides identity and authentication for all OpenStack services.
- Repozytorium obrazów - Glance: This provides the compute image repository. All compute instances launch from glance images.
- Neutron: This is responsible for provisioning the virtual or physical networks that compute instances connect to on boot.

How to use
----------

- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.

::

 $ openstack help server create
 usage: openstack server create [-h] [-f {json,shell,table,value,yaml}]
                                [-c COLUMN] [--max-width <integer>]
                                [--fit-width] [--print-empty] [--noindent]
                                [--prefix PREFIX]
                                (--image <image> | --volume <volume>) --flavor
                                <flavor> [--security-group <security-group>]
 ...
 
 Create a new server
 positional arguments:
   <server-name>         New server name
 optional arguments:
   -h, --help            show this help message and exit
   --image <image>       Create server boot disk from this image (name or ID)
   --volume <volume>     Create server using this volume as the boot disk (name
                         or ID).
                         This option automatically creates a block device
                         mapping with a boot index of 0. On many hypervisors
                         (libvirt/kvm for example) this will be device vda. Do
                         not create a duplicate mapping using --block-device-
                         mapping for this volume.
   --flavor <flavor>     Create server with this flavor (name or ID)
   --security-group <security-group>


- Nova Client: For some very advanced features (or administrative commands) of nova you may need to use nova client. It is still supported, but the openstack cli is recommended.

API resources
-------------

- `Compute API Guide <https://developer.openstack.org/api-guide/compute/>`_: The concept guide for the API. This helps lay out the concepts behind the API to make consuming the API reference easier.
- `Compute API Reference <http://developer.openstack.org/api-ref/compute/>`_: The complete reference for the compute API, including all methods and request / response parameters and their meaning.

More resources
--------------

- `Reference Material <https://docs.openstack.org/nova/latest/#reference-material>`_
- `OpenStackClient Docs <https://docs.openstack.org/python-openstackclient/latest/>`_
- `NovaClient Docs <https://docs.openstack.org/python-novaclient/latest/user/shell.html>`_

