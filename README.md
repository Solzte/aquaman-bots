# 🤖 Aquaman Bots - Discord Bot Sistemi

Çoklu modül destekli, kapsamlı Discord sunucu yönetim botu.

## 📋 Gereksinimler

- **Node.js** v18.0.0 veya üzeri
- **MongoDB** (yerel veya uzak)
- **Discord Bot Token(ları)**

## 🚀 Kurulum

### 1. Bağımlılıkları Yükle

```bash
npm install
```

### 2. Konfigürasyon

`Global/Settings/System.js` dosyasını düzenleyin:

```javascript
module.exports = {
  // Sunucu bilgileri
  serverID: "SUNUCU_ID", // Discord sunucu ID'niz
  serverName: "SUNUCU_ADI", // Sunucu adınız
  ownerID: ["SAHIP_ID_1", "SAHIP_ID_2"], // Sunucu sahiplerinin ID'leri
  channelID: "LOG_KANAL_ID", // Log kanalı ID'si
  database: "mongodb://localhost:27017/VERITABANI_ADI", // MongoDB bağlantı URL'i

  // Bot durumu
  Presence: {
    Status: "dnd", // online, idle, dnd, invisible
    Type: ActivityType.Playing, // Playing, Watching, Listening, Streaming
    Message: ["Durum mesajınız"],
  },

  // Webhook'lar (opsiyonel)
  Monitor: [
    { ID: "System", Webhook: "WEBHOOK_URL" },
    { ID: "Servers", Webhook: "WEBHOOK_URL" },
    { ID: "Feedbacks", Webhook: "WEBHOOK_URL" },
    { ID: "Bugs", Webhook: "WEBHOOK_URL" },
  ],

  // Ana botlar
  Main: {
    Mainframe: "ANA_BOT_TOKEN", // Ana bot token'ı
    Elixir: "ELIXIR_BOT_TOKEN", // Elixir bot token'ı
    Point: "POINT_BOT_TOKEN", // Point bot token'ı
    Prefix: ["."], // Komut prefix'i
  },

  // Hoşgeldin botları
  Welcome: {
    Tokens: [
      "WELCOME_BOT_1_TOKEN",
      "WELCOME_BOT_2_TOKEN",
      // ... daha fazla eklenebilir
    ],
    Channels: [
      "HOSGELDIN_KANAL_1_ID",
      "HOSGELDIN_KANAL_2_ID",
      // ... daha fazla eklenebilir
    ],
  },

  // Güvenlik botları
  Security: {
    Logger: "LOGGER_BOT_TOKEN",
    Punish: "PUNISH_BOT_TOKEN",
    Backup: "BACKUP_BOT_TOKEN",
    Dists: [
      "DIST_BOT_1_TOKEN",
      // ... daha fazla eklenebilir
    ],
    BotsIDs: [
      "BOT_1_ID",
      "BOT_2_ID",
      // ... tüm bot ID'leri
    ],
    Prefix: "!",
  },
};
```

### 3. Çekiliş Verilerini Temizle

Yeni kurulum için `Global/Settings/Server/Giveaways.json` dosyasını temizleyin:

```json
[]
```

### PM2 ile Tüm Botları Başlatma

```bash
# PM2 kurulumu (ilk seferde)
npm install -g pm2

# Tüm botları başlat
pm2 start ecosystem.config.js

# Durumu kontrol et
pm2 status

# Logları görüntüle
pm2 logs

# Botları durdur
pm2 stop all

# Botları yeniden başlat
pm2 restart all
```

## 🔧 Bot Modülleri

| Modül               | Açıklama                                   |
| ------------------- | ------------------------------------------ |
| **Mainframe**       | Ana bot - tüm komutlar ve temel özellikler |
| **Elixir**          | Yardımcı bot - ek özellikler               |
| **Point**           | Puan/XP sistemi                            |
| **Guardian Logger** | Sunucu log sistemi                         |
| **Guardian Punish** | Ceza sistemi                               |
| **Guardian Backup** | Yedekleme sistemi                          |
| **Welcomes**        | Hoşgeldin mesajları                        |

## 📝 Discord Bot Oluşturma

1. [Discord Developer Portal](https://discord.com/developers/applications)'a gidin
2. "New Application" butonuna tıklayın
3. Bot sekmesine gidin ve "Add Bot" tıklayın
4. "Reset Token" ile token'ı kopyalayın
5. **Privileged Gateway Intents** bölümünden tüm intent'leri açın:
   - Presence Intent
   - Server Members Intent
   - Message Content Intent
6. OAuth2 > URL Generator'dan botu sunucuya davet edin:
   - Scopes: `bot`, `applications.commands`
   - Permissions: `Administrator`

## ⚠️ Önemli Notlar

- Token'larınızı **asla** paylaşmayın
- MongoDB'nin çalıştığından emin olun
- Tüm bot intent'lerinin açık olduğundan emin olun
- Her bot için ayrı uygulama oluşturmanız gerekir
