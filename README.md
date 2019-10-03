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
