# Chapter 7 — Computer Network Design

## 1.1 บทนำ (Introduction)

**ความหมายของ Computer Network**
เครือข่ายคอมพิวเตอร์ (Computer Network) คือการเชื่อมโยงคอมพิวเตอร์ อุปกรณ์อิเล็กทรอนิกส์ และอุปกรณ์เครือข่ายต่าง ๆ เข้าด้วยกันผ่านสื่อกลางการสื่อสาร เช่น สายสัญญาณทองแดง สายใยแก้วนำแสง หรือคลื่นวิทยุ เพื่อให้สามารถแลกเปลี่ยนข้อมูลและใช้ทรัพยากรร่วมกันได้อย่างมีประสิทธิภาพ เครือข่ายอาจครอบคลุมตั้งแต่พื้นที่ขนาดเล็ก เช่น ห้องปฏิบัติการคอมพิวเตอร์ ไปจนถึงขนาดใหญ่ระดับโลก เช่น อินเทอร์เน็ต การมีเครือข่ายช่วยให้ผู้ใช้งานสามารถติดต่อสื่อสาร แบ่งปันไฟล์ หรือเข้าถึงทรัพยากรจากระยะไกลได้สะดวกและรวดเร็ว

**ประโยชน์ของการใช้งาน**

1. **การแชร์ทรัพยากร (Resource Sharing):** อุปกรณ์ต่าง ๆ เช่น เครื่องพิมพ์ (Printer) หรือเซิร์ฟเวอร์ไฟล์ สามารถใช้ร่วมกันได้โดยไม่จำเป็นต้องจัดหาให้ทุกคนแยกเป็นรายบุคคล ลดค่าใช้จ่ายและเพิ่มประสิทธิภาพการทำงาน
2. **การสื่อสาร (Communication):** ผู้ใช้งานสามารถติดต่อกันผ่านอีเมล แชท วิดีโอคอนเฟอเรนซ์ หรือระบบการเรียนการสอนออนไลน์ ซึ่งมีความสำคัญอย่างมากในสถาบันการศึกษา
3. **การจัดการแบบรวมศูนย์ (Centralized Management):** ผู้ดูแลระบบสามารถควบคุม จัดการ และบำรุงรักษาทุกอุปกรณ์ในเครือข่ายจากศูนย์กลาง เช่น การอัปเดตซอฟต์แวร์ การกำหนดสิทธิ์เข้าถึง และการรักษาความปลอดภัย


## 1.2 อุปกรณ์เครือข่าย (Network Devices)

**Switch**
Switch เป็นอุปกรณ์ Layer 2 ของโมเดล OSI ทำหน้าที่เชื่อมต่ออุปกรณ์ปลายทาง (End Devices) เช่น PC, Printer หรือ Server เข้าด้วยกันภายในเครือข่ายท้องถิ่น (LAN) Switch จะใช้ MAC Address เป็นตัวอ้างอิงเพื่อส่งข้อมูลไปยังพอร์ตที่ถูกต้อง ทำให้เกิดการสื่อสารแบบเฉพาะเจาะจง ลดการชนกันของข้อมูล (Collision) และเพิ่มประสิทธิภาพในห้องปฏิบัติการที่มีคอมพิวเตอร์จำนวนมาก

**Router**
Router เป็นอุปกรณ์ Layer 3 ใช้สำหรับเชื่อมต่อเครือข่ายที่แตกต่างกัน เช่น VLAN หลาย ๆ กลุ่ม หรือเชื่อม LAN ภายในห้องปฏิบัติการออกสู่อินเทอร์เน็ต Router มีหน้าที่กำหนดเส้นทาง (Routing) และทำงานร่วมกับโปรโตคอล เช่น OSPF, RIP หรือ Static Routing เพื่อเลือกเส้นทางที่เหมาะสม นอกจากนี้ยังสามารถทำ NAT (Network Address Translation) เพื่อให้เครื่องหลายเครื่องแชร์การใช้งาน Public IP ได้

