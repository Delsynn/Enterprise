## Switch Configuratie Branch Office

Hierbij de configuratie voor de coreswitch van het branch office:

```
Building configuration...

Current configuration : 5936 bytes
!
! Last configuration change at 11:02:59 UTC Tue Dec 19 2023
!
version 15.2
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname Switchbranch
!
boot-start-marker
boot-end-marker
!
!
username admin privilege 15 secret 9 $9$WVoeQT1iEvWGeW$g0X8rabYR0yk29tIj2xx0N7IpSmZegmC0aP22sx23ho
no aaa new-model
switch 1 provision c1000-24t-4g-l
system mtu routing 1500
!
!
no ip domain-lookup
ip domain-name uclllabs.local
!
!
!
!
!
!
crypto pki trustpoint TP-self-signed-117245440
 enrollment selfsigned
 subject-name cn=IOS-Self-Signed-Certificate-117245440
 revocation-check none
 rsakeypair TP-self-signed-117245440
!
!
crypto pki certificate chain TP-self-signed-117245440
 certificate self-signed 01
  30820229 30820192 A0030201 02020101 300D0609 2A864886 F70D0101 05050030
  30312E30 2C060355 04031325 494F532D 53656C66 2D536967 6E65642D 43657274
  69666963 6174652D 31313732 34353434 30301E17 0D323331 30303531 31303530
  325A170D 33303031 30313030 30303030 5A303031 2E302C06 03550403 1325494F
  532D5365 6C662D53 69676E65 642D4365 72746966 69636174 652D3131 37323435
  34343030 819F300D 06092A86 4886F70D 01010105 0003818D 00308189 02818100
  AC5C3DE9 42FAB031 8C1133B5 8131F7D5 C7B3505F CD7B7FEA 6E79A91E E44A2C88
  CE098D25 9C82EF81 41F93809 E6B1F840 A6E124C7 DE6BCF30 0FB48150 745DDFF3
  9A94F23B 00F9527D 3B168C5D 93040DE1 A36DE154 FE7CCEDC 4B7F1CE2 851CFF56
  51DF7E20 DBA43D80 5E237B1A 9BD79DF0 57FDE1C0 988FAC23 91314FB2 E15B53F5
  02030100 01A35330 51300F06 03551D13 0101FF04 05300301 01FF301F 0603551D
  23041830 16801439 1FD01D83 33DADFFD 46C30076 10B81FC2 C3B86F30 1D060355
  1D0E0416 0414391F D01D8333 DADFFD46 C3007610 B81FC2C3 B86F300D 06092A86
  4886F70D 01010505 00038181 00123EB9 3EE9C0F2 CB2CB016 78BB4254 3DD0A6AF
  BB424FE8 3C8F447B 91757CFA 380001CA 40E6FACF 5DA69805 F17DD7CA 548B2A85
  22050398 325C860C 1B425141 79BF9F8C 0E26A77B BBB77DD9 C42369F8 BA8D252D
  FD90861D D39EADAB 12FD0375 7AD2444A 115F01B7 A38AC4A5 A401C214 D136F9CF
  2B2EE0D0 51CFA1DA 152C4DA9 43
        quit
!
spanning-tree mode rapid-pvst
spanning-tree extend system-id
!
vlan internal allocation policy ascending
!
!
!
!
!
!
interface GigabitEthernet1/0/1
 switchport trunk native vlan 99
 switchport mode trunk
!
interface GigabitEthernet1/0/2
 switchport access vlan 140
 switchport mode access
  switchport port-security violation restrict
 switchport port-security mac-address sticky
 switchport port-security aging time 60
 switchport port-security
!
interface GigabitEthernet1/0/3
 switchport access vlan 150
 switchport mode access
  switchport port-security violation restrict
 switchport port-security mac-address sticky
 switchport port-security aging time 60
 switchport port-security
!
interface GigabitEthernet1/0/4
 switchport access vlan 160
 switchport mode access
  switchport port-security violation restrict
 switchport port-security mac-address sticky
 switchport port-security aging time 60
 switchport port-security
!
interface GigabitEthernet1/0/5
 switchport access vlan 170
 switchport mode access
  switchport port-security violation restrict
 switchport port-security mac-address sticky
 switchport port-security aging time 60
 switchport port-security
!
interface GigabitEthernet1/0/6
 switchport access vlan 180
 switchport mode access
 switchport port-security violation restrict
 switchport port-security mac-address sticky
 switchport port-security aging time 60
 switchport port-security
!
interface GigabitEthernet1/0/7
 switchport access vlan 190
 switchport mode access
 switchport port-security violation restrict
 switchport port-security mac-address sticky
 switchport port-security aging time 60
 switchport port-security
!
interface GigabitEthernet1/0/8
 switchport access vlan 200
 switchport mode access
 switchport port-security violation restrict
 switchport port-security mac-address sticky
 switchport port-security aging time 60
 switchport port-security
!
interface GigabitEthernet1/0/9

!
interface GigabitEthernet1/0/10

!
interface GigabitEthernet1/0/11

!
interface GigabitEthernet1/0/12

!
interface GigabitEthernet1/0/13

!
interface GigabitEthernet1/0/14

!
interface GigabitEthernet1/0/15

!
interface GigabitEthernet1/0/16

!
interface GigabitEthernet1/0/17

!
interface GigabitEthernet1/0/18
!
interface GigabitEthernet1/0/19
!
interface GigabitEthernet1/0/20
!
interface GigabitEthernet1/0/21
!
interface GigabitEthernet1/0/22
!
interface GigabitEthernet1/0/23
!
interface GigabitEthernet1/0/24
!
interface GigabitEthernet1/0/25
!
interface GigabitEthernet1/0/26
!
interface GigabitEthernet1/0/27
!
interface GigabitEthernet1/0/28
!
interface Vlan1
 no ip address
!
ip http server
ip http secure-server
!
!
!
!
line con 0
line vty 0 4
 login
 transport input none
line vty 5 15
 login local
 transport input ssh
!
end
```
