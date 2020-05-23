
# GM_SerialImage
              GM 串口图像显示软件 V1.0 by 李锦上 
  * 功能简介 
  * ======================================= 
  * 将串口收到的图像数据按图像格式显示出来 
  * 最大支持65535字节图像 
  * ======================================= 
  * 通信协议： 每两帧之间间隔大于10ms 
  * Byte0 ：A5 帧头 
  * Byte1 ：5A 帧头 
  * Byte2 ：本帧包含的字节数 高8位，除帧头字节外 
  * Byte3 ：本帧包含的字节数 低8位，除帧头字节外 
  * ByteN ：图像数据 按照从上向下，从左向右依次发送 高位在前 
  * ByteN+1  ：AA 帧尾 
  * =======================================
  * 图像数据帧例子： 
  * 图像格式：GRAY1 图像宽度：128 图像高度：128 

    A5 5A 08 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 C0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FF FF F0 00 00 00 00 00 00 00 00 00 00 00 00 1F FF FF FF C0 00 00 00 00 00 00 00 00 00 00 01 FF FF FF FF FC 00 00 00 00 00 00 00 00 00 00 0F FF FF FF FF FF 80 00 00 00 00 00 00 00 00 00 3F FF FF FF FF FF F0 00 00 00 00 00 00 00 00 01 FF FF FF FF FF FF FC 00 00 00 00 00 00 00 00 07 FF FF FF FF FF FF FF 00 00 00 00 00 00 00 00 1F FF FF F8 00 FF FF FF C0 00 00 00 00 00 00 00 3F FF FF 00 00 0F FF FF F0 00 00 00 00 00 00 00 FF FF F8 00 00 01 FF FF F8 00 00 00 00 00 00 01 FF FF E0 00 00 00 7F FF FE 00 00 00 00 00 00 03 FF FF 00 00 00 00 1F FF FF 00 00 00 00 00 00 07 FF FC 00 00 00 00 07 FF FF 80 00 00 00 00 00 1F FF F8 00 00 00 00 01 FF FF C0 00 00 00 00 00 3F FF E0 00 00 00 00 00 FF FF F0 00 00 00 00 00 7F FF C0 3F 00 00 00 00 7F FF F8 00 00 00 00 00 FF FF 80 FF 00 00 C0 00 3F FF F8 00 00 00 00 00 FF FE 07 FF 80 03 E0 00 7F FF FC 00 00 00 00 01 FF FE 1F FF 80 07 E0 00 FF FF FE 00 00 00 00 03 FF FE 7F FF C0 1F F0 01 FF FF FF 00 00 00 00 07 FF FC FF FF C0 3F E0 03 FD FF FF 80 00 00 00 07 FF FF FF C3 80 7F E0 07 FC FF FF 80 00 00 00 0F FF FF FF 03 80 FF E0 1F F8 FF FF E0 00 00 00 1F FF FF FE 03 81 EF C0 3F F0 7F FF F0 00 00 00 1F FF FF F8 03 83 C7 C0 7F E0 3F FF F8 00 00 00 3F FF 3F E0 07 07 87 80 FF E0 1F FF F8 00 00 00 3F FF 7F C0 07 0E 0F 81 FF C0 0F FF F8 00 00 00 7F FE 7F 00 06 1C 0F 03 FF 80 0F FF F0 00 00 00 7F FC 7C 00 0E 38 1F 07 8F 00 07 FF E0 00 00 00 FF FC 70 00 0C 78 1E 0F 1E 00 03 FF C0 00 00 00 FF F8 00 00 1C F0 3C 1E 3C 00 03 FF 80 00 00 01 FF F8 00 00 3C E0 3C 3C 78 00 01 FF 00 00 00 01 FF F0 00 00 39 C0 78 78 78 00 00 FC 00 00 00 03 FF F0 00 00 73 80 F8 F0 F0 00 00 00 00 00 00 03 FF F0 00 00 77 00 F1 E1 E0 00 00 00 00 00 00 03 FF E0 00 00 FF 01 F3 C3 E0 00 00 00 00 00 00 07 FF E0 00 01 FE 01 E7 87 C0 00 00 00 00 00 00 07 FF C0 00 01 FC 03 CF 0F 80 00 00 00 00 00 00 07 FF C0 00 03 F8 07 DE 0F 80 00 00 00 00 00 00 07 FF C0 00 07 F0 0F BC 1F 00 00 00 00 00 00 00 0F FF 80 00 07 F0 0F F8 3F 00 00 00 00 00 00 00 0F FF 80 00 0F E0 1F F0 3E 00 00 00 00 00 00 00 0F FF 80 00 1F C0 3F E0 7E 00 00 00 00 00 00 00 0F FF 80 00 3F C0 3F C0 FC 00 00 00 00 00 00 00 1F FF 00 00 3F 80 7F C0 FC 00 00 00 00 00 00 00 1F FF 00 00 7F 00 FF 80 F8 00 00 00 00 00 00 00 1F FF 00 00 FF 01 FF 01 F8 00 00 00 00 00 00 00 1F FF 00 01 FE 01 FE 01 F8 00 40 00 00 00 00 00 1F FE 00 01 FC 03 FC 01 F0 01 80 00 00 00 00 00 1F FE 00 03 FC 03 F8 03 F0 03 00 00 00 00 00 00 3F FE 00 03 F8 07 F8 03 F0 0E 00 00 00 00 00 00 3F FE 00 03 F0 07 F0 03 F0 1C 00 00 00 00 00 00 3F FE 00 01 F0 07 E0 03 F8 78 00 00 00 00 00 00 3F FE 00 01 E0 07 C0 03 FF F0 00 00 00 00 00 00 3F FC 00 00 C0 03 80 03 FF C0 00 00 00 00 00 00 3F FC 00 00 00 03 80 01 FF 80 00 00 00 00 00 10 3F FC 00 00 00 01 00 01 FE 00 00 00 00 00 01 F8 3F FC 00 00 00 00 00 0F FF A0 00 00 00 00 3F F8 3F FC 00 00 00 00 00 7F FF FF FF FF FF FF FF F0 3F FC 00 00 00 00 01 FF FF FF FF FF FF FF FF F0 3F FE 00 00 00 00 03 FF FF FF FF FF FF FF FF E0 3F FE 00 00 00 00 03 FF FF FF FF FF FF FF FF E0 3F FE 00 00 00 00 07 FF FF FF FF FF FF FF FF C0 3F FE 00 00 00 00 07 FF FF FF FF FF FF FF FF 80 3F FE 00 00 00 00 0F FF FF E0 01 FF FF FF FF 00 3F FE 00 00 00 00 0F FF FC 00 00 7F FF FF FC 00 1F FF 00 00 00 00 0F FF C0 00 00 3F FF FF F0 00 1F FF 00 00 00 00 0F FE 00 00 00 1F FF FF 80 00 1F FF 00 00 00 00 07 E0 00 00 00 0F FF F8 00 00 1F FF 80 00 00 00 00 00 00 00 00 0F FF 80 00 00 1F FF 80 00 00 00 00 00 00 00 00 0F FF 80 00 00 0F FF 80 00 00 00 00 00 00 00 00 0F FF 80 00 00 0F FF C0 00 00 00 00 00 00 00 00 0F FF 80 00 00 0F FF C0 00 00 00 00 00 00 00 00 1F FF 80 00 00 0F FF E0 00 00 00 00 00 00 00 00 1F FF 80 00 00 07 FF E0 00 00 00 00 00 00 00 00 1F FF 80 00 00 07 FF F0 00 00 00 00 00 00 00 00 1F FF 80 00 00 03 FF F0 00 00 00 00 00 00 00 00 1F FF 80 00 00 03 FF F8 00 00 00 00 00 00 00 00 3F FF 80 00 00 03 FF FC 00 00 00 00 00 00 00 00 3F FF 80 00 00 01 FF FC 00 00 00 00 00 00 00 00 7F FF 80 00 00 00 FF FE 00 00 00 00 00 00 00 00 FF FF 80 00 00 00 FF FF 00 00 00 00 00 00 00 00 FF FF 80 00 00 00 7F FF 80 00 00 00 00 00 00 01 FF FF 80 00 00 00 7F FF C0 00 00 00 00 00 00 03 FF FF 80 00 00 00 3F FF E0 00 00 00 00 00 00 07 FF FF 80 00 00 00 1F FF F0 00 00 00 00 00 00 0F FB FF 80 00 00 00 0F FF FC 00 00 00 00 00 00 3F F3 FF 80 00 00 00 07 FF FE 00 00 00 00 00 00 FF E3 FF 80 00 00 00 03 FF FF 80 00 00 00 00 03 FF C3 FF C0 00 00 00 01 FF FF E0 00 00 00 00 0F FF 83 FF C0 00 00 00 00 FF FF FC 00 00 00 00 7F FE 03 FF C0 00 00 00 00 7F FF FF 00 00 00 03 FF FC 03 FF C0 00 00 00 00 1F FF FF F0 00 00 7F FF F8 03 FF C0 00 00 00 00 0F FF FF FF C0 3F FF FF E0 01 FF E0 00 00 00 00 03 FF FF FF FF FF FF FF 80 01 FF E0 00 00 00 00 00 FF FF FF FF FF FF FE 00 01 FF E0 00 00 00 00 00 3F FF FF FF FF FF F8 00 00 FF C0 00 00 00 00 00 07 FF FF FF FF FF E0 00 00 FF C0 00 00 00 00 00 00 FF FF FF FF FE 00 00 00 7F 80 00 00 00 00 00 00 07 FF FF FF F0 00 00 00 1F 00 00 00 00 00 00 00 00 1F FF FC 00 00 00 00 00 00 00 00 00 00 00 00 00 00 0C 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 AA   
  * 图像格式：RGB565 图像宽度：48 图像高度：48 
  
    A5 5A 12 02 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF DF FE FB FF DF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF DF FE FB FD F7 FC 71 FB EF FA AA F9 45 FA 8A FB CF FC 10 FD 55 FE 79 FF 3C FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE 18 FB CF F9 E7 F8 20 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 82 FA 8A FC 71 FE 79 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF DF FD 55 F9 E7 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 20 F9 C7 FD 34 FF DF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE 38 F9 C7 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F9 04 FB 0C FC D3 FE 59 FF 5D FE FB FE 18 FC B2 FB 2C F8 61 F8 00 F8 00 F8 20 F8 00 F8 00 F8 00 F9 86 FD D7 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FC 72 F8 00 F8 00 F8 20 F8 00 F8 00 F8 00 FB 2C FE 79 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 3C FC D3 F8 C3 F8 00 F8 00 F8 20 F8 20 F8 00 F8 00 FB 8E FF BE FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FB 0C F8 00 F8 00 F8 20 F8 00 F8 00 FA 8A FF 1C FF FF FF FF FF 9E FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 7D FB AE F8 00 F8 00 F8 20 F8 20 F8 00 F8 00 F9 E7 FF BE FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FA AA F8 00 F8 00 F8 20 F8 00 F8 00 FD 55 FF FF FF 1C FB CF F8 41 F8 61 FF 5D FF FF FF FF FF FF FF FF FE 9A FD 55 FF FF FF FF FF FF FF FF FF FF FD 55 F8 00 F8 00 F8 20 F8 20 F8 20 F8 00 F9 86 FF DF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FC 51 F8 00 F8 00 F8 20 F8 00 F8 00 FC B2 FF 9E FA CB F8 00 F8 00 F8 00 F8 00 FC 10 FF FF FF FF FF FF FD 14 F8 00 F8 00 FE 59 FF FF FF FF FF FF FE 79 FA 69 F8 00 F8 00 F8 00 F8 20 F8 20 F8 20 F8 00 FA 28 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE BA F8 00 F8 00 F8 20 F8 00 F8 00 F8 61 FB 8E F8 61 F8 00 F8 00 F9 E7 FD 75 F9 24 FA 69 FF FF FF FF FA AA F8 00 F8 00 F8 00 FE 9A FF FF FF FF FD 96 F8 00 F8 00 F8 20 FC B3 F8 00 F8 00 F8 20 F8 20 F8 00 F8 00 FC 10 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF F8 82 F8 00 F8 20 F8 00 F8 00 F8 A2 F8 00 F8 00 F8 00 F9 04 FD 55 FF FF FF FF F9 65 FD F7 FF FF F9 65 F9 04 FD 55 F8 00 FA 08 FF FF FF FF FC 72 F8 00 F8 00 F8 00 FC B2 FF FF FD F7 F8 00 F8 00 F8 20 F8 20 F8 00 F8 00 FB AE FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD 75 F8 00 F8 00 F8 20 F8 00 FB 2C FC 92 F8 00 F8 00 FB CF FF 9E FF FF FF FF FE FB F8 C3 FF FF FB 2C F8 A2 FF FF FE 59 F8 00 FF 3C FF FF FB 6D F8 00 F8 82 F8 00 FB 0C FF FF FF FF FF FF FB 2C F8 00 F8 20 F8 20 F8 20 F8 00 F9 24 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF DF F8 61 F8 00 F8 20 F8 00 F8 00 FE DB FC F3 FB 0C FE DB FF FF FF FF FF FF FF FF FA 08 FD 55 FD 14 F8 00 FF DF FF FF F0 00 FA EB FF FF FB 6D F8 00 FE BA F9 86 FA 49 FF FF FF FF FF FF FF FF FF DF F8 A2 F8 00 F8 00 F8 00 F9 65 FF 7D FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD B6 F8 00 F8 00 F8 20 F8 00 FA 8A FF FF FF DF FF FF FF FF FF FF FF FF FF FF FE 7A F9 45 FD 55 F8 00 FF 5D FF FF FC 71 F8 00 FF BE FC 10 F8 00 FF 9E FC D3 F8 00 FF BE FF FF FF FF FF FF FF FF FF FF FE 9A F8 C3 F8 41 FB 4D FF 9E FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FA 69 F8 00 F8 20 F8 00 F8 00 FE 59 FF FF FF FF FF FF FF FF FF FF FF FF FF FF F8 E3 F9 A6 F8 E3 FE FB FF FF FF 7D F8 00 FD D7 FD 34 F8 00 FF FF FD F7 F0 00 FE FB FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 5D FE BA FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 7D F8 00 F8 00 F8 20 F8 00 F8 E3 FF DF FF FF FF FF FF FF FF FF FF FF FF FF FC 72 F8 00 F0 00 FD 96 FF FF FF FF F9 86 F9 E7 FC D3 F8 00 FF BE FF 1C F8 00 FC 10 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD B6 F8 00 F8 00 F8 20 F8 00 FC 30 FF FF FF FF FF FF FF FF FF FF FF FF FE FB F8 00 F8 00 FB 6D FF FF FF FF FC 92 F8 00 F8 E3 F8 20 FF 3C FF FF F8 20 F8 20 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FB EF F8 00 F8 20 F8 00 F8 00 FE 79 FF FF FF FF FF FF FF FF FF FF FF DF F8 E3 F8 00 F9 24 FF DF FF FF FF 1C F8 00 F8 00 F8 00 FE 79 FF FF FB 2C F0 00 FD 76 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF F9 E7 F8 00 F8 20 F8 00 F8 41 FF 5D FF FF FF FF FF FF FF FF FF FF FB 6D F8 00 F8 00 FE FB FF FF FF BE F8 61 F8 00 F8 00 FE 18 FF FF FF 1C F8 00 F8 41 FF DF FF FF FF FF FF FF FF 7D FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF BE F8 61 F8 00 F8 20 F8 00 F9 E7 FF FF FF FF FF FF FF FF FF FF FD 55 F8 00 F8 00 FC F3 FF FF FF FF FB 6D F8 00 F8 00 FC 51 FF FF FF FF FC 10 F8 00 FB 0C FF FF FF FF FF FF FC D3 FB AE FF DF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE DB F8 00 F8 00 F8 20 F8 00 FB 6D FF FF FF FF FF FF FF FF FF FF F9 C7 F0 00 F8 E3 FF FF FF FF FE DB F8 00 F8 00 FA 69 FF FF FF FF FF FF F9 C7 F8 00 FB 4D FF FF FF 5D FA AA FA 08 FF 3C FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE 79 F8 00 F8 00 F8 20 F8 00 FC B2 FF FF FF FF FF FF FF FF FF FF FD 96 F0 00 FE BA FF FF FF FF FE FB F8 00 F8 E3 FF DF FF FF FF FF FF FF FB 0C F8 00 F8 41 FA 8A F8 E3 FC 30 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FC 10 F8 00 F8 00 F8 20 F8 00 FD 96 FF FF FF FF FF FF FF FF FF FF FF DF FE 59 FF FF FF FF FF FF FF FF FB CF FE BA FF FF FF FF FF FF FF 9E FC 30 F8 00 F8 00 F8 61 FC D3 FF FF FF FF FF BE FF DF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF BE FF 3C FD 96 FA EB FB 4D FF 1C FB EF F8 00 F8 00 F8 20 F8 00 FD 14 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 5D FB 6D F8 00 F8 00 F8 20 F8 00 F8 E3 F9 C6 F8 A2 F9 24 F9 45 FA 08 F9 C7 F9 65 F9 E7 FA 28 FA 69 FA 49 FA 49 FA 69 FA 8A FA 28 F9 24 F8 00 F8 00 F8 00 FA 69 FF 9E FD D7 F8 00 F8 00 F8 20 F8 00 FC 71 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF BF F9 C7 F8 00 F8 00 F8 00 F8 20 F8 20 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 FF 9E FF FF FE 79 F8 00 F8 00 F8 20 F8 00 FB 0C FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD D7 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 A2 FA 28 FB 2C FC 10 FC 71 FC 10 FA 8A F8 20 F8 00 F8 20 F8 20 F8 20 F8 20 F8 20 F8 20 F8 00 F8 00 F8 00 F8 E3 FE 79 FF FF FF FF FF 3C F8 00 F8 00 F8 20 F8 00 F9 04 FF BE FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD 34 F8 00 F8 00 F8 00 F9 45 FB 8E FE 18 FF 1C FF FF FF FF FF FF FF FF FF FF FF FF FE 18 F8 82 F8 00 F8 20 F8 20 F8 20 F8 00 F8 00 F8 40 FA 08 FC B2 FF 7D FF FF FF FF FF FF FF DF F9 24 F8 00 F8 20 F8 00 F8 00 FE BA FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 5D FC 71 FD 96 FE 38 FF 7D FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FB 0C F8 00 F8 20 F8 20 F8 00 FA AA FE 59 FE BA FF FF FF FF FF FF FF FF FF FF FF FF FF FF FB 8E F8 00 F8 20 F8 20 F8 00 FB EF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FB 4D F8 00 F8 20 F8 20 F8 00 FE 59 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD F7 F8 00 F8 00 F8 20 F8 00 F8 61 FF BE FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FA 08 F8 00 F8 20 F8 00 F8 00 FE 79 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF DF F8 41 F8 00 F8 20 F8 20 F8 00 FB EF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 9E F8 41 F8 00 F8 20 F8 00 F8 00 FE 38 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FC F3 F8 00 F8 20 F8 20 F8 00 F8 00 FE 9A FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FC 71 F8 00 F8 20 F8 20 F8 00 F8 00 FE 18 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF DF F8 41 F8 00 F8 20 F8 20 F8 00 F8 20 FE 9A FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE 79 F8 00 F8 00 F8 00 F8 20 F8 20 F8 00 FD B7 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE 9A F8 00 F8 00 F8 20 F8 20 F8 00 F8 00 FE 39 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD D7 F8 41 F8 00 F8 41 F9 45 F8 00 F8 20 F8 00 FC D3 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FD 14 F8 00 F8 00 F8 20 F8 20 F8 00 F8 20 FC 30 FF 9E FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 3D FB EF F8 00 F8 00 F8 00 FE 59 FC 92 F8 00 F8 20 F8 00 FC 71 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FC F3 F8 20 F8 00 F8 20 F8 20 F8 00 F8 00 F9 24 FC B2 FE FB FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 5D FE 18 FB 6D F8 61 F8 00 F8 00 F8 61 FE 18 FF FF FA AA F8 00 F8 20 F8 00 FB 2C FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE 59 F9 24 F8 00 F8 00 F8 20 F8 20 F8 00 F8 00 F8 20 FA 8A FC 30 FD B6 FE DB FF 5D FF 5D FF 1C FE 59 FD 55 FC 10 FB 0C F8 A2 F8 00 F8 00 F8 00 F8 00 FA 69 FF 1C FF FF FF FF FB 0C F8 00 F8 20 F8 00 F9 65 FF DF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 9E FC 71 F9 04 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 A2 F8 E3 F8 20 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F9 86 FD 55 FF FF FF FF FF FF FF FF FD 96 F8 00 F8 00 F8 00 F8 00 FE DB FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 7D FD 96 FA CB F9 45 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F8 00 F9 45 FB 2C FE 18 FF DF FF FF FF FF FF FF FF FF FF FF FF FF FA AA F8 00 F8 00 FB 0C FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 7D FE 38 FD 34 FB CF FB 2C FA 69 F9 C7 F8 A2 F8 A2 FA 28 FA EC FB 8E FC D3 FE 59 FF 7D FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF DF FB EF FB AE FF DF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 9E FE DB FE 79 FD F7 FD 34 FB AE FB CF FD B6 FE 79 FE 9A FF 5D FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FE FB FE BA FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF AA  
  * =======================================
  * 取模设置 
  * PCtoLCD2002(支持单色)：阴码、逐行式、顺向 
  * Image2Lcd(支持单色、灰度、彩色)：水平扫描、取消包含图像头数据、勾选高位在前、其它保持默认(字节内像素数据正序、自左向右扫描、自顶至底扫描) 
  * =======================================
  * 软件更新地址：https://github.com/lijinshang/GM_SerialImage 
  * 软件编写匆忙难免有bug，还请不吝指正 
  * 作者邮箱：lijinshang@126.com 
  * =======================================
 
