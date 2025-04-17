# VeloScripts - FIFA Bot - User Guide

Welcome to VeloScripts, a powerful automation tool for FIFA account management. This guide will help you understand how to use the bot effectively, with a special focus on the data files required for operation.

## System Requirements

- **Operating System**: Windows, macOS, or Linux
- **Google Chrome**: Must be installed (latest version recommended)
- **Internet Connection**: Stable connection required
- **Valid License Key**: Required for activation

## Quick Start Guide

1. Download the appropriate executable for your system:
   - Windows: `fifabot-win-x64.exe`
   - Mac (Apple Silicon): `fifabot-mac-arm64`
   - Mac (Intel): `fifabot-mac-x64`
   - Linux: `fifabot-linux-x64`

2. Run the executable and enter your license key when prompted
3. The bot will create necessary data files in the `dist/data` directory
4. Use the menu options to manage your FIFA accounts

## Data Files

The bot creates and uses several data files in the `dist/data` directory. Understanding these files is crucial for the effective use of the bot.

### 1. pendingEmails.csv

This file stores emails that are waiting to be registered with FIFA.

**Format:**
```
email,imapEmail,imapPassword
example@gmail.com,imap_example@gmail.com,imapPassword123
```

**Fields:**
- `email`: The email address to register with FIFA
- `imapEmail`: The IMAP-enabled email for verification (can be the same as the registration email)
- `imapPassword`: Password for the IMAP email account

**Notes:**
- The header row is required
- Each email should be on a new line
- All three fields are required for each entry
- You can manually edit this file or use the "Load Emails" option in the bot

### 2. registeredEmails.csv

This file stores successfully registered FIFA accounts.

**Format:**
```
email,imapEmail,imapPassword
registered@gmail.com,imap_registered@gmail.com,imapPassword123
```

**Fields:**
- `email`: The email registered with FIFA
- `imapEmail`: The IMAP email used for verification
- `imapPassword`: Password for the IMAP email account

**Notes:**
- The bot automatically adds entries to this file after successful registration
- Do not modify this file manually unless you know what you're doing
- This file is used for the "Mass Sign In" feature

### 3. proxyList.csv

This file stores proxy configurations for IP rotation.

**Format:**
```
ip,port,username,password,protocol
192.168.1.1,8080,proxyuser,proxypass,http
```

**Fields:**
- `ip`: Proxy server IP address
- `port`: Proxy server port
- `username`: Username for proxy authentication (if required)
- `password`: Password for proxy authentication (if required)
- `protocol`: Proxy protocol (usually http or https)

**Notes:**
- The header row is required
- Each proxy should be on a new line
- You can leave username and password empty if your proxy doesn't require authentication
- The bot will randomly select proxies from this list during operations

### 4. license.json

This file stores your license information.

**Format:**
```json
{
  "key": "YOUR-LICENSE-KEY",
  "hwid": "YOUR-HARDWARE-ID",
  "activatedAt": "2025-04-10T01:00:00.000Z"
}
```

**Notes:**
- This file is automatically created when you activate your license
- Do not modify this file manually
- If you need to use your license on a different device, you must reset it in your Whop dashboard

## Using the Data Files

### Adding Emails for Registration

1. **Option 1: Use the Bot Interface**
   - Select option 3 (Load Emails) from the main menu
   - Provide the path to your CSV file with the correct format

2. **Option 2: Edit the File Directly**
   - Open `dist/data/pendingEmails.csv` in any text editor
   - Add your emails following the format above
   - Save the file and restart the bot if it's already running

### Using Proxies

1. **Option 1: Use the Bot Interface**
   - Select option 6 (Load Proxies) from the main menu
   - Provide the path to your proxy list file

2. **Option 2: Edit the File Directly**
   - Open `dist/data/proxyList.csv` in any text editor
   - Add your proxies following the format above
   - Save the file and restart the bot if it's already running

## CSV File Templates

You can create your own CSV files for importing emails and proxies. Here are templates you can use:

### pendingEmails.csv Template
```
email,imapEmail,imapPassword
user1@example.com,imap_user1@example.com,password1
user2@example.com,imap_user2@example.com,password2
```

### proxyList.csv Template
```
ip,port,username,password,protocol
192.168.1.1,8080,user1,pass1,http
192.168.1.2,8080,user2,pass2,http
192.168.1.3,8080,,,http
```

## Common Issues and Solutions

### Issue: Bot can't find data files
**Solution**: Make sure the `dist/data` directory exists in the same location as the executable. If not, create it manually.

### Issue: Emails not being processed
**Solution**: Check that your `pendingEmails.csv` file has the correct format with the header row and all required fields.

### Issue: Proxy connection failures
**Solution**: Verify that your proxies are active and correctly formatted in the `proxyList.csv` file.

### Issue: License validation fails
**Solution**: Ensure your license key is active and not being used on another device. You may need to reset your license in your Whop dashboard.

## Best Practices

1. **Regular Backups**: Keep backups of your data files, especially `registeredEmails.csv`
2. **Use High-Quality Proxies**: For better success rates, use reliable proxy services
3. **Verify Email Access**: Ensure you have IMAP access to all emails used for registration
4. **Update Regularly**: Always use the latest version of the bot for best results

## Support

If you encounter any issues not covered in this guide, please contact support through your Whop dashboard or the official support channels.

---

Thank you for using VeloScripts! We hope this guide helps you get the most out of our software.
