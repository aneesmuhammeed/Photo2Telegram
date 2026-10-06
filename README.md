# 📸 Photo2Telegram

Photo2Telegram is an open-source **Apple Shortcut for iPhone** that automatically backs up photos to a **Telegram channel**.

The Shortcut identifies photos that need to be backed up, uploads multiple photos to Telegram using a Telegram Bot, and moves successfully processed photos into a dedicated **Telegram Backup** album/folder to prevent duplicate uploads.

The project is designed to provide a simple, customizable photo-backup workflow using Apple Shortcuts and Telegram without requiring a dedicated iOS application.

---

## ✨ Features

- 📸 Automatically processes photos from your iPhone
- 📤 Uploads photos to a Telegram channel
- 🖼️ Supports multiple photos in a single run
- 🔄 Supports automation through Apple Shortcuts
- 🗂️ Organizes backed-up photos into a dedicated Telegram Backup album/folder
- 🚫 Prevents previously processed photos from being uploaded repeatedly
- 🤖 Uses the Telegram Bot API for uploads
- 📱 Runs using Apple's built-in Shortcuts application
- ⚙️ Configurable with your own Telegram Bot and Telegram channel
- 🔓 Open source and customizable
- 💻 No separate iOS application is required

---

# 🚀 How It Works

Photo2Telegram uses Apple Shortcuts to create a simple photo-backup workflow.

The basic process is:

```text
iPhone Photos
      │
      ▼
Photo2Telegram Shortcut
      │
      ▼
Find Photos to Back Up
      │
      ▼
Process Multiple Photos
      │
      ▼
Telegram Bot API
      │
      ▼
Telegram Channel
      │
      ▼
Successful Upload
      │
      ▼
Move/Add Photo to
Telegram Backup Album
```

The dedicated Telegram Backup album is used to keep track of photos that have already been processed.

This helps prevent the Shortcut from repeatedly uploading the same photos during future executions.

---

# 📂 Duplicate Prevention

One of the main features of Photo2Telegram is built-in duplicate prevention.

Instead of maintaining a separate database, the Shortcut uses a dedicated photo album/folder called:

```text
Telegram Backup
```

After a photo is successfully processed, it is added or moved to this location depending on the configured workflow.

The Shortcut can therefore distinguish between photos that still need to be processed and photos that have already been backed up.

Conceptually:

```text
New Photos
     │
     ▼
Photo already processed?
     │
 ┌───┴────┐
 │        │
YES       NO
 │        │
 ▼        ▼
Skip     Upload
          │
          ▼
       Telegram
          │
          ▼
      Successful
          │
          ▼
 Telegram Backup
      Album/Folder
```

This approach keeps the Shortcut relatively simple while avoiding repeated uploads.

> Note: Apple Photos albums do not necessarily behave like traditional filesystem folders. Depending on how the Shortcut is configured, adding a photo to an album may not remove it from the main Photos library.

---

# 🖼️ Multiple Photo Support

Photo2Telegram can process multiple photos during a single execution.

Instead of requiring the user to run the Shortcut separately for every image, the Shortcut can retrieve multiple eligible photos and process them sequentially.

Example:

```text
5 New Photos
     │
     ▼
Repeat with Each
     │
     ├── Photo 1 → Telegram
     ├── Photo 2 → Telegram
     ├── Photo 3 → Telegram
     ├── Photo 4 → Telegram
     └── Photo 5 → Telegram
```

After each successful upload, the corresponding photo can be added/moved to the Telegram Backup location.

---

# 🤖 Telegram Integration

Photo2Telegram communicates with Telegram through a Telegram Bot.

You will need:

1. A Telegram account
2. A Telegram Bot
3. A Telegram channel
4. The Bot Token
5. The Telegram Channel ID or username
6. Apple Shortcuts on your iPhone

---

# 🛠️ Setup

## 1. Create a Telegram Bot

Open Telegram and search for:

```text
@BotFather
```

Start a conversation and create a bot using:

```text
/newbot
```

Follow BotFather's instructions.

After creating your bot, Telegram will provide a Bot Token.

It will look similar to:

