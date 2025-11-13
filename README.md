# 💻 F1zuli1 Projeleri

Bu depo, benim **Python, SQL, Discord bot** ve **HTML/CSS** deneyimlerimi gösteren projelerimi içerir.  
Hem web tasarımı hem de Discord bot geliştirme çalışmaları burada bir arada.

---

## 🚀 Projeler

## 1️⃣ Mezuniyet Projesi (Web)
**[GitHub Repo](https://github.com/f1zuli1/mezuniyet-projesi)**  

🛠 **Teknolojiler:** ![HTML](https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white) | ![CSS](https://img.shields.io/badge/CSS-1572B6?style=for-the-badge&logo=css3&logoColor=white) | ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) 
🎨 Modern ve responsive web tasarım  
📄 Öğrenci projelerini görüntülemek için optimize edilmiş arayüz  

**Kurulum:**
```bash
git clone https://github.com/f1zuli1/mezuniyet-projesi.git
cd mezuniyet-projesi
Tarayıcıda index.html dosyasını açın.

Örnek HTML/CSS:

html
Kodu kopyala
<header>
  <h1>🎓 Mezuniyet Projesi</h1>
  <p>Hoşgeldiniz! Bu proje web tasarım becerilerimi gösterir.</p>
</header>
css
Kodu kopyala
header {
  background-color: #4caf50;
  color: white;
  text-align: center;
  padding: 20px;
}
```
## 2️⃣ DB-BOT English 0.1 (Discord Bot)
**[GitHub Repo](https://github.com/f1zuli1/DB-BOT-English-0.1)**  


🛠 Teknolojiler: ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) | ![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white) | ![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)
🤖 Discord üzerinden İngilizce öğrenmeyi destekleyen bot
💾 Veriler SQL veritabanında saklanır ve yönetilir

Kurulum:

Kodu kopyala
git clone https://github.com/f1zuli1/DB-BOT-English-0.1.git
cd DB-BOT-English-0.1
pip install -r requirements.txt
.env dosyası oluşturun ve bilgileri girin:

Kodu kopyala
DISCORD_TOKEN=YOUR_DISCORD_BOT_TOKEN
DATABASE_URL=sqlite:///database.db
Botu başlatın:


Örnek Python/Discord Bot Kodları:

## bot.py
```bash
import discord
from discord.ext import commands
import sqlite3
import os

bot = commands.Bot(command_prefix='!')

# Veritabanı bağlantısı
conn = sqlite3.connect('database.db')
c = conn.cursor()
c.execute('''
CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT,
    discord_id TEXT UNIQUE
)
''')
conn.commit()

@bot.event
async def on_ready():
    print(f'✅ {bot.user} giriş yaptı!')

@bot.command()
async def ekle(ctx, username):
    c.execute('INSERT INTO users (username, discord_id) VALUES (?, ?)', (username, str(ctx.author.id)))
    conn.commit()
    await ctx.send(f"✅ {username} başarıyla eklendi!")

bot.run(os.getenv('DISCORD_TOKEN'))
```


![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)
