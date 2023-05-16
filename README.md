# [bananaPi CM4](https://www.aliexpress.com/item/1005005115415086.html) on [Turing Pi2](https://turingpi.com/product/turing-pi-2/)

:warning: :warning: :warning:  testing is still undergoing, content of this page may change :warning: :warning: :warning:

``(March 2023)`` Because of global shortage, I had no other choice but to order [4 x BPI-CM4](https://www.aliexpress.com/item/1005005115415086.html) in place of raspberry CM4.

 :expressionless: :expressionless: Element14/Farnell is planning for availability arround february/march 2024 :expressionless: :expressionless:


## Resources

### SINOVOIP links
https://wiki.banana-pi.org/Banana_Pi_BPI-CM4

https://wiki.banana-pi.org/Getting_Started_with_CM4

https://www.amlogicusbburningtool.com/

### Bret's review
https://bret.dk/banana-pi-cm4-review/

### Jeff's Geerling review
https://github.com/geerlingguy/sbc-reviews/issues/11


## What's working

Component/feature |Tested | Working  | Remark
---|---|---| --
BMC power | :heavy_check_mark:|:heavy_check_mark: | 
Network I/O 1 node only| :heavy_check_mark:|:heavy_check_mark: | dhcp client correctly getting IP
Network I/O multiple nodes | :heavy_check_mark: | :x: | :warning: Beware when using ``2023-01-12-debian-10-buster-bpi-cm4-aarch64-sd-emmc.img``, same mac is used on  nodes. :heavy_check_mark:``Armbian_23.02.0-trunk_Bananapicm4_bullseye_current_6.0.14_minimal.img`` works fine.
HDMI ouput| :heavy_check_mark: |:heavy_check_mark:| main HDMI on node 1 with [same HDMI Circuit Switch configuration](https://help.turingpi.com/hc/en-us/articles/8685766680477-Specifications-and-I-O-Ports#f231ec3c) as rapsberry PI CM4
Boot from SD card| :heavy_check_mark: |:heavy_check_mark:| write img on SDcard then insert in the turingPI CM4 adapator
Boot from EMMC | :heavy_check_mark:	 |:heavy_check_mark: | boot from SD card then `dd` your img to ``/dev/mmcblk0`` [see this](https://wiki.banana-pi.org/Getting_Started_with_CM4#Install_Image_to_EMMC)
USB OTG (host) | :heavy_check_mark: |:grey_question: | (node1) I  didn't get USB host to work yet.
USB OTG (device) | :heavy_check_mark: |:grey_question: | (node1) ``GX-CHIP`` peripheral will appear on windows 10, install [AML burning tool suite](https://download.banana-pi.dev/d/3ebbfa04265d4dddb81b/files/?p=%2FTools%2Fimage_download_tools%2Faml_usb_burning_tool_V2_setup_v2.2.3.3.zip) to get the driver.
OS img ``armbian bullseye`` | :heavy_check_mark:|:heavy_check_mark: | Testing ``Armbian_23.02.0-trunk_Bananapicm4_bullseye_current_6.0.14_minimal.img``. ssh working user/pwd ``root/1234`` then create ``pi/bananapi``
OS img ``debian 10`` | :heavy_check_mark:|:heavy_check_mark: | Testing ``2023-01-12-debian-10-buster-bpi-cm4-aarch64-sd-emmc.img``. ssh working user/pwd ``pi/bananapi`` then ``su -``
OS img custom ``dietPi`` | :heavy_check_mark:|:x: | using DietPi transformation script fails after 1st reboot, initramfs doesn't have support for A311 processor

:x: ko / :heavy_check_mark: ok / :grey_question: todo or more testing required

## Software

Armbian community has added support for bananapi CM4, currently valid since Armbian 23.5 for testing.

See https://www.armbian.com/bananapicm4io/