```text
123456789:ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

Keep this token private.

---

## 2. Create a Telegram Channel

Create a new Telegram channel that will be used for your photo backups.

For example:

```text
My Photo Backup
```

The channel can be configured according to your privacy requirements.

For personal photo backups, using a private channel is recommended.

---

## 3. Add the Bot to the Channel

Open your Telegram channel settings.

Navigate to:

```text
Administrators
```

Add your Telegram Bot as an administrator.

Give the bot the permissions required to post messages/media to the channel.

---

## 4. Obtain Your Channel Identifier

Photo2Telegram needs to know which Telegram channel should receive the photos.

Depending on your configuration, this may be a channel username or numeric channel identifier.

Example:

```text
@my_photo_backup
```

or a numeric identifier supported by the Telegram Bot API.

---

## 5. Create the Backup Album

Open the Apple Photos app on your iPhone and create a new album named exactly:

```text
Telegram Backup
```

The Shortcut uses this specific album to verify whether a photo has already been uploaded or not.

---

## 6. Install the Shortcut

**Option 1: iCloud Link (Recommended)**  
[Install Photo2Telegram Shortcut](https://www.icloud.com/shortcuts/161a2301deda427aa7a99755945ff103)  

**Option 2: Manual Installation**  
Download the Photo2Telegram Shortcut from this repository.

The Shortcut file can be found inside:

```text
shortcut/
```

Example:

```text
shortcut/Photo2Telegram.shortcut
```

Open the file on an iPhone and import it into the Apple Shortcuts application.

Review all Shortcut actions before running it.

---

## 7. Configure the Shortcut

The Shortcut requires your Telegram configuration.

Replace the placeholder values with your own credentials.

Example:

```text
BOT_TOKEN = YOUR_TELEGRAM_BOT_TOKEN
CHANNEL_ID = YOUR_TELEGRAM_CHANNEL_ID
```

Never commit your real Bot Token to GitHub.

---

# 🔐 Security Warning

Your Telegram Bot Token is effectively a credential.

Anyone who obtains the token may be able to interact with your bot according to its permissions.

**Never publish your Bot Token.**

Do not place your personal token inside:

```text
README.md
screenshots/
documentation/
GitHub Issues
GitHub Discussions
commits
```

Before publishing screenshots of the Shortcut, verify that the Bot Token, channel identifiers, personal photos, names, or other sensitive information are not visible.

If a Bot Token is accidentally published, revoke/regenerate it using BotFather as soon as possible.

---

# 🔏 Privacy

Photo2Telegram handles personal photos, so users should understand where their data is being sent.

The Shortcut sends selected photos to the Telegram Bot API and ultimately to the Telegram channel configured by the user.

Users are responsible for:

- Securing their Telegram account
- Securing their Telegram Bot Token
- Configuring appropriate channel privacy
- Reviewing the Shortcut before installation
- Understanding Telegram's privacy and data-storage policies

This project does not provide its own cloud-storage infrastructure.

---

# 📁 Repository Structure

```text
Photo2Telegram/
│
├── README.md
├── LICENSE
├── CONTRIBUTING.md
│
├── shortcut/
│   └── Photo2Telegram.shortcut
│
├── screenshots/
│   ├── workflow.png
│   ├── setup.png
│   └── telegram-result.png
│
└── docs/
    └── setup.md
```

---

# 📱 Requirements

You will need:

- An iPhone or compatible Apple device
- Apple Shortcuts
- Telegram
- A Telegram Bot
- A Telegram channel
- Internet connectivity

The exact iOS version tested should be documented with each release.

---

# ⚠️ Important

Always test the Shortcut with non-important photos before enabling a fully automated workflow.

Photo2Telegram interacts with your photo library and an external service. Users should understand every action in the Shortcut before granting permissions or enabling automation.

It is recommended to keep an independent backup of important photos.

---

# 🧪 Testing

Before submitting changes or using the Shortcut with your main photo library, test:

- Single photo upload
- Multiple photo upload
- Telegram Bot authentication
- Channel posting
- Duplicate prevention
- Telegram Backup album handling
- Failed upload behavior
- Network interruption behavior
- Shortcut permissions

Contributors should mention their tested iOS version when submitting changes.

---

# 🤝 Contributing

Contributions are welcome.

You can contribute by:

- Fixing bugs
- Improving duplicate detection
- Improving error handling
- Adding new automation options
- Improving documentation
- Testing different iOS versions
- Improving Telegram integration
- Improving performance with large photo collections
- Adding optional configuration features
- Reporting reproducible issues

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a Pull Request.

---

# 🐛 Reporting Issues

If you discover a problem, create a GitHub Issue.

Please include:

```text
iPhone Model:
iOS Version:
Shortcut Version:

Expected Behavior:

Actual Behavior:

Steps to Reproduce:

Additional Information:
```

**Never include your Telegram Bot Token in an issue.**

---

# 🗺️ Possible Future Improvements

Potential future features include:

- Video backup
- Configurable photo batch size
- Retry handling for failed uploads
- Better upload progress information
- Upload statistics
- Date-based filtering
- Screenshot-only backup
- Configurable Telegram destinations
- Optional captions
- Improved error notifications
- More advanced duplicate detection

Feature suggestions are welcome through GitHub Issues.

---

# 📜 License

Photo2Telegram is released under the MIT License.

See [LICENSE](LICENSE) for details.

---

# ⭐ Support

If you find Photo2Telegram useful, consider starring the repository.

Stars help other users discover the project.

You can also support the project by:

- Reporting bugs
- Suggesting features
- Improving documentation
- Testing the Shortcut
- Submitting Pull Requests

---

## Disclaimer

Photo2Telegram is an independent open-source project and is not affiliated with, endorsed by, or sponsored by Apple Inc. or Telegram.

Apple, iPhone, iOS, and Shortcuts are trademarks of Apple Inc.

Telegram is a trademark of its respective owner.