**Access Point (AP)**
Access Point เป็นอุปกรณ์ไร้สายที่ให้ Notebook, Smartphone หรืออุปกรณ์ IoT เชื่อมต่อเข้าสู่เครือข่าย LAN ผ่านมาตรฐาน IEEE 802.11 (Wi-Fi) AP ทำหน้าที่เป็นสะพานเชื่อม (Bridge) ระหว่างเครือข่ายไร้สายและสาย ทำให้ผู้ใช้งานในห้องปฏิบัติการสามารถเข้าถึงเครือข่ายได้แม้ไม่ใช้สาย LAN


## 1.3 IP Addressing & Subnetting

**IPv4 Address**
ในเครือข่ายห้องปฏิบัติการ มักใช้ที่อยู่แบบ Private IP เช่น `192.168.x.x` ซึ่งไม่สามารถเข้าถึงได้โดยตรงจากอินเทอร์เน็ต แต่เหมาะสมสำหรับการใช้งานภายในองค์กร

**Subnet Mask และ CIDR**
Subnet Mask กำหนดส่วนของ Network และ Host ภายใน IP Address เช่น `255.255.255.0` หรือ `/24` จะมี 254 Host ที่ใช้งานได้ เหมาะสมกับห้องคอมพิวเตอร์ที่มีจำนวนเครื่องไม่เกิน 254 เครื่อง

**Default Gateway**
ในแต่ละ VLAN จะต้องมี Default Gateway ซึ่งโดยทั่วไปคือ IP ของ Router ที่เชื่อมต่อกับ VLAN นั้น ๆ เช่น VLAN 10 → `192.168.10.1`

**DNS (Domain Name System)**
DNS ช่วยแปลงชื่อโดเมน เช่น `www.google.com` ให้เป็น IP Address เช่น `142.250.190.14` เพื่อให้เครื่องลูกข่ายใช้งานอินเทอร์เน็ตได้สะดวก โดยใน Lab มักตั้งค่าใช้ Google DNS (`8.8.8.8`)


## 1.4  หลักการของ Hierarchical Design

การออกแบบเครือข่ายแบบ **Hierarchical Network Design** (การออกแบบเครือข่ายเชิงลำดับชั้น)
คือแนวคิดในการออกแบบโครงสร้างเครือข่ายให้เป็น “ชั้น ๆ” หรือ “ลำดับขั้น” ที่ชัดเจน โดยแต่ละชั้นมีหน้าที่แตกต่างกันไปและทำงานร่วมกัน เพื่อให้เครือข่ายมี **ประสิทธิภาพ (Performance)**, **ความง่ายในการบริหารจัดการ (Manageability)**, **ความยืดหยุ่น (Scalability)** และ **ความทนทานต่อความผิดพลาด (Resiliency)**


Cisco และ CompTIA Network+ อธิบายว่าโครงสร้างเชิงลำดับชั้นของเครือข่ายมักจะแบ่งออกเป็น 3 ชั้นหลัก ได้แก่

### Core Layer (ชั้นแกนกลาง)

* ทำหน้าที่เป็น **backbone** ของเครือข่าย
* รองรับการส่งข้อมูลความเร็วสูงระหว่าง Distribution Layer
* ควรใช้เส้นทางที่เรียบง่ายที่สุด (fast switching) และอุปกรณ์คุณภาพสูง
* ตัวอย่าง: Core Switch, High-Speed Router

### Distribution Layer (ชั้นกระจาย)

* ทำหน้าที่เป็น “ตัวกลาง” ระหว่าง Core และ Access
* จัดการ **การกำหนดนโยบาย (Policy Control)** เช่น Access Control List (ACL), Routing, Inter-VLAN Routing, QoS
* รวมการเชื่อมต่อจาก Access Layer หลาย ๆ จุดเข้ามา
* ตัวอย่าง: Multilayer Switch, Router

### Access Layer (ชั้นการเข้าถึง)

* เป็นชั้นที่เชื่อมต่อโดยตรงกับผู้ใช้งาน (End Devices) เช่น PC, Printer, Access Point
* ทำงานที่ Layer 2 เป็นหลัก (เช่น Switch ที่แจกจ่าย VLAN, Port Security)
* มักเป็นจุดที่ผู้ใช้เชื่อมต่อเข้ามากับระบบเครือข่าย

 

