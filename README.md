# [bananaPi CM4](https://www.aliexpress.com/item/1005005115415086.html) on [Turing Pi2](https://turingpi.com/product/turing-pi-2/)

**Warning**  testing is still undergoing, content of this page may change

``(March 2023)`` Because of global shortage, I had no other choice but to order [4 x BPI-CM4](https://www.aliexpress.com/item/1005005115415086.html) in place of raspberry CM4.

 :expressionless: :expressionless: Element14/Farnell is planning for availability arround february/march 2024 :expressionless: :expressionless:

## Resources

author | links |
 --- | --- |
SINOVOIP | https://wiki.banana-pi.org/Banana_Pi_BPI-CM4
|| https://wiki.banana-pi.org/Getting_Started_with_CM4
|| https://www.amlogicusbburningtool.com/
Bret's review | https://bret.dk/banana-pi-cm4-review/
Jeff's Geerling review | https://github.com/geerlingguy/sbc-reviews/issues/11

## What's working

Component/feature |Tested | Working  | Remark
---|---|---| ---
BMC power | :heavy_check_mark:|:heavy_check_mark: | 
Network I/O (x nodes) | :heavy_check_mark: | :heavy_check_mark: | :warning: with ``2023-01-12-debian-10-buster-bpi-cm4-aarch64-sd-emmc.img``, same mac address is used on nodes. :heavy_check_mark: [official armbian image](https://www.armbian.com/bananapicm4io/) works fine.
HDMI ouput| :heavy_check_mark: |:heavy_check_mark:| main HDMI on node 1 with [same HDMI Circuit Switch configuration](https://help.turingpi.com/hc/en-us/articles/8685766680477-Specifications-and-I-O-Ports#f231ec3c) as rapsberry PI CM4
Boot from SD card| :heavy_check_mark: |:heavy_check_mark:| write img on SDcard then insert in the turingPI CM4 adapator
Boot from EMMC | :heavy_check_mark:	 |:heavy_check_mark: | boot from SD card then `dd` your img to ``/dev/mmcblk0`` [see this](https://wiki.banana-pi.org/Getting_Started_with_CM4#Install_Image_to_EMMC)
USB OTG (host) | :heavy_check_mark: |:grey_question: | (node1) I  didn't get USB host to work yet.
USB OTG (device) | :heavy_check_mark: |:grey_question: | (node1) ``GX-CHIP`` peripheral will appear on windows 10, install [AML burning tool suite](https://download.banana-pi.dev/d/3ebbfa04265d4dddb81b/files/?p=%2FTools%2Fimage_download_tools%2Faml_usb_burning_tool_V2_setup_v2.2.3.3.zip) to get the driver.
OS ``armbian bookworm`` | :heavy_check_mark:|:heavy_check_mark: | Testing [``Armbian 23.5 Bookworm minimal``](https://redirect.armbian.com/bananapicm4io/Bookworm_current_minimal). ssh working user/pwd ``root/1234`` then create ``pi/bananapi``
OS ``debian 10`` | :heavy_check_mark:|:heavy_check_mark: | Testing ``2023-01-12-debian-10-buster-bpi-cm4-aarch64-sd-emmc.img``. ssh working user/pwd ``pi/bananapi`` then ``su -``
OS ``dietPi`` | :heavy_check_mark:|:x: | DietPi's transformation script fails on [official armbian image](https://www.armbian.com/bananapicm4io/)

:x: ko / :heavy_check_mark: ok / :grey_question: todo or more testing required

## Software

Armbian community has added support for bananapi CM4, currently valid since Armbian 23.5.

See https://www.armbian.com/bananapicm4io/


## Ansible playbooks

Some helpfull playbook for your bpi-cm4

### [bpi-cm4-armbian-setup.yml](ansible/bpi-cm4-armbian-setup.yml)

* enable/disable wifi support (can prevent board from heating up)
* enable/disable ramlog
* add sudo permission for daily user

#### Avallable variables
```yaml
wifi_enable: true     # enable wifi or not
ramlog_enable: true  # enable ramlog or not
everyday_user: pi     # user for everyday use, usually pi
```

### [bpi-cm4-emmc-erase.yml](ansible/bpi-cm4-emmc-erase.yml)

* erase local ``EMMC`` with ``mmc``(default) command or ``dd``

#### Avallable variables

```yaml
emmc_disk: mmcblk1        # until a better storage selection method is found manual specification is used
dd_block_count: 14910     # size of the emmc in block, bpi-cm4 v1.à release is 16Gb only
brute_force_erase: false  # dd method's used when 'mmc erase' doesn't exist,"mmc"'s faster but not necessarily available on your distro
all_partitions: false     # do wipe all emmc partitions?
```