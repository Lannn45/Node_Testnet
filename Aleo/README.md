
# ALEO NODE TESTNET 

##  Spesifiksi Minimal

Berikut adalah persyaratan minimum untuk menjalankan Node Aleo:


|  Komponen |  Persyaratan Minimum |
| ------------ | ------------ |
| CPU  | 16-core|
| RAM | 16GB RAM |
| Penyimpanan  | 128GB of storage (SSD or NVME) |

# Instal Otomatis 

```
wget -O prover.sh https://raw.githubusercontent.com/Lannn45/Node_Testnet/main/Aleo/aleo.sh && chmod +x prover.sh && ./prover.sh
```

Biarkan Instalisasi Selesai 

# Run Prover

```
cd snarkOS
screen -R aleo
```

```
./run-prover.sh
```
- Masukan Private Key Yang Sudah Kalian Backup Sebelumnya dan Diamkan Hingga Selesai. 
- `ctrl A D` untuk Menyimpan Screen Agar Jalan di Background Pc Kalian
- Jika anda Ingin Kembali ke Screen Yang Sedang Jalan, Gunakan Perintah `screen -Rd prover`

## Delete

```
rustup self uninstall
rm -rf prover.sh
rm -rf snarkOS
```
