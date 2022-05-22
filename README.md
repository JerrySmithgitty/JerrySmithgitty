- 👋 Hi, I’m @JerrySmithgitty
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
JerrySmithgitty/JerrySmithgitty is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
Hostname wijzigen
Switch#
Switch#configure terminal
Switch(config)#hostname blabla
blabla(config)#

ww maken 
line console 0
Switch (config-line)#password [wachtwoord]
Switch (config-line)#login
Switch (config-line)#exit

Priveledge-mode beveiligen enabel
Switch(config)#enabel secret [wachtwoord]
- Switch(config)#enabel secret [wachtwoord] of - Switch(config)#enabel password [wachtwoord]

Leesbare wachtwoorden versleutelen
switch(config)#service password-encryption
 
Login Banner
Switch(config)#banner motd $ Authorized Access Only! $

Vlan shit

Aanmaken 
SW01#config terminal
SW01(config)#vlan 2
SW01(config-vlan)#name IT
SW01(config-vlan)#exit
SW01(config)#vlan 3
SW01(config-vlan)#name HR
SW01(config-vlan)#exit
SW01(config)#vlan 4
SW01(config-vlan)#name verkoop
SW01(config-vlan)#exit
SW01(config)#
Show vlan

Verwijderen
SW01#config terminal
SW01(config)#no vlan 2

Switch beher en confi
show interfaces status
confi 
#switchport mode ?

Operational mode van de switchpoort
Access poort:
Switch(config-if)#switchport mode
Access
Switch(config-if)#
Trunk poort:
Switch(config-if)#switchport mode
Trunk
Switch(config-if)

Een switchpoort toekennen aan een VLAN
Switch(config-if)#switchport mode
Access
Switch(config-if)#switchport access
vlan 10

Default-gateway
Switch#configure terminal
Switch(config)#ip default-gateway [IP adres router]


Ssh
Het maken van een certificaat gaat als volgt:
Switch(config)#hostname [hostname]
Switch(config)#ip domain-name [domeinnaam]
Switch(config)# crypto key generate rsa


Virtuele consolepoort
Switch(config)#username [gebruikersnaam] secret [wachtwoord]
Bijvoorbeeld:
Switch(config)#username beheerder secret C1sc0#

Vty poorten confi
Switch#config terminal
Switch(config)#line vty 0 15
Switch(config-line)#transport input ssh
Switch(config-line)#login local
Switch(config-line)#exit
Switch(config)#ip ssh version 2
Wifi zooi
Confi aP 
ap# Enable
ap# Conf t
ap(config)#Dot11 ssid [SSID_NAAM_1]
ap(config-ssid)# Vlan [ID_1]
ap(config-ssid)# authentication open
ap(config-ssid)# authentication key-management wpa version 2
ap(config-ssid)# wpa-psk ascii ciscopassword
ap(config-ssid)# Mbssid Guest-mode
ap(config-ssid)# End
ap(config)#
ap(config)#Dot11 ssid [SSID_NAAM_2]
ap(config-ssid)# Vlan [ID_2]
ap(config-ssid)# authentication open
ap(config-ssid)# authentication key-management wpa version 2
ap(config-ssid)# wpa-psk ascii ciscopassword
ap(config-ssid)# Mbssid Guest-mode
ap(config-ssid)# End
ap(config)#

confi encryptie
AP#conf t
AP(config)# Int dot11 0
AP(config-if)# Mbssid
AP(config-if)# encryption vlan [ID_1] mode ciphers aes-ccm
AP(config-if)# encryption vlan [ID_2] mode ciphers aes-ccm
AP(config-if)# ssid [SSID_NAAM_1]
AP(config-if)# ssid [SSID_NAAM_2]
AP(config-if)# no shut

Confi sub inter 2.4 radio en ethernet
AP# configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
AP(config)# interface Dot11Radio0.[vlan_ID_1]
AP(config-subif)# encapsulation dot1Q [vlan_ID_1]
AP(config-subif)#bridge group [vlan_ID_1]
AP(config-subif)# interface GigabitEthernet0.[vlan_ID_1]
AP(config-subif)#bridge group [vlan_ID_1]
AP(config-subif)# encapsulation dot1Q [vlan_ID_1]
AP(config-subif)# end
AP# write memory
AP(config)# interface Dot11Radio0.[vlan_ID_2]
AP(config-subif)# encapsulation dot1Q [vlan_ID_2]
AP(config-subif)#bridge group [vlan_ID_2]
AP(config-subif)# interface FastEthernet0.[vlan_ID_2]
AP(config-subif)#bridge group [vlan_ID_2]
AP(config-subif)# encapsulation dot1Q [vlan_ID_2]
AP(config-subif)# end
AP# write memory
Confi de switch
ST_SW_01> enable
ST_SW_01# conf t
ST_SW_01(config)#int fa1/0/21
ST_SW_01(config-if)# switchport trunk allowed vlan 20,25 (voorbeeld)
ST_SW_01(config-if)# switchport trunk encapsulation dot1q
ST_SW_01(config-if)# switchport mode trunk
ST_SW_01(config-if)# switchport trunk native vlan 99
end




Beheer ap via manament interface
ap> enable
ap# Conf t
ap# Int bvi 1
ap(config-if)# ip address 10.10.99.252 255.255.255.0
ap(config-if)# no shut
ap(config-if)# end




