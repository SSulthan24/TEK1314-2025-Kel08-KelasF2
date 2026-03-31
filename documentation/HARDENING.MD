=========================
  HARDENING WINDOWS 11
=========================

1. Aktifkan Firewall:
netsh advfirewall set allprofiles state on

2. Izinkan ICMP (biar tetap bisa ping):
netsh advfirewall firewall add rule name="Allow ICMPv4" protocol=icmpv4 dir=in action=allow

3. Block Reverse Shell Port (contoh: 4444):
netsh advfirewall firewall add rule name="Block Reverse Shell" dir=out protocol=TCP localport=4444 action=block

4. Disable Guest Account:
net user guest /active:no

5. Set Password Policy:
net accounts /minpwlen:8
net accounts /maxpwage:30

6. Disable Service Tidak Perlu:
sc config RemoteRegistry start= disabled
net stop RemoteRegistry

7. Hardening PowerShell:
powershell -Command "Set-ExecutionPolicy Restricted -Force"

8. Aktifkan Audit Logging:
auditpol /set /category:* /success:enable /failure:enable
