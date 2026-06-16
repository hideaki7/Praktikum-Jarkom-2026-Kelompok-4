# Laporan Tugas Modul 5-Vlan-Trunk-OSPF-MultiVendor

## Tugas Modul 1 — Konfigurasi Cisco Switch Jakarta

Cisco Switch Jakarta dikonfigurasi untuk membuat VLAN 10, 20, dan 60, mengatur port access ke masing-masing client dan Ubuntu Server, serta mengaktifkan trunk ke Cisco Router dan MikroTik Router agar semua VLAN dapat melewatinya.

**Hasil yang Diharapkan**
- VLAN 10, 20, dan 60 berhasil dibuat
- Client VLAN 10, 20, dan Ubuntu Server berada pada VLAN yang benar
- Link trunk ke Cisco Router dan MikroTik Router aktif membawa VLAN 10, 20, dan 60

**Bukti Konfigurasi**

1. Topologi jaringan sisi Jakarta

![Topologi Jakarta](image/.png)

2. Screenshot `show vlan brief` untuk membuktikan VLAN 10, 20, dan 60 berhasil dibuat

![show vlan brief](image/show%20vlan%20brief%20switch%20jakarta.png)

3. Screenshot `show interfaces trunk` untuk membuktikan trunk ke Cisco Router dan MikroTik Router aktif membawa VLAN 10, 20, dan 60

![show interfaces trunk](image/show%20interfaces%20trunk%20switch%20jakarta.png)

---

## Tugas Modul 2 — Konfigurasi Cisco Router Jakarta

Cisco Router Jakarta dikonfigurasi dengan subinterface untuk VLAN 10, 20, dan 60, menjalankan VRRP sebagai master untuk VLAN 10 dan 60, mengaktifkan DHCP Relay menuju Ubuntu Server Jakarta, serta mengkonfigurasi link ke FortiGate Jakarta.

**Hasil yang Diharapkan**
- Subinterface VLAN 10, 20, dan 60 aktif dengan IP masing-masing
- Cisco Router menjadi VRRP master untuk VLAN 10 dan 60
- DHCP Relay berhasil meneruskan request ke Ubuntu Server
- Cisco Router dapat terhubung ke FortiGate Jakarta

**Bukti Konfigurasi**

1. Screenshot `show ip interface brief` untuk membuktikan subinterface VLAN 10, 20, dan 60 aktif dengan IP masing-masing

![show ip interface brief](image/show%20ip%20interface%20brief%20router%20jakarta.png)

2. Screenshot `show vrrp brief` untuk membuktikan Cisco Router menjadi VRRP master untuk VLAN 10 dan 60

![show vrrp brief](image/show%20vrrp%20brief%20router%20jakarta.png)

3. Screenshot konfigurasi subinterface VLAN 10, 20, dan 60 pada Cisco Router Jakarta

![Konfigurasi Subinterface](image/konfigurasi%20subinterface%20router%20jakarta.png)

4. Screenshot ping dari Cisco Router ke FortiGate Jakarta (10.10.100.1) untuk membuktikan konektivitas antar perangkat

![Ping ke FortiGate](image/ping%20dari%20Cisco%20Router%20ke%20FortiGate%20Jakarta.png)

---

## Tugas Modul 3 — Konfigurasi MikroTik Router Jakarta

MikroTik Router Jakarta dikonfigurasi dengan VLAN interface untuk VLAN 10, 20, dan 60, menjalankan VRRP sebagai master untuk VLAN 20, mengaktifkan DHCP Relay menuju Ubuntu Server Jakarta, serta mengkonfigurasi link dan default route ke FortiGate Jakarta.

**Hasil yang Diharapkan**
- VLAN interface untuk VLAN 10, 20, dan 60 aktif
- MikroTik menjadi VRRP master untuk VLAN 20
- DHCP Relay berhasil meneruskan request ke Ubuntu Server
- MikroTik dapat terhubung ke FortiGate Jakarta

**Bukti Konfigurasi**

1. Screenshot keseluruhan konfigurasi MikroTik Router Jakarta mencakup `/ip address print`, `/interface vrrp print`, `/ip dhcp-relay print`, `/ip route print`, dan ping ke FortiGate Jakarta

![Konfigurasi MikroTik Router Jakarta](image/tumod%203%20%28semua%29.png)

---

## Tugas Modul 4 — Konfigurasi Ubuntu Server Jakarta

Ubuntu Server Jakarta dikonfigurasi dengan IP static pada VLAN 60, menjalankan ISC-DHCP Server untuk melayani VLAN 10 dan VLAN 20, serta menginstall Nginx sebagai web server Jakarta.

**Bukti Konfigurasi**

