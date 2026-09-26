import telebot, os
from telebot import types

TOKEN = os.environ.get("BOT_TOKEN")
MONETAG_LINK = os.environ.get("MONETAG_LINK")

bot = telebot.TeleBot(TOKEN)

TEXTS = {
 'ar': {'welcome': "🌍 مرحبا في Earn Loop!\nلغة جهازك عربية\n\n💰 رصيدك: 0.00$\n🔄 مهامك: 0/10", 'balance': "💰 رصيدك", 'tasks': "📺 شاهد واربح", 'referral': "👥 الإحالة", 'withdraw': "💸 سحب"},
 'en': {'welcome': "🌍 Welcome to Earn Loop!\n\n💰 Balance: $0.00\n🔄 Tasks: 0/10", 'balance': "💰 Balance", 'tasks': "📺 Watch & Earn", 'referral': "👥 Referral", 'withdraw': "💸 Withdraw"},
 'fr': {'welcome': "🌍 Bienvenue!", 'balance': "💰 Solde", 'tasks': "📺 Gagner", 'referral': "👥 Parrainage", 'withdraw': "💸 Retirer"}
}

def get_lang(m):
 c=m.from_user.language_code
 if c and 'ar' in c: return 'ar'
 if c and 'fr' in c: return 'fr'
 return 'en'

@bot.message_handler(commands=['start'])
def start(m):
 lang=get_lang(m)
 t=TEXTS[lang]
 markup=types.InlineKeyboardMarkup()
 markup.add(types.InlineKeyboardButton(t['tasks'], url=MONETAG_LINK))
 markup.add(types.InlineKeyboardButton(t['balance'], callback_data='bal'), types.InlineKeyboardButton(t['referral'], callback_data='ref'))
 bot.send_message(m.chat.id, t['welcome'], reply_markup=markup)

bot.infinity_polling()
