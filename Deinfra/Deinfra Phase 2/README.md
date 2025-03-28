# DEINFRA PHASE II

## Catatan Penting (Prerequisites)
Sebelum menjalankan Panduan berikut ini, pastikan anda memiliki :
1. `Domain` (Bisa add dari domain anda, atau minta ke support, dan berikan IP Anda)
- Jika tidak punya domain sendiri, silahkan minta sama admin https://t.me/Vovike (Recommended), kasih aja IPmu
- Anda juga bisa minta ke saya, di telegram https://t.me/SaujanaOK saya bisa bantu buatkan gratis, kalau saya pas online. Send IP only. Rekomendasi saya sih minta sama admin deinfra saja.
- Hostname = Domain Name
2. Email Address
3. Link `upstream` didapat dari bot telegram deinfra https://t.me/thepowerio_bot saat mendaftar phase 2, dan ingat jumlah linknya biasanya ada 3, tapi kalau ternyata cuma ada 2, maka salah satu link gak papa masukin 2x di auto setup nya ya. Contoh pada gambar, itu juga akan menentukan dimana Chain kamu berada. Pada gambar tersebut, contohnya akan berada di chain 1043. Tentunya setiap orang bisa berbeda-beda. (**HARAP DIBACA DENGAN BAIK-BAIK AGAR PAHAM**)
<br/>![image](https://user-images.githubusercontent.com/85033021/227006864-62169d01-a92c-42df-8383-ff4ff0c6ec5d.png)

Nah siapkan data-data tersebut untuk mengikuti panduan ini, agar dapat bekerja dengan cepat dan terstruktur.

## Auto Set Up keperluan
```
wget -O dp2.sh https://raw.githubusercontent.com/SaujanaOK/Node-TestNet-Guide/main/Deinfra/Deinfra%20Phase%202/deinfraphase2.sh && chmod +x dp2.sh  && ./dp2.sh
```
### Pasca Installasi
```
source $HOME/.bashrc
```
## Install Socat
```
sudo -i
apt-get install socat
```
Langsung paste saja:
```
source $HOME/.bashrc
curl https://get.acme.sh | sh -s email=$Your_Email
```

## Seting SSL
Langsung paste saja:
```
source $HOME/.bashrc
acme.sh --issue --standalone --force -d $Your_Hostname
```

```
acme.sh --install-cert -d $Your_Hostname \
--cert-file /opt/thepower/db/cert/${Your_Hostname}.crt \
--key-file /opt/thepower/db/cert/${Your_Hostname}.key \
--ca-file /opt/thepower/db/cert/${Your_Hostname}.crt.ca.crt
acme.sh --info -d $Your_Hostname
```

## Run Docker
```
cd /opt/thepower
docker-compose up -d
```
## Check Node
```
curl https://${Your_Hostname}:1443/api/node/status | jq
```
```
curl http://${Your_Hostname}:1080/api/node/status | jq
```

## Logs Docker
```
cd /opt/thepower
docker-compose logs tpnode
```
or
```
docker-compose logs -f
```

## Jika ingin stop docker
```
cd /opt/thepower
docker-compose down
```
## Untuk link yang dikirim ke BOT Telegram
```
https://<Your_Hostname>:1443/api/node/status
```

## helper status checker
Dikasih admin Vladmir
```
curl -s https://raw.githubusercontent.com/giDai7ja/nodeutils/main/helper.sh | bash
```
___________________________
## Source
- https://medium.com/the-power-official-blog/deinfra-testnet-results-of-phase1-and-launch-of-phase-2-a45b96b82c72
- https://doc.thepower.io/docs/Community/phase-2/testnet-flow#prerequisites-for-a-node
