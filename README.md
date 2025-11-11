# Tugas-Subnetting-Jarkom-Muhammad-Fatihul-023

## Topologi 

<img width="1183" height="705" alt="image" src="https://github.com/user-attachments/assets/e30959e3-36ea-4c20-bbbf-8902b840622a" />

## Base Network

- NRP : **5027241023**
- Aturan base network : `10.(NRP mod 256).0.0`
- Perhitungan : `5027241023 mod 256 = 63`
- **Base network (NRP)** : `10.63.0.0`
- **Subnet besar untuk VLSM** : `10.63.0.0/22`  

Subnet besar `10.63.0.0/22` ini yang kemudian dipecah-pecah menggunakan teknik **VLSM** sesuai kebutuhan setiap subnet pada topologi.

## Subnetting

| Subnet                             | Kebutuhan Host (termasuk router) | Netmask |
|------------------------------------|----------------------------------:|:-------:|
| Bidang Guru & Tendik              | 96 host                           | /25     |
| Bidang Kurikulum                  | 221 host                          | /24     |
| Bidang Sarana Prasarana           | 46 host                           | /26     |
| Bidang Pengawas Sekolah (Cabang)  | 19 host                           | /27     |
| Server & Admin                    | 7 host                            | /28     |
| Sekretariat                       | 381 host                          | /23     |
| Router Interlink                  | 6 host                            | /29     |
| Tunnel / VPN                      | 2 host                            | /30     |
| **TOTAL**                         | **778 host**                      | **/22** |

> Total 778 host ini, karena yang ditambah 1 hanya LAN-LAN  
> (Sekretariat, Kurikulum, Guru & Tendik, Sarpras, Pengawas, Server & Admin)  
> sementara **Router Interlink (6)** dan **Tunnel/VPN (2)** tetap.

## VLSM 

<img width="1328" height="693" alt="image" src="https://github.com/user-attachments/assets/3331e658-eda7-425f-a2a0-5afccea3642b" />


| Subnet                             | Kebutuhan Host (termasuk router) | Network ID    | Netmask         | Prefix | Block Size (alamat) | Usable Host | Range Host                     | Broadcast     |
|------------------------------------|----------------------------------:|--------------:|-----------------|:------:|--------------------:|------------:|--------------------------------|--------------|
| Sekretariat                       | 381                               | 10.63.0.0     | 255.255.254.0   | /23    | 512                 | 510         | 10.63.0.1 – 10.63.1.254        | 10.63.1.255  |
| Bidang Kurikulum                  | 221                               | 10.63.2.0     | 255.255.255.0   | /24    | 256                 | 254         | 10.63.2.1 – 10.63.2.254        | 10.63.2.255  |
| Bidang Guru & Tendik              | 96                                | 10.63.3.0     | 255.255.255.128 | /25    | 128                 | 126         | 10.63.3.1 – 10.63.3.126        | 10.63.3.127  |
| Bidang Sarana Prasarana           | 46                                | 10.63.3.128   | 255.255.255.192 | /26    | 64                  | 62          | 10.63.3.129 – 10.63.3.190      | 10.63.3.191  |
| Bidang Pengawas Sekolah (Cabang)  | 19                                | 10.63.3.192   | 255.255.255.224 | /27    | 32                  | 30          | 10.63.3.193 – 10.63.3.222      | 10.63.3.223  |
| Server & Admin                    | 7                                 | 10.63.3.224   | 255.255.255.240 | /28    | 16                  | 14          | 10.63.3.225 – 10.63.3.238      | 10.63.3.239  |
| Router Interlink                  | 6                                 | 10.63.3.240   | 255.255.255.248 | /29    | 8                   | 6           | 10.63.3.241 – 10.63.3.246      | 10.63.3.247  |
| Tunnel / VPN                      | 2                                 | 10.63.3.248   | 255.255.255.252 | /30    | 4                   | 2           | 10.63.3.249 – 10.63.3.250      | 10.63.3.251  |

> Semua subnet di atas masih berada di dalam **subnet besar 10.63.0.0/22**,  

## Tree VLSM 

<img width="1052" height="643" alt="image" src="https://github.com/user-attachments/assets/bd3b82a1-d7ff-4de4-92dc-2ecdfc932fa6" />

## CIDR

<img width="1581" height="701" alt="image" src="https://github.com/user-attachments/assets/ac7d3060-529a-4d5b-b713-fecb9d56375b" />

## Langkah 1 – Tentukan subnet & labelling (A1–A8)

Semua subnet hasil VLSM diberi label A1–A8 seperti di topologi Packet Tracer.

