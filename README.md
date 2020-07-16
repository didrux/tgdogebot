#! /usr/bin/env python
# -*- coding: utf-8 -*-
import telebot

bot = telebot.TeleBot('977887581:AAFA8AFTIHzgLMF4exHNe40qNnG5aJxS4EQ')

from telebot import types

@bot.message_handler(content_types=['text', 'document', 'audio'])

def get_text_messages(message):

    if message.text == "/doge":

        bot.send_message(message.from_user.id, "which type of dogs you want?")

        keyboard = types.InlineKeyboardMarkup()

        key_husky = types.InlineKeyboardButton(text='Husky', callback_data='doggy1')
        keyboard.add(key_husky)

        key_bulldog = types.InlineKeyboardButton(text='Bulldog', callback_data='doggy2')
        keyboard.add(key_bulldog)

        key_puppy = types.InlineKeyboardButton(text='Puppy', callback_data='doggy3')
        keyboard.add(key_puppy)

        key_pug = types.InlineKeyboardButton(text='Pug', callback_data='doggy4')
        keyboard.add(key_pug)

        bot.send_message(message.from_user.id, text='choose the doge type', reply_markup=keyboard)

    else:

        bot.send_message(message.from_user.id, "You can look at dogs here. Use command /doge")

@bot.callback_query_handler(func=lambda call: True)

def callback_worker(call):

    if call.data == "doggy1":

        mv1 = 'https://pbs.twimg.com/profile_images/615993481685794816/vMhSLk-2.jpg'

        bot.send_message(call.message.chat.id, mv1)

    elif call.data == "doggy2":

        mv2 = 'https://i.pinimg.com/originals/b8/17/42/b81742b0593c420dcd3b3750728515de.jpg'

        bot.send_message(call.message.chat.id, mv2)

    elif call.data == "doggy3":

        mv3 = 'https://static-s.aa-cdn.net/img/amazon/30600000149397/48c13d7ff0705dd937a4c470a10562b1?v=1'

        bot.send_message(call.message.chat.id, mv3)

    elif call.data == "doggy4":

        mv4 = 'https://pbs.twimg.com/profile_images/670898593717334016/CDtB_3Xq_400x400.jpg'

        bot.send_message(call.message.chat.id, mv4)











if __name__ == '__main__':
	bot.polling(none_stop=True)

