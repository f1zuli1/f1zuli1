# 💻 F1zuli1 Projeleri

Bu depo, benim **Python, SQL, Discord bot** ve **HTML/CSS** deneyimlerimi gösteren projelerimi içerir.  
Hem web tasarımı hem de Discord bot geliştirme çalışmaları burada bir arada.

---

## 🚀 Projeler

### 1️⃣ Mezuniyet Projesi (Web)
**[GitHub Repo](https://github.com/f1zuli1/mezuniyet-projesi)**  

🛠 **Teknolojiler:** `HTML` | `CSS` | `JavaScript`  
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
2️⃣ DB-BOT English 0.1 (Discord Bot)
GitHub Repo

🛠 Teknolojiler: Python | SQL | Discord.py
🤖 Discord üzerinden İngilizce öğrenmeyi destekleyen bot
💾 Veriler SQL veritabanında saklanır ve yönetilir

Kurulum:

bash
Kodu kopyala
git clone https://github.com/f1zuli1/DB-BOT-English-0.1.git
cd DB-BOT-English-0.1
pip install -r requirements.txt
.env dosyası oluşturun ve bilgileri girin:

ini
Kodu kopyala
DISCORD_TOKEN=YOUR_DISCORD_BOT_TOKEN
DATABASE_URL=sqlite:///database.db
Botu başlatın:

bash
Kodu kopyala
python bot.py
Örnek Python/Discord Bot Kodları:

python
Kodu kopyala
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