1. Screenshot keseluruhan konfigurasi Ubuntu Server Jakarta
![Konfigurasi Ubuntu Server Jakarta](image/Konfigurasi%20Ubuntu%20Server%20Jakarta.png)

2. Screenshot `ip a` untuk membuktikan IP static 192.168.60.10/24 terkonfigurasi pada interface eth0
![ip a Ubuntu Jakarta](image/4.5.jpg)

3. Screenshot `ip route` untuk membuktikan default gateway mengarah ke VRRP virtual IP VLAN 60
![ip route Ubuntu Jakarta](image/4.6.jpg)

4. Screenshot `sudo cat /etc/dhcp/dhcpd.conf` untuk membuktikan DHCP pool VLAN 10 dan VLAN 20 terkonfigurasi
![dhcpd.conf Ubuntu Jakarta](image/4.8.jpg)

5. Screenshot `ping 8.8.8.8` untuk membuktikan Ubuntu Server dapat mengakses internet
![ping 8.8.8.8 Ubuntu Jakarta](image/4.9.jpg)

6. Screenshot client VLAN 10 mendapat IP DHCP dari Ubuntu Server
![DHCP client VLAN 10 Jakarta](image/4.10.png)

7. Screenshot client VLAN 20 mendapat IP DHCP dari Ubuntu Server
![DHCP client VLAN 20 Jakarta](image/4.11.png)

8. Screenshot tampilan web Nginx diakses dari browser sebagai bukti web server Jakarta aktif
![Nginx dari browser](image/4.13.jpeg)

---

## Tugas Modul 5 — Konfigurasi FortiGate Jakarta

**Bukti Konfigurasi**

1. Screenshot konfigurasi FortiGate Jakarta bagian 1 mencakup konfigurasi interface dan routing
![FortiGate Jakarta part 1](image/FortiGate_Jakarta_part_1.png)

2. Screenshot konfigurasi FortiGate Jakarta bagian 2 mencakup konfigurasi GRE Tunnel dan OSPF
![FortiGate Jakarta part 2](image/FortiGate_Jakarta_part_2.png)

3. Screenshot `get router info routing-table all` untuk membuktikan routing table FortiGate Jakarta lengkap termasuk route Surabaya
![routing-table-all FortiGate Jakarta](image/5.3.jpg)

4. Screenshot firewall policy untuk membuktikan policy dari jaringan Jakarta ke internet aktif dengan NAT
![Firewall Policy FortiGate Jakarta](image/5.4.jpeg)

5. Screenshot `ping 8.8.8.8` untuk membuktikan FortiGate Jakarta dapat mengakses internet
![ping 8.8.8.8 FortiGate Jakarta](image/5.5.jpg)

6. Screenshot ping ke IP tunnel Surabaya (172.16.0.2) untuk membuktikan GRE Tunnel aktif
![ping tunnel Surabaya FortiGate Jakarta](image/5.6.jpg)

7. Screenshot `get router info ospf neighbor` untuk membuktikan OSPF neighbor dengan FortiGate Surabaya berstatus Full
![ospf neighbor FortiGate Jakarta](image/5.8.jpg)

8. Screenshot `get router info routing-table ospf` untuk membuktikan route VLAN Surabaya diterima melalui OSPF
![routing-table ospf FortiGate Jakarta](image/5.7.jpeg)

9. Screenshot `get system interface physical` untuk membuktikan interface ke Cisco Router, MikroTik Router, dan MikroTik ISP aktif
![interface physical FortiGate Jakarta](image/5.9.jpg)

---

## Tugas Modul 6 — Konfigurasi MikroTik ISP

**Bukti Konfigurasi**

1. Screenshot keseluruhan konfigurasi MikroTik ISP mencakup IP address, route, dan NAT masquerade
![Konfigurasi MikroTik ISP](image/Konfigurasi%20MikroTik%20ISP.png)

2. Screenshot `ping 8.8.8.8` untuk membuktikan MikroTik ISP dapat mengakses internet
![ping 8.8.8.8 MikroTik ISP](image/6.2.png)

3. Screenshot ping antar-WAN FortiGate untuk membuktikan FortiGate Jakarta dan Surabaya saling reachable melalui ISP
![ping antar-WAN FortiGate](image/6.3.png)

---

## Tugas Modul 7 — Konfigurasi Switch dan MikroTik Surabaya

**Bukti Konfigurasi**

1. Screenshot keseluruhan konfigurasi Cisco Switch Surabaya mencakup VLAN dan trunk
![Konfigurasi Cisco Switch Surabaya](image/Konfigurasi%20Cisco%20Switch%20Surabaya.png)

2. Screenshot keseluruhan konfigurasi MikroTik Router Surabaya mencakup IP address, DHCP server, dan routing
![Konfigurasi MikroTik Router Surabaya](image/Konfigurasi%20MikroTik%20Router%20Surabaya.png)

