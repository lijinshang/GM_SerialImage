
# GM_SerialImage
              GM 串口图像显示软件 V1.1 by 李锦上 
  * 功能简介 
  * ======================================= 
  * 将串口收到的图像数据按图像格式显示出来 
  * 支持多种格式的图像 
  * 支持按行更新图像 
  * 支持多行更新图像 
  * 占用MCU资源小 通信成功率高 
  * ======================================= 
  * 通信协议： 每两帧之间间隔大于10ms 
  * Byte0 ：0xA5 帧头 
  * Byte1 ：0x5A 帧头 
  * Byte2 ：帧长 低8位 
  * Byte3 ：帧长 高8位 
  * Byte4 ：功能码 0x01:图像水平更新 
  * Byte5 ：图像行号 低8位 
  * Byte6 ：图像行号 高8位 
  * ByteN ：图像数据 一列数据从左向右依次填充 小端模式 
  * ByteN+8：0xAA 帧尾 
  * =======================================
  * 图像数据帧例子： 
  * 图像格式：GRAY1 图像宽度：128 图像高度：128 
  * 更新第0行的图像：A5 5A 18 00  01  00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  AA 
  * 图像格式：RGB565 图像宽度：48 图像高度：48 
  * 更新第0行的图像：A5 5A  68 00  01  00 00  FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF  AA
  * =======================================
  * 取模设置 
  * PCtoLCD2002(支持单色)：阴码、逐行式、顺向 
  * Image2Lcd(支持单色、灰度、彩色)：水平扫描、取消包含图像头数据、勾选高位在前、其它保持默认(字节内像素数据正序、自左向右扫描、自顶至底扫描) 
  * =======================================
  * 软件更新地址：https://github.com/lijinshang/GM_SerialImage 
  * 软件编写匆忙难免有bug，还请不吝指正 
  * 作者邮箱：lijinshang@126.com 
  * =======================================
 
 
