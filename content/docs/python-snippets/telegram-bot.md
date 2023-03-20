Simple Python script that responds to certain strings:

```python
import telebot

bot_token = "YOUR_BOT_TOKEN_HERE"
bot = telebot.TeleBot(bot_token)

@bot.message_handler(func=lambda message: True)
def handle_message(message):
    text = message.text.lower()
    chat_id = message.chat.id

    if "hello" in text:
        bot.send_message(chat_id, "Hello there!")
    elif "how are you" in text:
        bot.send_message(chat_id, "I'm doing well, thank you for asking!")
    else:
        bot.send_message(chat_id, "Sorry, I didn't understand that.")

bot.polling()
```
This script uses the telebot library to create a Telegram bot and handle incoming messages. The handle_message function is decorated with the @bot.message_handler decorator to register it as a message handler. This function checks the text of each incoming message for certain strings (in this case, "hello" and "how are you") and responds accordingly. You can modify this script to suit your specific needs.
