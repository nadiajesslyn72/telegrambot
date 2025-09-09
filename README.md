telegram-bot-example/
│── bot.py
│── requirements.txt
│── README.md

from telegram import Update
from telegram.ext import Application, CommandHandler, MessageHandler, filters, ContextTypes

# Ganti dengan token bot kamu dari BotFather
BOT_TOKEN = "ISI_TOKEN_BOTMU_DI_SINI"

# Fungsi untuk command /start
async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(
        "Halo 👋! Saya adalah bot Telegram sederhana.\nKetik /help untuk melihat perintah."
    )

# Fungsi untuk command /help
async def help_command(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(
        "Daftar perintah:\n"
        "/start - Mulai bot\n"
        "/help - Bantuan\n\n"
        "Atau ketik pesan apa saja, saya akan mengulanginya 😊"
    )

# Fungsi untuk balas semua teks
async def echo(update: Update, context: ContextTypes.DEFAULT_TYPE):
    text = update.message.text
    await update.message.reply_text(f"Kamu bilang: {text}")

def main():
    # Buat aplikasi bot
    app = Application.builder().token(BOT_TOKEN).build()

    # Tambahkan handler command
    app.add_handler(CommandHandler("start", start))
    app.add_handler(CommandHandler("help", help_command))

    # Tambahkan handler pesan teks biasa
    app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, echo))

    # Jalankan bot
    print("✅ Bot sedang berjalan... Tekan CTRL+C untuk berhenti.")
    app.run_polling()

if __name__ == "__main__":
    main()

python-telegram-bot==20.3
# 🤖 Telegram Bot Example

Contoh bot Telegram sederhana menggunakan Python dan library [python-telegram-bot](https://python-telegram-bot.org/).

## 🚀 Fitur
- `/start` → menyapa pengguna
- `/help` → menampilkan bantuan
- Balas otomatis semua pesan teks

## 📦 Instalasi
1. Clone repo ini:
   ```bash
   git clone https://github.com/username/telegram-bot-example.git
   cd telegram-bot-example
pip install -r requirements.txt
