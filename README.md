# Museums_Sunday_Bot (Berlin)

A Telegram bot that helps you avail [Museumssonntag](https://www.museumssonntag.berlin/de) in Berlin. Appreciate the arts and culture of Berlin more by visiting museums for FREE every month!

This bot does 2 things:

1. It messages you the moment when the next Museums Sunday tickets becomes available for booking
2. It gives you an updated list of museums that still have free tickets available for booking

From [Museums Sunday Berlin](https://www.museumssonntag.berlin/) website:

> Sundays at the museum! Admission is free on the first Sunday of every month – everyone is welcome and warmly invited. There is a lot to discover at our museums, with exhibitions and events on topics such as art, design, religion, history, nature, everyday culture, the history of the city, and technology. On Berlin’s Museum Sunday there is something for everyone. We look forward to your visit.

available - updated list of museums that still have free tickets available for booking

---

This project is not possible without:

# cf-workers-telegram-bot

serverless telegram bot on cf workers

The original `worker.js` is the content of Nikhil John's
https://github.com/nikhiljohn10/telegram-bot-worker which is licensed with MIT.
My modifications are licensed under the Apache license.

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/codebam/cf-workers-telegram-bot)

To use the deploy button:

- Click the deploy button
- Navigate to your new **GitHub repository &gt; Settings &gt; Secrets** and add the following secrets:

  ```yaml
  - Name: CF_API_TOKEN (should be added automatically)
  - Name: CF_ACCOUNT_ID (should be added automatically)

  - Name: SECRET_TELEGRAM_API_TOKEN
  - Value: your-telegram-bot-token
  ```

- Push to `master` to trigger a deploy

To fork this repo and use wrangler:

- Click fork
- `wrangler secret put SECRET_TELEGRAM_API_TOKEN` and set it to your telegram
  bot token
- `wrangler publish`
- Done!

## Getting started with cf-workers-telegram-bot

Once you've deployed the bot you can get your Webhook command URL by doing any
of the following.

- sha256sum(YourTelegramSecretKey) is the path to your webhook commands and
  should be put at the end of your worker URL to access commands such as
  setting your webhook
- Use `sha256sum <<< "your secret key"` to get the path
- Open the Cloudflare Worker Logs under **Workers &gt; cf-workers-telegram-bot
  &gt; Logs &gt; Begin log stream** and make a GET request (open it in your browser)
  to your Worker URL and look at the logs to see your Access URL
- Run `wrangler tail --format pretty` from inside your git repository and make
  a GET request to your Worker URL

Example URL for setting the Webhook and dropping pending updates:

`https://cf-workers-telegram-bot.codebam.workers.dev/a948904f2f0f479b8f8197694b30184b0d2ed1c1cd2a1ec0fb85d299a192a447?command=set`
