# Computer Network

## resoures for 
- CME66-311 Computer Network System
- IMI62-232 Computer Network

## Instructor

**Assist. Prof. Dr. Chanankorn Jandaeng**

School of Informatics, Walailak University


## Credit Hours

4(3-2-7)

## Course Description

This course introduces students to fundamental principles and advanced practices in computer networks. Topics include data communication theory, network protocols and models, transmission media, topologies, IP addressing, switching and routing, security systems, wireless and internet technologies, and network design and deployment. Emphasis is placed on analyzing, designing, implementing, and maintaining network and server systems for organizational use.

## Course Objectives

Upon successful completion of the course, students will be able to:

| **CLO** | **%** | **Learning Outcome**                                                                                     | **Formative**                | **Summative**                        |
| ------- | ----: | -------------------------------------------------------------------------------------------------------- | ---------------------------- | ------------------------------------ |
| CLO1.1  |   20% | Explain the core concepts of computer communication, OSI and TCP/IP models, and transmission techniques. | In-class discussion, quizzes | Midterm, final exam                  |
| CLO2.1  |   20% | Analyze and design network topologies and address plans for LAN/WAN environments.                        | Hands-on design tasks        | Practical exam, design documentation |
| CLO3.1  |   25% | Configure and troubleshoot basic network devices (switches, routers) and services (DHCP, DNS).           | Lab exercises, CLI practice  | Lab exam, configuration demo         |
| CLO5.1  |   10% | Demonstrate teamwork, responsibility, and communication in planning and presenting network projects.     | Peer feedback, rehearsals    | Final group presentation             |
| CLO6.1  |   10% | Evaluate the suitability of network technologies and tools for real-world organizational use.            | Comparative analysis task    | Project documentation                |

## Prerequisites

Basic knowledge of computer systems and operating systems.

## Teaching and Learning Strategies

1. **Lectures and Conceptual Discussions**
   Delivery of key networking theories and models (OSI, TCP/IP, routing, security).
2. **Hands-on Laboratory Sessions**
   Real-world application using tools like Cisco Packet Tracer and Wireshark.
3. **Project-Based Learning**
   Students work in teams to analyze needs, design, and propose functional network systems.
4. **Peer Learning and Collaboration**
   Presentations and peer feedback encourage deeper conceptual understanding.
5. **Simulations and Demonstrations**
   Use of virtual environments to simulate network behaviors and vulnerabilities.
6. **Reflective Learning**
   Self-assessment activities encourage critical thinking and evaluation of ethical use of networks.

## Assessment Methods and Weighting

| **Assessment Method**       | **Related CLOs**       | **Weight(%)** | **Description**                                                |
| --------------------------- | ---------------------- | -------------: | -------------------------------------------------------------- |
| Quizzes and Concept Reviews | CLO1.1                 |            10% | Short assessments to reinforce theoretical knowledge           |
| Midterm Exam                | CLO1.1, CLO2.1         |            20% | Evaluation of communication theory, models, and network design |
| Lab Assignments             | CLO3.1, CLO4.1         |            20% | Applied configurations and troubleshooting in lab environments |
| Network Design Project      | CLO2.1, CLO5.1, CLO6.1 |            20% | Real-world network design with documentation and proposal      |
| Final Examination           | CLO1.1, CLO3.1, CLO4.1 |            20% | Comprehensive assessment of theory and applied knowledge       |
| Team Collaboration          | CLO5.1, CLO6.1         |            10% | Communication, teamwork, and ethical considerations            |

**Total: 100%**

## Course Outline / Weekly Schedule

| **Chapter** | **Title**                       | **Topics** | **Learning Outcomes** | **Activities** | **File Link** |
|---------|-------------------------------------|-------------------------------|-------------------|--------------------|-----------|
| 1       | Introduction to Networking          | • What is a computer network?<br>• Why do we need a computer network<br>• Types of Computer Networks<br>• Internet | LO1: Define the concept and essential functions of a computer network.<br>LO2: Explain importance of networks.<br>LO3: Differentiate PAN, LAN, MAN, WAN, CAN, SAN, VPN.<br>LO4: Describe historical development of Internet. | Not explicitly listed | [chapter-01.md](chapter-01.md)|
| 2       | Connecting to the World             | • Definitions<br>• Understanding a Basic IP Networks<br>• Common Network Command-line Tools<br>• DHCP | • Explain/configure IPv4 and subnetting<br>• Understand subnet masks<br>• Implement DHCP & DNS<br>• Configure gateways<br>• Troubleshoot with tools | Includes CLI tasks: `ipconfig`, `ping`, `tracert`, `netstat`, `nslookup`; DHCP DORA process exercises | [chapter-02.md](chapter-02.md)|
| 3       | Network Devices                     | • Introduction to network devices<br>• Network topologies & architecture | • Identify functions of switches, routers, PCs<br>• Build network in Packet Tracer<br>• Use `ipconfig` & Control Panel | Packet Tracer lab; hands-on with `ipconfig`, `ping`, `tracert` | [chapter-03.md](chapter-03.md)|
| 4       | Network Architecture                | • OSI/TCP-IP models<br>• encapsulation <br>•  addressing <br>• routing | • Describe layered architectures (OSI, TCP/IP)<br>• Explain roles of devices/media/services/protocols<br>• Analyze encapsulation, addressing, and protocol operations | No explicit activity section, but concepts include TCP three-way handshake, routing exercises | [chapter-04.md](chapter-04.md)|
| 5       | LAN Design and Implementation       | • VLAN concept and benefits<br>• Creating/assigning VLANs<br>• Inter-VLAN routing<br>• Reducing broadcast domains | • Understand VLANs<br>• Configure VLANs on switches<br>• Implement inter-VLAN communication<br>• Limit broadcast domains | Cisco IOS configuration tasks: VLAN creation, port assignment, trunking, verification (`show vlan brief`, `show mac address-table`) | [chapter-05.md](chapter-05.md)|
| 6       | IP Addressing and Router Configuration | •  IPv4, CIDR <br>•subnetting <br>•IOS router config | • Explain IPv4 & special addresses<br>• Design subnets with CIDR/VLSM<br>• Describe router roles/interfaces<br>• Configure router interfaces & verify<br>• Deploy DHCP on IOS<br>• Implement static routes | Router config tasks (`ip address`, `encapsulation dot1Q`, DHCP setup); subnetting exercises | [chapter-06.md](chapter-06.md)|
| 7       | Network Design | •  Design Simple Network <br>• Implementing Simple Network   | ออกแบบเครือข่ายห้องปฏิบัติการคอมพิวเตอร์แบบเชิงลำดับชั้น (Hierarchical Design) โดยใช้ VLAN เพื่อลด Broadcast Domain และกำหนดโครงสร้าง Core–Distribution–Access ได้อย่างเหมาะสม| ออกแบบเครือข่ายเชิงลำดับชั้น | [chapter-07.md](chapter-07.md)| 



## Textbooks and References

* *Computer Networking: A Top-Down Approach* by James F. Kurose and Keith W. Ross
* *Data and Computer Communications* by William Stallings
* Cisco Networking Academy resources: [https://www.netacad.com](https://www.netacad.com)
* Wireshark documentation: [https://www.wireshark.org](https://www.wireshark.org)

## Policies

* **Attendance:** A minimum of 80% attendance is required to sit for the final exam.
* **Late Submissions:** Penalized unless due to valid and approved reasons.
* **Academic Integrity:** Strictly enforced. Violations may lead to failing the course.
* **Communication:** Students must monitor the LMS and university email for course updates.

---
