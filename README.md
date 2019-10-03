# nvf_telco_notes

Hugepages: 80GB of RAM allocated to HugePages.
Enabling PCI passthrough to enable SR-IOV on intel card.

GRUB PARAMETERS need to be reconfigured:

```
$GRUB_CMD_LINE_DEFAULT="intel_iommu=on hugepages=40000 transparent_hugepage=never default_hugepagesz=2M hugepagesz=2M"
```
Apply grub changes:

```
host01$ sudo update-grub2
host01$ sudo reboot
```

```
 cat /proc/meminfo | grep Huge
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
HugePages_Total:   40000
HugePages_Free:    40000
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB

