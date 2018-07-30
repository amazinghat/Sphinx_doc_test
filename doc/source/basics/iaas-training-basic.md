IaaS Enterprise Platform
===
## Basics

###### Krzysztof Szałkowski
###### Szymon Rymarz
###### Piotr Kopeć
---
Agenda
===
1. [Nazewnictwo](./basics/naming.md)
2. [Przegląd GUI - Horizon](./basics/horizon.md)
3. [Repozytorium obrazów - Glance](./basics/glance.md)
4. [Compute - Nova](./basics/nova.md)
5. [Sieci - Neutron](./basics/neutron.md)
6. [Block storage - Cinder](./basics/cinder.md)
---

# Podstawowe nazewnictwo
- Instancja = VM
- Block storage/Persistent storage = volumen
- Ephemeral storage = “/dev/sda”
- Flavor = rozmiar VM
- “Snapshot” = Image
- Floating IP = NAT
- Sieć zewnętrzna = sieć routowalna w CDC = DMZ
---
# More:
- Ephemeral storage is allocated for an instance and is deleted when the instance is deleted. The Compute service manages ephemeral storage and by default.
- Persistent storage exists outside all instances. Two types of persistent storage are provided:
- The Block Storage service (cinder) that can use LVM or Ceph RBD as the storage back end.
- The Image service (glance) that can use the Object Storage service (swift) or Ceph RBD as the storage back end.
---

Horizon
===
Web-based GUI.

 https://cecp.cadc.pl - https://cecp.cadc.pl 
##### Resources
 Docs - https://docs.openstack.org/horizon/latest/user/index.html 

---
# Glance - image service
Glance image services include discovering, registering, and retrieving virtual machine (VM) images. Glance has a RESTful API that allows querying of VM image metadata as well as retrieval of the actual image.

---
## How to use
- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.
---
## CLI
```
$ openstack help image create
usage: openstack image create [-h] [-f {json,shell,table,value,yaml}]
                              [-c COLUMN] [--max-width <integer>]
                              [--fit-width] [--print-empty] [--noindent]
                              [--prefix PREFIX] [--id <id>]
                              [--container-format <container-format>]
                              [--disk-format <disk-format>]
...
```
---
## Custom images requirements
- Disk partitions and resize root partition on boot (cloud-init)
- No hard-coded MAC address information
- Ensure ssh server runs
- Disable firewall
- Access instance by using ssh public key (cloud-init)
- Process user data and other metadata (cloud-init)
- Ensure image writes boot log to console
 Detailed requiremetns - https://docs.openstack.org/image-guide/openstack-images.html 
---
## Ready images
- CentOS 6 - http://cloud.centos.org/centos/6/images/
- CentOS 7 - http://cloud.centos.org/centos/7/images/
- Ubuntu - http://cloud-images.ubuntu.com/trusty/current/
- Red Hat 6&7 – requires access to RHN.
---
## Resources
- GlanceClient:  Docs - https://docs.openstack.org/python-glanceclient/latest/cli/index.html 
---
# Nova - Compute Service
Nova is the OpenStack project that provides a way to provision compute instances (aka virtual servers).

---
# Nova
It requires the following additional OpenStack services for basic function:

- Keystone: This provides identity and authentication for all OpenStack services.
- [Glance](./glance.md): This provides the compute image repository. All compute instances launch from glance images.
- [Neutron](./neutron.md): This is responsible for provisioning the virtual or physical networks that compute instances connect to on boot.
---
## How to use
- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.
---
## CLI

```
$ openstack help server create
usage: openstack server create [-h] [-f {json,shell,table,value,yaml}]
                               [-c COLUMN] [--max-width <integer>]
                               [--fit-width] [--print-empty] [--noindent]
                               [--prefix PREFIX]
                               (--image <image> | --volume <volume>) --flavor
                               <flavor> [--security-group <security-group>]
...
```
---
# Nova client
- Nova Client: For some very advanced features (or administrative commands) of nova you may need to use nova client. It is still supported, but *the openstack cli is recommended*.
```
$ pip install python-novaclient
$ nova --help
```
---
## API resources
-  Compute API Guide - https://developer.openstack.org/api-guide/compute/ : The concept guide for the API. This helps lay out the concepts behind the API to make consuming the API reference easier.
-  Compute API Reference - http://developer.openstack.org/api-ref/compute/ : The complete reference for the compute API, including all methods and request / response parameters and their meaning.
---
## More resources
-  Reference Material - https://docs.openstack.org/nova/latest/#reference-material 
-  OpenStackClient Docs - https://docs.openstack.org/python-openstackclient/latest/ 
-  NovaClient Docs - https://docs.openstack.org/python-novaclient/latest/user/shell.html 
---
# Neutron - network service
Neutron is an OpenStack project to provide “network connectivity as a service” between interface devices (e.g., vNICs) managed by other OpenStack services (e.g., nova).

---
## How to use
- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.
---
## CLI
```
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
```
---
## Resources
 CLI Reference - https://docs.openstack.org/neutron/queens/cli/index.html 
 Neutron API Reference - https://developer.openstack.org/api-ref/network/ 

---
# Cinder - block storage service
Cinder is an OpenStack project to provide “block storage as a service”.

---
## How to use
- Horizon: The official web ui for the OpenStack Project.
- OpenStack Client: The official CLI for OpenStack Projects. You should use this as your CLI for most things, it includes not just nova commands but also commands for most of the projects in OpenStack.
---
## CLI
```
$ openstack help volume create
usage: openstack volume create [-h] [-f {json,shell,table,value,yaml}]
                               [-c COLUMN] [--max-width <integer>]
                               [--fit-width] [--print-empty] [--noindent]
                               [--prefix PREFIX] [--size <size>]
                               [--type <volume-type>]
                               [--image <image> | --snapshot <snapshot> | --source <volume> | --source-replicated <replicated-volume>]
                               [--description <description>] [--user <user>]
```
---
## Resources
 API Reference - https://developer.openstack.org/api-ref/block-storage/ 
 CLI Docs - https://docs.openstack.org/cinder/latest/cli/index.html 