3. Screenshot client VLAN 30 mendapat IP DHCP dari MikroTik Surabaya
![DHCP client VLAN 30 Surabaya](image/4.3.jpg)

4. Screenshot ping client VLAN 30 ke gateway (192.168.30.1)
![ping gateway VLAN 30 Surabaya](image/4.4.jpg)

5. Screenshot client VLAN 40 menggunakan IP static
![IP static client VLAN 40 Surabaya](image/4.1.jpg)

6. Screenshot ping client VLAN 40 ke gateway (192.168.40.1)
![ping gateway VLAN 40 Surabaya](image/4.2.jpg)

7. Screenshot ping client Surabaya ke 8.8.8.8 untuk membuktikan akses internet
![ping 8.8.8.8 client Surabaya](image/4.2.jpg)

## Tugas Modul 8 — Konfigurasi FortiGate Surabaya

FortiGate Surabaya dikonfigurasi sebagai edge firewall dan GRE endpoint sisi Surabaya, mengatur interface ke ISP dan MikroTik Surabaya, menambahkan route internal dan default route, membuat firewall policy untuk akses internet, serta mengkonfigurasi GRE Tunnel dan OSPF over GRE menuju FortiGate Jakarta.

**Hasil yang Diharapkan**
- FortiGate Surabaya dapat ping MikroTik ISP dan 8.8.8.8
- Client Surabaya dapat akses internet
- GRE Tunnel ke Jakarta aktif
- OSPF neighbor dengan FortiGate Jakarta berstatus Full
- Route Jakarta muncul di routing table FortiGate Surabaya

**Bukti Konfigurasi**

1. Screenshot konfigurasi FortiGate Surabaya bagian 1 mencakup konfigurasi interface dan routing

![FortiGate Surabaya part 1](image/FortiGate_Surabaya_part_1.png)

2. Screenshot konfigurasi FortiGate Surabaya bagian 2 mencakup konfigurasi GRE Tunnel dan OSPF

![FortiGate Surabaya part 2](image/FortiGate_Surabaya_part_2.png)

3. Screenshot `get system interface physical` untuk membuktikan interface ke ISP dan MikroTik Surabaya aktif

![interface physical FortiGate Surabaya](image/interface-physical-fortigate-surabaya.png)

4. Screenshot firewall policy untuk membuktikan policy dari jaringan Surabaya ke internet aktif dengan NAT

![Firewall Policy FortiGate Surabaya](image/firewall-policy-fortigate-surabaya.png)

5. Screenshot `ping 8.8.8.8` untuk membuktikan FortiGate Surabaya dapat mengakses internet

![ping 8.8.8.8 FortiGate Surabaya](image/ping-8888-fortigate-surabaya.png)

6. Screenshot ping ke IP tunnel Jakarta (172.16.0.1) untuk membuktikan GRE Tunnel aktif

![ping tunnel Jakarta FortiGate Surabaya](image/ping-tunnel-jakarta-fortigate-surabaya.png)

7. Screenshot `get router info ospf neighbor` untuk membuktikan OSPF neighbor dengan FortiGate Jakarta berstatus Full

![ospf neighbor FortiGate Surabaya](image/ospf-neighbor-fortigate-surabaya.png)

8. Screenshot `get router info routing-table ospf` untuk membuktikan route VLAN Jakarta diterima melalui OSPF

![routing-table ospf FortiGate Surabaya](image/routing-table-ospf-fortigate-surabaya.png)

---

## Tugas Modul 9 — Konfigurasi GRE Tunnel dan OSPF over GRE

GRE Tunnel dikonfigurasi antara FortiGate Jakarta dan FortiGate Surabaya sebagai jalur virtual antar-site. OSPF dijalankan di atas tunnel agar route jaringan Jakarta dan Surabaya dapat saling dipertukarkan secara dinamis melalui redistribute static route.

**Hasil yang Diharapkan**
- FortiGate Jakarta dan Surabaya dapat saling ping melalui IP tunnel
- OSPF neighbor antar-FortiGate berstatus Full
- Route VLAN Jakarta muncul di Surabaya dan sebaliknya
- Client Jakarta dan client Surabaya dapat saling ping

**Bukti Konfigurasi**

1. Screenshot implementasi GRE Tunnel dan OSPF over GRE pada FortiGate Jakarta bagian 1

![Implementasi GRE Tunnel FortiGate Jakarta part 1](image/Implementasi_GRE_Tunnel_%26_OSPF_over_GRE_Eksekusi_pada_FortiGate_Jakarta_part_1.png)

2. Screenshot implementasi GRE Tunnel dan OSPF over GRE pada FortiGate Jakarta bagian 2

