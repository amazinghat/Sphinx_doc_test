- Instancja = VM
- Block storage/Persistent storage = volumen
- Ephemeral storage = “/dev/sda”
- Flavor = rozmiar VM
- “Snapshot” = Image
- Floating IP = NAT
- Sieć zewnętrzna = sieć routowalna w CDC = DMZ

More:

- Ephemeral storage is allocated for an instance and is deleted when the instance is deleted. The Compute service manages ephemeral storage and by default.

- Persistent storage exists outside all instances. Two types of persistent storage are provided:

   + The Block Storage service (cinder) that can use LVM or Ceph RBD as the storage back end.

   + The Image service (glance) that can use the Object Storage service (swift) or Ceph RBD as the storage back end.
