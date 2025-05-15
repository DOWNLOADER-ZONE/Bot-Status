## 📦 ***Repo Config SetUp***:

### _`.env` File SetUp :_
- `API_ID`: Authenticate your Telegram account, get this from https://my.telegram.org.
- `API_HASH`: Authenticate your Telegram account, get this from https://my.telegram.org.
- `PYRO_SESSION`: Pyrogram User Session to Access Bots, Generate from [Here](https://colab.research.google.com/drive/1wjYvtwUo5zDsUvukyafAR9Of-2NYkKsu)
- `HEADER_MSG` : Put Header Msg for 1st Line. 
  > Default: Telegram Bot Status :
- `TIME_ZONE`: Time Zone for Sync with your Local Time
  > Default: Asia/Kolkata
- `BOT_TOKEN`: (Optional) Only Required if `MSG_BUTTONS` is added for Post Buttons.
- `MSG_BUTTONS`: Make Awesome Telegram Buttons to show at the bottom of the Text.
  > Unlimited Buttons with Any Design ! 
  - ***How to Use ?***
    - **Separator :** # for Text and Link, | for Button Separator, || for Next Line Separator
    - _Sample Use Cases:_
      ```
      Input:
      b_text1#b_url|b_text2#b_url||b_text3#b_url|b_text4#b_url
      
      Output: (Buttons)
      [ b_text1 ][ b_text2 ]
      [ b_text3 ][ b_text4 ]
      
      Input:
      b_text1#b_url||b_text2#b_url|b_text3#b_url|b_text4#b_url
      
      Output: (Buttons)
      [            b_text1            ]
      [ b_text2 ][ b_text3 ][ b_text4 ]
      
      Input:
      b_text1#b_url||b_text2#b_url||b_text3#b_url
      [ b_text1 ]
      [ b_text2 ]
      [ b_text3 ]
      ```

---

### _`config.json` File SetUp :_
- _Sections are Divided into 2 Parts_:
  1. Bots Details:
    `bot1`: Indentifier Name (Can be Anything But Unique for Every Bot)

    |Variable|Value|Required|
    |:---:|:---:|:---:|
    |`base_url_of_bot`|If MLTB bot, give Base URL of it.|(Optional)|
    |`host`|Host name where you have deployed|*Required|
    |`bot_uname`|Bot Username without @|*Required|
    
  2. Chat Details:
    `chat1`: Indentifier Name (Can be Anything But Unique for Every Bot)

    |Variable|Value|Required|
    |:---:|:---:|:---:|
    |`chat_id`|chat id of the Target Channel or Group|*Required|
    |`message_id`|message id of the Message to Edit. If link is https://t.me/cha_uname/123 Here, 123 is the Message ID|*Required|

#### 🪧 ***Sample JSON Format***
```json
{
  "bots": {
    "bot1": {
      "base_url_of_bot": "http://0.0.0.0",
      "host": "HK",
      "bot_uname": "@botfather"
    },
    "bot2": {
      "host": "Vps",
      "bot_uname": "@botfather"
    }
    ...more
  },
  "channels": {
    "chat1": {
      "chat_id": "-100xxxxxx",
      "message_id": "54321"
    },
    "chat2": {
      "chat_id": "-100xxxxxxx",
      "message_id": "12345"
    }
    ...more
  }
}
```

### _Required Config Setup :_
Either Add these URL to these Variables or Directly Add a File on Repo as File name Specified.

- `CONFIG_ENV_URL`: _(Optional if .env provided)_ Direct URL of `.env` file posted on [gist.github.com](https://gist.github.com)
- `CONFIG_JSON_URL`:  _(Optional if config.json provided)_ Direct URL of `config.json` file posted on [gist.github.com](https://gist.github.com)

> [!NOTE]
> `CONFIG_JSON_URL` & `CONFIG_ENV_URL` will overwrite the existing local files if provided.

---

## 🗄 ***Deploy Guide***
- Only Deployable on Workflows
- Soon Add for Heroku & VPS Users

### _Prerequisites:_
- Setup `config.json` and `.env`
- Send a Dummy Message on the Channel (say 'test') you want to Setup Status and Retrieve the message id of it.

### _Procedure:_
- **Step 1:** _Fork & Star the Repo_
- **Step 2:** _Set Variables in Secrets in Settings Tab_
  > Available Variables: API_ID, API_HASH, PYRO_SESSION, CONFIG_ENV_URL, CONFIG_JSON_URL
- **Step 3:** _Enable `Actions` -> `Select Workflow` -> `Run Workflow`_

---

## ♻️ ***Cron Job Workflow***:
- Format for Tg Message Edit/Update Interval
  - `*/5 * * * *`: Update Every 5mins Interval
    > Due to Github Runner, Working Time Varies from 5min to more..
  - `0 */2 * * *`: Update Every 2hrs Interval
