# whatsapp-chatgpt-relay

A Jupyter notebook that reads unread WhatsApp Web messages, asks ChatGPT in the browser, and sends the answer back on WhatsApp.

## Status

Prototype from 2023. It drives the ChatGPT and WhatsApp Web pages through hard-coded CSS selectors and XPaths. Both sites have changed since, so expect the selectors to fail and need updating. It does not use any official API.

## Features

- Opens ChatGPT (incognito window) and WhatsApp Web in two separate Chrome sessions using `undetected_chromedriver`.
- Waits for a chat with an unread message, opens it and reads the last message.
- Types the message into ChatGPT, waits until the response has finished streaming, and reads the reply.
- Pastes the reply into the WhatsApp chat and sends it.
- Handles 5 messages per run (fixed loop).

## Tech stack

Python 3, Jupyter, Selenium, undetected-chromedriver, Google Chrome.

## Structure

```
chatgpt_WhatsApp.ipynb   the whole program
LICENSE
```

## Setup

Requirements: Python 3.8+, Google Chrome, a ChatGPT account and a WhatsApp account.

```bash
pip install selenium undetected-chromedriver notebook
jupyter notebook chatgpt_WhatsApp.ipynb
```

No environment variables are used. You log in by hand.

## Usage

1. Run the cells in order. Two Chrome windows open.
2. Within the 30 second pause, log in to ChatGPT and scan the WhatsApp Web QR code.
3. Send a message to the account from another phone. The notebook picks up the unread chat, asks ChatGPT and replies.

## Limitations

- Selectors are hard-coded and likely outdated.
- The `send_Answer` step clicks the third pinned chat, which only suits one specific account layout.
- Blocks for a very long time waiting for an unread message.
- Browser automation of these services may not be allowed by their terms.

## License

MIT
