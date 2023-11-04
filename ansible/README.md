# Ansible playbooks

Some helpfull playbooks for your bpi-cm4

## [bpi-cm4-armbian-setup.yml](ansible/bpi-cm4-armbian-setup.yml)

* enable/disable wifi physical support (can prevent board from heating up)
* enable/disable ramlog/zram
* add sudo permission for daily user

#### Avallable variables
```yaml
disable_wifi: true     # enable wifi or not
ramlog_enable: true  # enable ramlog or not
everyday_user: pi     # user for everyday use, usually pi
```

### Example
```bash
# disable wifi module
ansible-playbook bpi-cm4-armbian-setup.yml -e "wifi_enable=false"
```

### [bpi-cm4-emmc-erase.yml](ansible/bpi-cm4-emmc-erase.yml)

* erase local ``EMMC`` with ``mmc``(default) command or ``dd``

### Avallable variables

```yaml
emmc_disk: mmcblk1        # until a better storage selection method is found manual specification is used
dd_block_count: 14910     # size of the emmc in block, bpi-cm4 v1.à release is 16Gb only
brute_force_erase: false  # dd method's used when 'mmc erase' doesn't exist,"mmc"'s faster but not necessarily available on your distro
all_partitions: false     # do wipe all emmc partitions?
```

### Example

```bash
# erase my_host EMMC
ansible-playbook bpi-cm4-emmc-erase.yml -l my_host
```
