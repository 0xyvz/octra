# 🛠️ OCTRA Testnet Kurulum ve Kullanım Rehberi (Güncel Sürümlerle)

Bu rehber OCTRA testnet ortamında cüzdan oluşturma, test token alma ve işlemleri yapmayı adım adım açıklar.

---

## 1. Ortam Hazırlığı

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git curl wget tmux screen clang jq btop htop -y
```

---

## 2. Cüzdan Oluşturma

### CLI ile Tek Komut Kurulum

```bash
bash <(curl -s https://raw.githubusercontent.com/octra-labs/octra-wallet-cli/main/install.sh)
```

Kurulum sonunda ekranda çıkan `privateKey` ve `address` değerlerini mutlaka kaydet.

---

## 3. Web Panel ile Cüzdan Oluşturma

```bash
wget https://github.com/octra-labs/wallet-gen/releases/download/v4/wallet-generator-linux-x64.tar.gz
tar -xzvf wallet-generator-linux-x64.tar.gz
chmod +x wallet-generator-linux-x64
./wallet-generator-linux-x64
```

Ardından tarayıcıda `http://localhost:8888` adresine girip cüzdan oluşturabilirsin.

---

## 4. Faucet'ten Test Token Alma

Oluşturduğun cüzdan adresini şu adrese yapıştırarak test token alabilirsin:  
🔗 https://faucet.octra.network/

---

## 5. İşlem Aracı Kurulumu (Encrypt, Transfer, Decrypt)

```bash
git clone https://github.com/octra-labs/octra_pre_client.git
cd octra_pre_client
chmod +x run.sh
nano wallet.json
```

### wallet.json Örneği

```json
{
  "priv": "cüzdanprivatekeyiniburayayaz",
  "addr": "octilebaslayancuzdanadresiniz",
  "rpc": "https://octra.network"
}
```

Dosyayı kendi bilgilerinle doldur ve kaydet.

---

### Ardından aracı çalıştır:

```bash
./run.sh
```

---

## 6. Panelde Sunulan İşlemler

- `[4] Encrypt`  
- `[6] Private Transfer`  
- `[5] Decrypt`  
- `[7] Claim`  

İşlem sonrasında her zaman explorer'dan işlem durumunu kontrol et:  
🔍 https://explorer.octra.network/

---

## 7. Screen ile Arka Planda Çalıştırma

```bash
screen -S octra
./run.sh
```

Screen oturumundan çıkmak için: `CTRL+A`, sonra `D`  
Yeniden bağlanmak için:  
```bash
screen -r octra
```

---

## Notlar

- Private key'ini asla kimseyle paylaşma.  
- Sunucu yeniden başlarsa `screen` ile işlemi tekrar başlatmayı unutma.

---

## Katkı ve Lisans

Bu rehber topluluk katkısı ile güncellenmektedir. Katkıda bulunmak istersen PR gönder.  
Lisans: MIT