![Implementasi GRE Tunnel FortiGate Jakarta part 2](image/Implementasi%20GRE%20Tunnel%20%26%20OSPF%20over%20GRE%20Eksekusi%20pada%20FortiGate%20Jakarta%20part%202.png)

3. Screenshot implementasi GRE Tunnel dan OSPF over GRE pada FortiGate Jakarta bagian 3

![Implementasi GRE Tunnel FortiGate Jakarta part 3](image/Implementasi%20GRE%20Tunnel%20%26%20OSPF%20over%20GRE%20Eksekusi%20pada%20FortiGate%20Jakarta%20part%203.png)

4. Screenshot implementasi GRE Tunnel dan OSPF over GRE pada FortiGate Surabaya bagian 1

![Implementasi GRE Tunnel FortiGate Surabaya part 1](image/Implementasi%20GRE%20Tunnel%20%26%20OSPF%20over%20GRE%20Eksekusi%20pada%20FortiGate%20Surabaya%20part%201.png)

5. Screenshot implementasi GRE Tunnel dan OSPF over GRE pada FortiGate Surabaya bagian 2

![Implementasi GRE Tunnel FortiGate Surabaya part 2](image/Implementasi%20GRE%20Tunnel%20%26%20OSPF%20over%20GRE%20Eksekusi%20pada%20FortiGate%20Surabaya%20part%202.png)

6. Screenshot implementasi GRE Tunnel dan OSPF over GRE pada FortiGate Surabaya bagian 3

![Implementasi GRE Tunnel FortiGate Surabaya part 3](image/Implementasi%20GRE%20Tunnel%20%26%20OSPF%20over%20GRE%20Eksekusi%20pada%20FortiGate%20Surabaya%20part%203.png)

7. Screenshot ping WAN antar-FortiGate untuk membuktikan IP WAN kedua FortiGate saling reachable

![ping WAN antar-FortiGate](image/ping-wan-antar-fortigate-modul9.png)

8. Screenshot `get router info ospf neighbor` dari FortiGate Jakarta untuk membuktikan OSPF neighbor berstatus Full

![ospf neighbor FortiGate Jakarta modul9](image/ospf-neighbor-fortigate-jakarta-modul9.png)

9. Screenshot `get router info routing-table ospf` dari FortiGate Jakarta untuk membuktikan route VLAN Surabaya diterima

![routing-table ospf FortiGate Jakarta modul9](image/routing-table-ospf-fortigate-jakarta-modul9.png)

---

## Tugas Modul 10 — Pengujian Akhir

Pengujian dilakukan pada seluruh perangkat untuk memastikan semua konfigurasi berjalan sesuai ketentuan, mulai dari DHCP, konektivitas internet, komunikasi antar-site melalui GRE Tunnel, hingga akses web server Jakarta dari Surabaya.

**Hasil yang Diharapkan**
- Seluruh client mendapatkan konfigurasi IP sesuai ketentuan
- Internet access berjalan pada sisi Jakarta dan Surabaya
- GRE Tunnel aktif dan OSPF neighbor berstatus Full
- Route antar-site tersebar melalui OSPF
- Web server Jakarta dapat diakses dari Surabaya
- Failover gateway Jakarta berjalan menggunakan VRRP

**Bukti Konfigurasi**

1. Screenshot konfigurasi Cisco Router Jakarta pada pengujian akhir

![Konfigurasi Router Jakarta](image/10.png)

2. Screenshot konfigurasi MikroTik Router Jakarta pada pengujian akhir

![Konfigurasi MikroTik Router Jakarta](image/20.png)

3. Screenshot client VLAN 10 Jakarta mendapat IP DHCP dari Ubuntu Server

![DHCP client VLAN 10 Jakarta final](image/dhcp-client-vlan10-jakarta-final.png)

4. Screenshot client VLAN 30 Surabaya mendapat IP DHCP dari MikroTik Surabaya

![DHCP client VLAN 30 Surabaya final](image/dhcp-client-vlan30-surabaya-final.png)

5. Screenshot ping internet dari client Jakarta

![ping internet Jakarta final](image/ping-internet-jakarta-final.png)

6. Screenshot ping internet dari client Surabaya

![ping internet Surabaya final](image/ping-internet-surabaya-final.png)

7. Screenshot ping antar-site (client Jakarta ke client Surabaya atau sebaliknya)

![ping antar-site final](image/ping-antar-site-final.png)

8. **[MASIH KURANG]** Screenshot akses web server Jakarta dari browser di sisi Surabaya

![Akses web server Jakarta dari Surabaya](image/nginx-jakarta-dari-surabaya.png)

9. **[MASIH KURANG]** Screenshot `get router info routing-table ospf` sebagai bukti route antar-site tersebar melalui OSPF

![routing table OSPF final](image/routing-table-ospf-final.png)
