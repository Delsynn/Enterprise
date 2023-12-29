## Router Configuratie Datacenter

Hierbij de configuratie voor de router van het datacenter:

```
Current configuration : 5377 bytes
!
! Last configuration change at 14:01:36 UTC Wed Dec 20 2023
!
version 15.4
no service timestamps debug uptime
no service timestamps log uptime
no service password-encryption
service call-home
!
hostname Routerdc
!
boot-start-marker
boot-end-marker
!
!
enable secret 5 $1$RWym$fMHJaNLk1EQk25cy3udnb0
!
no aaa new-model
!
!
!
!
!
!
call-home
 contact-email-addr sch-smart-licensing@cisco.com
 profile "CiscoTAC-1"
  active
  destination transport-method http
  no destination transport-method email
!
!
!
!
!
ip dhcp excluded-address 192.168.210.1 192.168.210.10
ip dhcp excluded-address 192.168.210.255
!
ip dhcp pool DATACENTER
 network 192.168.210.0 255.255.255.0
 default-router 192.168.210.1
 dns-server 8.8.8.8
!
!
!
ip domain name ucll.local
ip cef
login on-success log
no ipv6 cef
multilink bundle-name authenticated
!
!
cts logging verbose
!
crypto pki trustpoint TP-self-signed-932223096
 enrollment selfsigned
 subject-name cn=IOS-Self-Signed-Certificate-932223096
 revocation-check none
 rsakeypair TP-self-signed-932223096
!
crypto pki trustpoint SLA-TrustPoint
 revocation-check crl
!
!
crypto pki certificate chain TP-self-signed-932223096
 certificate self-signed 01
  3082032E 30820216 A0030201 02020101 300D0609 2A864886 F70D0101 05050030
  30312E30 2C060355 04031325 494F532D 53656C66 2D536967 6E65642D 43657274
  69666963 6174652D 39333232 32333039 36301E17 0D323331 32313930 39303835
  335A170D 33333132 31383039 30383533 5A303031 2E302C06 03550403 1325494F
  532D5365 6C662D53 69676E65 642D4365 72746966 69636174 652D3933 32323233
  30393630 82012230 0D06092A 864886F7 0D010101 05000382 010F0030 82010A02
  82010100 B627C5D3 5FB54B5B B0DA1950 F50DF398 CA06BAC9 6AEBB57B A548DBA4
  AAADCE65 CFF572F9 00BB5CE8 EC104B5F 82B4BE5A D96FA3EB AAD851E9 1429C394
  33043DA9 01ACAC6D D2AFEEAA 2A39B696 2D47C03F 05B0AB3D F91D39F1 FD9817AA
  1F58072D 1ADD2021 3F0A5BB1 38A2EDAA D6122FF5 AE5393A9 DADE70C2 BF1168AF
  F86DD35F 7D911E86 97E1C641 26B3A4AB 9823B33F 73EC8A08 7C5E74B1 8813275B
  63046FAD ABEF4DB3 4AEFC2DA 87C76A52 67367E8C 0244A4B5 C8E81F8D EC7C74C0
  F5E630EC C99D46E7 F36B126A 3D085EDF 370C7FF5 ABA8BDB0 0720CD48 21ADF68A
  A633A9FE E3A587A3 7991C532 49E12B5C 6784F563 5377227D 37D2EABA 65CAF37A
  6D804ADB 02030100 01A35330 51300F06 03551D13 0101FF04 05300301 01FF301F
  0603551D 23041830 168014E6 FA7B0774 3E174F56 0FC623C4 39BDEE84 E01B3F30
  1D060355 1D0E0416 0414E6FA 7B07743E 174F560F C623C439 BDEE84E0 1B3F300D
  06092A86 4886F70D 01010505 00038201 01001E93 8E455BA0 436CC117 03DFCCD1
  2C5F9D9D C13C7AE8 B4A70C22 C788131D B2A8C28B D1C595A6 65B8B39A F3471290
  8F5490A6 5F06B94E A904DB24 E82B12E0 18C3179D 0029436E 5D7A0575 5F59D5AC
  AE1542E0 6EBDC1BB B887373A 4A5D4ED1 1C6B5AB7 28A7EC80 F33DD62F BD8BE304
  983310F1 B51224BB 643843FD 1E651C8D AE1AA2C9 FB8F8317 A74E3F96 DAA32B2A
  E6A6870D 2FD40BF1 66CC0A13 3ADEFB30 CFB1A134 DAC2ABCA E9AE3B42 85BE2B24
  135164B2 27499004 D5B61041 02D5BB4B B9C7C664 02F09FDB CB5AC7C7 ED946825
  CAF8D6CA C3222D90 76F42AF4 57B5D6C6 02039930 6FCA55F3 E79BCF75 924F242B
  B1121CAA E3E12A03 7D0DB7C5 63EFDAA4 B842
        quit
crypto pki certificate chain SLA-TrustPoint
license udi pid CISCO2901/K9 sn FCZ194163BZ
license boot module c2900 technology-package securityk9
!
!
memory free low-watermark processor 68094
username admin secret 5 $1$uxvj$XztU/eGgrc0C/FRoYCCsL/
!
redundancy
!
!
ip ssh version 2
!
!
!
!
interface Embedded-Service-Engine0/0
 no ip address
 shutdown
!
interface GigabitEthernet0/0
 no ip address
 ip virtual-reassembly in
 shutdown
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 no ip address
 ip nat inside
 ip virtual-reassembly in
 shutdown
 duplex auto
 speed auto
!
interface GigabitEthernet0/1.210
 encapsulation dot1Q 210
 ip address 192.168.210.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
!
interface GigabitEthernet0/1.220
 encapsulation dot1Q 220
 ip address 192.168.220.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
!
interface GigabitEthernet0/1.230
 encapsulation dot1Q 230
 ip address 192.168.230.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
!
interface GigabitEthernet0/1.240
 encapsulation dot1Q 240
 ip address 192.168.240.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
!
interface GigabitEthernet0/1.250
 encapsulation dot1Q 250
 ip address 192.168.250.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
!
interface Serial0/0/0
 ip address 10.0.2.2 255.255.255.252
 ip nat inside
 ip virtual-reassembly in
 clock rate 2000000
!
interface Serial0/0/1
 no ip address
 shutdown
 clock rate 2000000
!
router ospf 1
 router-id 3.3.3.3
 passive-interface GigabitEthernet0/1
 network 10.0.2.0 0.0.0.3 area 0
 network 192.168.210.0 0.0.0.255 area 0
 network 192.168.220.0 0.0.0.255 area 0
 network 192.168.230.0 0.0.0.255 area 0
 network 192.168.240.0 0.0.0.255 area 0
 network 192.168.250.0 0.0.0.255 area 0
!
ip forward-protocol nd
!
ip http server
ip http authentication local
ip http secure-server
!
ip route 0.0.0.0 0.0.0.0 10.0.2.1
!
!
!
access-list 1 permit any
!
control-plane
!
!
!
line con 0
 stopbits 1
line aux 0
line 2
 no activation-character
 no exec
 transport preferred none
 transport output pad telnet rlogin lapb-ta mop udptn v120 ssh
 stopbits 1
line vty 0 4
 login local
 transport input ssh
line vty 5 15
 login local
 transport input ssh
!
scheduler allocate 20000 1000
!
end
```