# 🛠️ OCTRA Testnet Kurulum ve Kullanım Rehberi (0'dan Başlayanlar için)

Bu rehber, OCTRA blockchain testnet ortamında cüzdan oluşturmak, token almak ve işlemler yapmak isteyenler için hazırlanmıştır.

---

## 📆 1. Ortam Hazırlığı

> Ubuntu / Debian sistemler için önerilir (WSL dahil)

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git curl wget tmux screen clang jq btop htop -y
```

---

## 🔐 2. Cüzdan Oluşturma

### Yöntem 1: Tek Komutla CLI Kurulumu

```bash
bash <(curl -s https://raw.githubusercontent.com/zunxbt/octra-wallet-cli/main/install.sh)
```

Kurulum sonrası çıkan `privateKey` ve `address` değerlerini bir yere kaydetmeyi unutma.

---

## 🌐 3. Web Panel ile Cüzdan Kullanımı

```bash
wget https://github.com/zunxbt/wallet-generator/releases/download/1.0.0/wallet-generator-linux-x64
chmod +x wallet-generator-linux-x64
./wallet-generator-linux-x64
```

> Ardından `localhost:8888` adresine tarayıcınızla girerek cüzdan oluşturabilirsiniz.

---

## 💧 4. Faucet'ten Test Token Al

Oluşturduğunuz cüzdan adresini şu siteye yapıştırarak test token alın:
🔗 [https://faucet.octra.network/](https://faucet.octra.network/)

---

## ⚙️ 5. İşlem Aracı Kurulumu (Encrypt, Transfer, Decrypt)

```bash
git clone https://github.com/zunxbt/octra_pre_client.git
cd octra_pre_client
chmod +x run.sh
nano wallet.json
```

### wallet.json Örneği

```json
{
  "wallet_address": "senin_adresin",
  "wallet_private_key": "senin_private_keyin"
}
```

### Ardından başlat:

```bash
./run.sh
```

---

## ↻ 6. Panel Üzerinden İşlemler

Panelde sunulan komutlar:

* `[4] Encrypt`
* `[6] Private Transfer`
* `[5] Decrypt`
* `[7] Claim`

> Her işlem sonrası explorer'dan kontrol edin:
> 🔍 [https://explorer.octra.network/](https://explorer.octra.network/)

---

## 🧠 7. Screen ile Arka Planda Çalıştırma

```bash
screen -S octra
./run.sh
```

Screen'den çıkmak için: `CTRL+A`, ardından `D`
Tekrar bağlanmak için:

```bash
screen -r octra
```

---

## ❗ Notlar

* Sunucu yeniden başlarsa `screen` ile işlemleri tekrar başlatmanız gerekir.
* Private key’inizi **asla** başkalarıyla paylaşmayın.

---

## 🤝 Katkı ve Lisans

Bu rehber topluluk katkısı ile güncellenmektedir. Katkıda bulunmak isterseniz PR gönderin.
Lisans: MIT
