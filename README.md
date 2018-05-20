# NanopiNeo-Neo2_ExtensionBoard
The extension board of Kicad Files for Nano Pi Neo/Neo2 with USB and RTC, grove con.

[FriendlyElec製NanoPi Neo/Neo2][0]の拡張ボードです。<br>
ピンヘッダ上にあるUSB2ポート、I2Cポート(Grove)のコネクタを搭載しています。<br>
標準USBの1ポートで足りないという場合やGroveで拡張したいという場合に最適です。<br>
また、I2Cポートには[純正NASキット][1]と同じ[RTC　DS1307][2]が搭載しています。<br>
そのため、電源断でも時刻を保持することが可能です。<br>



<img src="https://github.com/meerstern/NanopiNeo-Neo2_ExtensionBoard/blob/master/nanopi_neo1.jpg" width="360">

<img src="https://github.com/meerstern/NanopiNeo-Neo2_ExtensionBoard/blob/master/nanopi_neo2.jpg" width="360">


## NanoPi Neo/Neo2拡張ボード仕様
  * USB2ポート(フルサイズtypeA、USB1、USB2)搭載
  * I2Cポート(Groveコネクタ、I2C0)搭載
  * RTC(リアルタイムクロック、DS1307、CR1220 or CR1225バッテリ、I2C0内部接続)搭載
  * I2Cは10kでプルアップ抵抗を基板回路に搭載
  
## NanoPi Neo/Neo2 RTC設定/読み込み方法
  1. RTC接続の有無確認    
  ```sudo i2cdetect -y 0```    
  68が表示されていれば、RTCが正常に接続されています。
  
  1. Neo/Neo2時刻設定  
  ```sudo date +%T -s "19:52:00"```  
  ```sudo date +%Y%m%d -s "20180518"```  

  1. RTC DS1307ドライバ読み込み  
  ```sudo modprobe rtc-ds1307```
  
  1. 時刻のRTCへの書き込み<br> 
  ```sudo hwclock -w -f /dev/rtc*```  
  *は1、2...といった数字が入ります。機器によって異なります。  
  
  1. 起動時の時刻のRTCからの読み込み<br>
  ```sudo hwclock -r -f /dev/rtc*```  
  *は1、2...といった数字が入ります。機器によって異なります。 
  
## NanoPi Neo/Neo2拡張ボード使用例

<img src="https://raw.githubusercontent.com/meerstern/NanopiNeo-Neo2_ExtensionBoard/master/img/IMG_1.JPG" width="360">

<img src="https://raw.githubusercontent.com/meerstern/NanopiNeo-Neo2_ExtensionBoard/master/img/IMG_2.JPG" width="360">

<img src="https://raw.githubusercontent.com/meerstern/NanopiNeo-Neo2_ExtensionBoard/master/img/IMG_3.JPG" width="360">

　ピンヘッダは別売、別途はんだ付けが必要です。
 
 
## NanoPi Neo/Neo2拡張ボード注意点
  * NanoPi Neo/Neo2のGPIO1、GPIO2に接続するためのピンヘッダは別売りです。
  * 取付するピンヘッダの長さが標準的な10mmの場合、電源供給用microUSBと拡張ボードのUSBが干渉してどちらかが使用できません。<br>
 この場合は長いピンヘッダやピンコネクタを使用して干渉を回避するか、
 microUSBを使用せずにDebugUARTピンをヒートシンク横から取り出して5V電源を供給してください。
  * RTC DS1307は電池なしで電源に接続した場合、破損する可能性があります。必ず電池を入れて使用してください。


 
  
[0]: http://www.friendlyarm.com/index.php?route=product/product&product_id=180 "*0"
[1]: http://www.friendlyarm.com/index.php?route=product/product&product_id=192 "*1"
[2]: https://www.maximintegrated.com/en/products/digital/real-time-clocks/DS1307.html "*1"