### ลักษณะสำคัญของการออกแบบแบบ Hierarchical

1. **แยกหน้าที่ชัดเจน** – แต่ละ Layer มีหน้าที่ของตนเอง เช่น Core เน้นความเร็ว, Distribution เน้นนโยบาย, Access เน้นการเข้าถึง
2. **การขยายระบบ (Scalability)** – สามารถเพิ่ม Switch หรือ Router ใน Access Layer ได้โดยไม่กระทบต่อ Core Layer
3. **การจัดการง่าย (Manageability)** – ผู้ดูแลระบบสามารถควบคุม Policy ได้จาก Distribution Layer โดยไม่ต้องแก้ที่ Access ทุกตัว
4. **ความเสถียรและสำรอง (Resiliency & Redundancy)** – สามารถทำ Redundant Link ระหว่าง Layer ได้ เพื่อป้องกันการล่มของระบบ



![](figure/07/network_diagram.png)
 
* **Core Switch**: รับผิดชอบ backbone ของเครือข่ายในมหาวิทยาลัยหรือศูนย์ข้อมูล
* **Distribution Switch**: ควบคุม VLAN, Routing และ Security Policy ของแต่ละกลุ่มห้องแลบ
* **Access Switch**: กระจายพอร์ตให้ PC นักศึกษา, เครื่องพิมพ์, Access Point


### ข้อดีของ Hierarchical Design

* เครือข่ายทำงานได้เร็วและมีประสิทธิภาพสูง
* ง่ายต่อการแก้ไขปัญหา (เพราะแยกเป็นชั้น)
* รองรับการขยายระบบในอนาคต
* สามารถกำหนดนโยบายความปลอดภัยในระดับกลาง (Distribution) ได้สะดวก


### โดยสรุป
**Hierarchical Network Design คือการออกแบบเครือข่ายแบบเป็นชั้น (Core–Distribution–Access) เพื่อให้เครือข่ายจัดการง่าย, ขยายได้, มีประสิทธิภาพ และมีความทนทานสูง เหมาะสำหรับองค์กร มหาวิทยาลัย หรือห้องปฏิบัติการคอมพิวเตอร์ที่มีผู้ใช้งานจำนวนมาก**

### 1.4 VLAN และ Broadcast Domain

VLAN (Virtual LAN) เป็นการแบ่งเครือข่ายท้องถิ่น (LAN) ออกเป็นกลุ่มย่อยทางตรรกะ (Logical Segmentation) โดยไม่จำเป็นต้องเปลี่ยนโครงสร้างสายจริง VLAN จะช่วยลดขนาดของ Broadcast Domain หมายความว่าการกระจายสัญญาณ (Broadcast) จะจำกัดอยู่แค่ภายใน VLAN เดียวกันเท่านั้น ส่งผลให้เครือข่ายทำงานได้มีประสิทธิภาพขึ้น และมีความปลอดภัยมากขึ้น

**การประยุกต์ใช้ VLAN ในห้องปฏิบัติการคอมพิวเตอร์**

* VLAN 10: สำหรับนักศึกษา เพื่อแยกการใช้งานออกจากบุคลากร
* VLAN 20: สำหรับอาจารย์หรือผู้ดูแล เพื่อเพิ่มความปลอดภัย
* VLAN 30: สำหรับเครื่อง Server และ Printer เพื่อการบริการส่วนกลาง

การแบ่ง VLAN ทำให้สามารถกำหนดสิทธิ์การเข้าถึง ป้องกันการ Broadcast ทั่วเครือข่าย และทำให้การบริหารจัดการเป็นระบบระเบียบมากขึ้น


# 🧾 Lab Sheet: การออกแบบเครือข่ายห้องปฏิบัติการคอมพิวเตอร์ (Cisco Packet Tracer/IOS)

 

## 1. Objective (วัตถุประสงค์)

