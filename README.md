# banapi-cm4_turing-pi2

BananaPI CM4 is a rather new SBC. 

(March 2023) Because of global shortage, I had no other choice but to order 4 pieces in place of raspberry CM4.

:expressionless: :expressionless: :expressionless: :expressionless: Element14/Farnell is planning for availabylity arround february/march 2024 :expressionless: :expressionless: :expressionless: :expressionless:

## What's working



Components |Tested | Working  | Remark
---|---|---| --
BMC power | :heavy_check_mark:|:heavy_check_mark: | 
Network I/O | :heavy_check_mark:|:heavy_check_mark: | dhcp client correctly getting IP
HDMI ouput| :heavy_check_mark: |:heavy_check_mark:| main HDMI on node 1 with [same HDMI Circuit Switch configuration](https://help.turingpi.com/hc/en-us/articles/8685766680477-Specifications-and-I-O-Ports#f231ec3c) as rapsberry PI CM4
Boot from SD card| :heavy_check_mark: |:heavy_check_mark:| write img on SDcard then insert in the turingPI CM4 adapator
Boot from EMMC | :x: |:grey_question: | under testing
USB OTG | :x: |:grey_question: | under testing

:x: ko :heavy_check_mark: ok :grey_question: todo