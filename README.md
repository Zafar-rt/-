const TelegramBot = require('node-telegram-bot-api');
const express = require('express');
const app = express();

const token = process.env.BOT_TOKEN;
const bot = new TelegramBot(token, { polling: true });

bot.on('message', (msg) => {
  const chatId = msg.chat.id;
  const text = msg.text;
  bot.sendMessage(chatId, `Привет, ${msg.from.first_name || 'друг'}! Ты написал: ${text}`);
});

app.get('/', (req, res) => {
  res.send('Бот работает!');
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Сервер запущен на порту ${PORT}`);
});
{
  "name": "smart-aibot",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "node-telegram-bot-api": "^0.61.0"
  }
}
