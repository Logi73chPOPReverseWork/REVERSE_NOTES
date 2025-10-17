# LogiSwitch BUTTON

Notes about reversing Logi73ch POP Button so we can still use it after it dies.

## Exploration

using HCI RTL8761BUV dongle

### BLE exploration

#### scan

```
wble-central --i hci1 scan
* clicks on each POP buttons *
 RSSI Lvl  Type  BD Address        Extra info
[-100 dBm] [PUB] a8:96:09:b1:7c:8d name:"GOAT-0256"
[-100 dBm] [PUB] fc:03:9f:5a:f6:f5 
[-044 dBm] [PUB] a0:e6:f8:db:26:76 name:"Logi Switch V1.06  "
[-044 dBm] [PUB] a0:e6:f8:db:29:09 name:"Logi Switch V1.06  "
```

#### explore

```
wble-central --interface hci1 -b a0:e6:f8:db:26:76 profile
Searching for target device a0:e6:f8:db:26:76 ...
Connecting to target device ...
Enumerating services and characteristics ...
Service Generic Access (0x1800)  (handle 1 to 7)
  Device Name (0x2A00) R, handle 2, value handle: 3
  Appearance (0x2A01) R, handle 4, value handle: 5
  Peripheral Preferred Connection Parameters (0x2A04) R, handle 6, value handle: 7

Service Generic Attribute (0x1801)  (handle 8 to 8)

Service Device Information (0x180A)  (handle 9 to 27)
  System ID (0x2A23) R, handle 10, value handle: 11
  Model Number String (0x2A24) R, handle 12, value handle: 13
  Serial Number String (0x2A25) R, handle 14, value handle: 15
  Firmware Revision String (0x2A26) R, handle 16, value handle: 17
  Hardware Revision String (0x2A27) R, handle 18, value handle: 19
  Software Revision String (0x2A28) R, handle 20, value handle: 21
  Manufacturer Name String (0x2A29) R, handle 22, value handle: 23
  IEEE 11073­20601 Regulatory Certification Data List (0x2A2A) R, handle 24, value handle: 25
  PnP ID (0x2A50) R, handle 26, value handle: 27

Service FE61  (handle 28 to 65535)
  FFF1 RN, handle 29, value handle: 30
    Descriptor type Client Characteristic Configuration (0x2902), handle: 31
    Descriptor type Characteristic User Description (0x2901), 'Certificate Read', handle: 32
  FFF2 W, handle 33, value handle: 34
    Descriptor type Characteristic User Description (0x2901), 'Secretwrite1Offset Eve', handle: 35
  FFF3 W, handle 36, value handle: 37
    Descriptor type Characteristic User Description (0x2901), 'Offset Event', handle: 38
  FFF4 RN, handle 39, value handle: 40
    Descriptor type Client Characteristic Configuration (0x2902), handle: 41
    Descriptor type Characteristic User Description (0x2901), 'Button Key event', handle: 42
  FFF5 W, handle 43, value handle: 44
    Descriptor type Characteristic User Description (0x2901), 'Button TDE Rx', handle: 45
  FFF6 RN, handle 46, value handle: 47
    Descriptor type Client Characteristic Configuration (0x2902), handle: 48
    Descriptor type Characteristic User Description (0x2901), 'Button TDE Tx', handle: 49

```



## Materiel

- Deux piles de 3v
- DEUX BOUTONS dont l'un est caché.

##### Composants:

- **CC2640**
  - CC2640 SimpleLink™ Bluetooth® Smart Wireless MCU

