# ZEGBot

This library wraps the JSON decoding processing, making it easy to decode incoming JSON String to manipulatable objects.

This library wraps the processing of converting objects to Telegram Bot API request parameters and the processing of performing request, making it easy to handle incoming update.

**This is a server-side swift library powered by [Perfect](https://github.com/PerfectlySoft/Perfect).  
Which will help you build your own Perfect Telegram Bot!**

## Installation

Add this project as a dependency in your Package.swift file.

```swift
.Package(url: "https://github.com/ShaneQi/ZEGBot.git", versions: Version(0,0,0)..<Version(10,0,0))
```
## Quick Start

```swift
import ZEGBot

let bot = ZEGBot(token: "TYPE YOUR TOKEN HERE")

bot.run(with: {
	update, bot in

  //  Handle updates here...

})
```

## Usage

- Get text content of the incoming message:
  ```swift
  ...
  if let text = update.message?.text {
    // Do something.
  }
  ...
  ```

- Get other type of content if exists:
  ```swift
  ...
  if let voice = update.message?.voice {
    // Do something.
  }
  ...
  ```

- Send a text message to a chat:
  ```swift
  ...
  if let message = update.message {
    bot.send(message: "bar", to: message.chat)
  }
  ...
  ```

- Send a **silent** message with a **none-preview markdown link** to a chat:
  ```swift
  ...
  if let message = update?.message {
    bot.send(message: "[Google](https://google.com)", to: message.chat, parseMode: .MARKDOWN, disableWebPagePreview: true, disableNotification: true)
  }
  ...
  ```

- In all the sending methods, send to a **Message Object** means **reply** to this specific message. While Send to a **Chat Object** means send to this chat **without replying** to anyone.
  ```swift
  ...
  if let message = update?.message {
    /* This sends a message replying to another message. */
    bot.send(message: "bar", to: message)
    /* This doesn't reply to a message. */
    bot.send(message: "bar", to: message.chat)
  }
  ...
  ```

## Support Types

- Update
- Message
- Chat
- User
- MessageEntity
- Audio
- Document
- PhotoSize
- Sticker
- Video
- Voice
- Contact
- Location
- Venue

Not all the types are supported, checkout more details on [Telegram Bot API](https://core.telegram.org/bots/api#available-types).

## Support Methods

- sendMessage
- forwardMessage
- sendPhoto
- sendAudio
- sendDocument
- sendSticker
- sendVideo
- sendVoice
- sendLocation
- sendVenue
- sendContact
- sendChatAction

Not all the methods are supported, checkout more details on [Telegram Bot API](https://core.telegram.org/bots/api#available-methods).

## License
This project is licensed under [Apache License v2.0](http://www.apache.org/licenses/LICENSE-2.0).
