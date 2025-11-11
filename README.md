# Tugas-Subnetting-Jarkom-Muhammad-Fatihul-023

## Topologi 

<img width="1183" height="705" alt="image" src="https://github.com/user-attachments/assets/e30959e3-36ea-4c20-bbbf-8902b840622a" />

## Base Network

- NRP : **5027241023**
- Peraturan base network : `10.(NRP mod 256).0.0`
- Perhitungan : `5027241023 mod 256 = 63`
- **Base network** : `10.63.0.0`

## Subnetting

> Tabel ini merangkum setiap subnet, kebutuhan host, prefix, block size, dan info network/broadcast secara singkat.

| Subnet / Site                            | Kebutuhan Host | Prefix | Block Size (jumlah alamat) | Keterangan Tambahan       | Aba (Network / Broadcast)              |
|------------------------------------------|---------------:|:------:|---------------------------:|---------------------------|----------------------------------------|
| Sekretariat (HQ)                         | 380            | /23    | 512                        | VLAN 10                   | 10.63.0.0 / 10.63.1.255                |
| Bidang Kurikulum (HQ)                    | 220            | /24    | 256                        | VLAN 20                   | 10.63.2.0 / 10.63.2.255                |
| Bidang Guru & Tendik (HQ)               | 95             | /25    | 128                        | VLAN 30                   | 10.63.3.0 / 10.63.3.127                |
| Bidang Sarana Prasarana (HQ)            | 45             | /26    | 64                         | VLAN 40                   | 10.63.3.128 / 10.63.3.191              |
| Server & Admin (HQ)                      | 6              | /29    | 8                          | VLAN 50                   | 10.63.3.224 / 10.63.3.231              |
| Link R-HQ ↔ R-Branch (point-to-point)    | 2              | /30    | 4                          | Serial / P2P              | 10.63.3.232 / 10.63.3.235              |
| Bidang Pengawas Sekolah (Branch)        | 18             | /27    | 32                         | LAN Cabang                | 10.63.4.0 / 10.63.4.31                 |