| Label | Subnet / Site                        | Network ID    | Prefix | Netmask         |
|------:|--------------------------------------|--------------:|:------:|-----------------| 
| A1    | Bidang Pengawas Sekolah (Cabang)    | 10.63.3.192   | /27    | 255.255.255.224 |
| A2    | Tunnel / VPN                         | 10.63.3.248   | /30    | 255.255.255.252 |
| A3    | Sekretariat                          | 10.63.0.0     | /23    | 255.255.254.0   |
| A4    | Bidang Kurikulum                     | 10.63.2.0     | /24    | 255.255.255.0   |
| A5    | Bidang Guru & Tendik                | 10.63.3.0     | /25    | 255.255.255.128 |
| A6    | Bidang Sarana Prasarana             | 10.63.3.128   | /26    | 255.255.255.192 |
| A7    | Server & Admin                      | 10.63.3.224   | /28    | 255.255.255.240 |
| A8    | Router Interlink                    | 10.63.3.240   | /29    | 255.255.255.248 |

Semua subnet di atas berada di dalam **subnet besar** 10.63.0.0/22.


### 2. Penggabungan ke B2 (gabungan A1 + A2)

| Langkah | Subnet yang Digabung              | Network ID Hasil | Prefix Hasil | Netmask Hasil     | Keterangan                      |
|--------:|-----------------------------------|-----------------:|:------------:|-------------------|----------------------------------|
| 1       | A1 (10.63.3.192/27)              | 10.63.3.192      | /26         | 255.255.255.192   | Rentang 10.63.3.192–10.63.3.255 |
|         | A2 (10.63.3.248/30)              |                  |             |                   | Termasuk di dalam blok /26 ini  |

Hasil penggabungan:

| Label Baru | Network ID    | Prefix | Netmask         | Berisi Subnet         |
|-----------:|--------------:|:------:|-----------------|-----------------------|
| **B2**     | 10.63.3.192   | /26    | 255.255.255.192 | A1 (Cabang) + A2 (VPN)|

> Secara diagram, B2 hanya diturunkan menjadi A1 dan A2 (seperti contoh temanmu).

---

### 3. Penggabungan ke B1 (gabungan A3–A8)

Di sisi lain, subnet A3–A8 dapat diringkas bertahap menjadi satu blok besar B1.

| Langkah | Subnet yang Digabung                                     | Network ID Hasil | Prefix Hasil | Netmask Hasil     | Keterangan                                   |
|--------:|----------------------------------------------------------|-----------------:|:------------:|-------------------|---------------------------------------------|
| 1       | A5 (10.63.3.0/25) + A6 (10.63.3.128/26) + A7 + A8 + A1+A2| 10.63.3.0        | /24         | 255.255.255.0     | Ringkasan semua 10.63.3.x                   |
| 2       | A4 (10.63.2.0/24) + blok 10.63.3.0/24                    | 10.63.2.0        | /23         | 255.255.254.0     | Ringkasan 10.63.2.x dan 10.63.3.x           |
| 3       | A3 (10.63.0.0/23) + blok 10.63.2.0/23                    | 10.63.0.0        | /22         | 255.255.252.0     | Ringkasan 10.63.0.0 – 10.63.3.255 (semua)   |

Hasil akhirnya:

| Label Baru | Network ID  | Prefix | Netmask       | Berisi Subnet                             |
|-----------:|------------:|:------:|---------------|-------------------------------------------|
| **B1**     | 10.63.0.0   | /22    | 255.255.252.0 | A3, A4, A5, A6, A7, A8 (dan juga A1, A2)  |

> Di diagram, B1 biasanya ditunjukkan sebagai lingkaran besar yang mencakup **semua subnet di topologi HQ + cabang**.

---

### 4. Penggabungan B1 dan B2 ke C1

Terakhir, kalau jaringan ini mau diiklankan lagi ke jaringan yang lebih besar (misal ISP), kita bisa buat satu supernet lagi:

| Langkah | Subnet yang Digabung          | Network ID Hasil | Prefix Hasil | Netmask Hasil     | Keterangan                        |
|--------:|-------------------------------|-----------------:|:------------:|-------------------|----------------------------------|
| 1       | B1 (10.63.0.0/22) + B2 (/26)  | 10.63.0.0        | /21         | 255.255.248.0     | Mencakup 10.63.0.0–10.63.7.255   |

Ringkasan terbesar:

| Label Baru | Network ID  | Prefix | Netmask       | Berisi Summary |
|-----------:|------------:|:------:|---------------|----------------|
| **C1**     | 10.63.0.0   | /21    | 255.255.248.0 | B1 dan B2      |

## Tree CIDR
<img width="1739" height="610" alt="image" src="https://github.com/user-attachments/assets/515047d2-6108-4aa2-bda4-525445b86332" />