1. เข้าใจหลักการแบ่งเครือข่ายย่อย (Subnetting และ VLAN Segmentation)
2. สามารถสร้างและกำหนดค่า VLAN บน Switch Cisco ได้
3. สามารถตั้งค่า Router-on-a-Stick เพื่อทำ Inter-VLAN Routing ได้
4. สามารถตั้งค่า DHCP บน Router เพื่อแจก IP Address อัตโนมัติได้
5. ตรวจสอบการเชื่อมต่อและการทำงานของเครือข่ายด้วยคำสั่งพื้นฐาน

 

## 2. Requirement (ความต้องการ)

* แบ่งผู้ใช้งานในห้องปฏิบัติการคอมพิวเตอร์ออกเป็น 3 VLAN:

  * VLAN10 → Student PCs
  * VLAN20 → Teacher PCs
  * VLAN30 → Server/Printer
* ทุกเครื่องได้รับ IP จาก DHCP Server โดยอัตโนมัติ
* ผู้ใช้งานข้าม VLAN สามารถสื่อสารกันได้ผ่าน Router
* อุปกรณ์เชื่อมต่อกับเครือข่าย Internet ผ่าน Router

 
## 3. Equipment (อุปกรณ์ที่ใช้)

* Cisco Router 1 เครื่อง (R1)
* Cisco Switch 1 เครื่อง (SW1)
* Access Point 1 ตัว (สำหรับอุปกรณ์ไร้สาย)
* PC อย่างน้อย 6 เครื่อง (แทน 30 เครื่องในห้องจริง)
* Software: Cisco Packet Tracer หรืออุปกรณ์จริง

 

## 4. Network Topology

![](figure/07/workshop_topology.png)

## 5. IP Addressing Plan

* VLAN10 (Student): 192.168.10.0/24, GW 192.168.10.1
* VLAN20 (Teacher): 192.168.20.0/24, GW 192.168.20.1
* VLAN30 (Server): 192.168.30.0/24, GW 192.168.30.1
* DNS: 8.8.8.8

 

## 6. Step by Step

### 6.1 Switch Configuration

```cisco
Switch> enable
Switch# configure terminal
! สร้าง VLAN
Switch(config)# vlan 10
Switch(config-vlan)# name STUDENT
Switch(config)# vlan 20
Switch(config-vlan)# name TEACHER
Switch(config)# vlan 30
Switch(config-vlan)# name SERVER
! กำหนดพอร์ต
Switch(config)# interface range fa0/1-10
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config)# interface range fa0/11-20
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config)# interface range fa0/21-24
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 30
! กำหนด trunk ไป Router
Switch(config)# interface fa0/24
Switch(config-if)# switchport mode trunk
```

 

### 6.2 Router-on-a-Stick

```cisco
Router> enable
Router# configure terminal
Router(config)# interface g0/0
Router(config-if)# no shutdown
Router(config)# interface g0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config)# interface g0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0
Router(config)# interface g0/0.30
Router(config-subif)# encapsulation dot1Q 30
Router(config-subif)# ip address 192.168.30.1 255.255.255.0
```

 

### 6.3 DHCP Server

```cisco
Router(config)# ip dhcp pool STUDENT
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 8.8.8.8

Router(config)# ip dhcp pool TEACHER
Router(dhcp-config)# network 192.168.20.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.20.1
Router(dhcp-config)# dns-server 8.8.8.8

Router(config)# ip dhcp pool SERVER
Router(dhcp-config)# network 192.168.30.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.30.1
Router(dhcp-config)# dns-server 8.8.8.8
```

 

## 7. Verification (ตรวจสอบผลลัพธ์)

* บน Switch

  ```
  show vlan brief
  show interfaces trunk
  ```
* บน Router

  ```
  show ip route
  show ip dhcp binding
  ```
* บน PC

  ```
  ipconfig
  ping 192.168.20.10   (ทดสอบข้าม VLAN)
  ping 8.8.8.8         (ทดสอบออกอินเทอร์เน็ต)
  ```

 

✅ **ผลลัพธ์ที่คาดหวัง:**

* ทุก PC ได้รับ IP อัตโนมัติจาก DHCP
* VLAN ถูกแยกการสื่อสารตามกลุ่ม แต่สามารถติดต่อกันผ่าน Router ได้
* ทุกเครื่องสามารถออกอินเทอร์เน็ตได้
 

 
