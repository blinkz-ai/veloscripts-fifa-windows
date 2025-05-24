# Veloscripts - User Guide

Welcome to Veloscripts, a powerful automation tool for FIFA account management. This guide will help you understand how to use the bot effectively, with special focus on the data files required for operation.

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

## Running the Windows Executable

1. **Download**: After downloading `fifabot-win-x64.exe`, place it in a dedicated folder (e.g., create a folder named "Veloscripts")

2. **First Run**:
   - Right-click on `fifabot-win-x64.exe` and select "Run as administrator"
   - If Windows SmartScreen appears, click "More info" and then "Run anyway"
   - The first time you run the executable, it will create a `dist/data` folder in the same directory

3. **License Activation**:
   - Enter your license key when prompted
   - The bot will validate your license and save it for future use

4. **Navigation**:
   - Use the number keys (1-9) to navigate the menu options
   - Follow on-screen instructions for each operation

5. **Closing the Bot**:
   - Always use the exit option in the menu to properly close the bot
   - Avoid forcibly closing the application to prevent data corruption

6. **Creating a Shortcut** (Optional):
   - Right-click on `fifabot-win-x64.exe`
   - Select "Create shortcut"
   - Move the shortcut to your desktop for easy access

## Data Files

The bot creates and uses several data files in the `dist/data` directory. Understanding these files is crucial for effective use of the bot.

### 1. pendingEmails.csv

This file stores emails waiting to be registered with FIFA.

**Format:**

```bash
email,imapEmail,imapPassword
example@gmail.com,imap_example@gmail.com,imapPassword123
```

**Fields:**

- `email`: The email address to register with FIFA
- `imapEmail`: The IMAP-enabled email for verification (can be the same as registration email)
- `imapPassword`: Password for the IMAP email account

**Notes:**

- The header row is required
- Each email should be on a new line
- All three fields are required for each entry
- You can manually edit this file or use the "Load Emails" option in the bot

### 2. registeredEmails.csv

This file stores successfully registered FIFA accounts.

**Format:**

```bash
email,imapEmail,imapPassword,fifaPassword,registeredAt
registered@gmail.com,imap_registered@gmail.com,imapPassword123,Fifa!Pass1,2025-05-23T04:33:59.265Z
```

**Fields:**

- `email`: The email registered with FIFA
- `imapEmail`: The IMAP email used for verification
- `imapPassword`: Password for the IMAP email account
- `fifaPassword`: The password used for the FIFA account (compliant with FIFA requirements)
- `registeredAt`: Timestamp when the account was registered

**Notes:**

- The bot automatically adds entries to this file after successful registration
- Do not modify this file manually unless you know what you're doing
- This file is used for the "Mass Sign In" feature

### 3. proxyList.csv

This file stores proxy configurations for IP rotation.

**Format:**

```bash
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

```bash
email,imapEmail,imapPassword
user1@example.com,imap_user1@example.com,password1
user2@example.com,imap_user2@example.com,password2
```

**Note**: You can optionally add a custom FIFA password in the pendingEmails.csv file by adding a fourth column:

```bash
email,imapEmail,imapPassword,fifaPassword
user1@example.com,imap_user1@example.com,password1,Custom!Pass123
```

### proxyList.csv Template

```bash
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

### Issue: Password not meeting FIFA requirements

**Solution**: If you're using a custom password, ensure it meets all FIFA requirements (uppercase, lowercase, number, special character, 8+ characters). If the password doesn't meet requirements, the bot will automatically generate a compliant password instead.

## Password Requirements

FIFA has updated their password requirements. All passwords must now include:

- At least 8 characters
- At least 1 uppercase letter
- At least 1 lowercase letter
- At least 1 number
- At least 1 special character (!@#$%^&*()-_=+[]{}|;:,.<>?)

The bot now has two options for handling passwords:

1. **Auto-generate compliant passwords**: The bot will automatically generate random passwords that meet FIFA's requirements
2. **Use custom password**: You can specify a custom password that will be used for all accounts (must meet FIFA requirements)

When signing in, the bot will automatically use the FIFA password stored in the registeredEmails.csv file.

## Headless Mode

Veloscripts now offers the option to run in headless or visible mode:

### What is Headless Mode?

Headless mode runs the browser in the background without displaying a visible window. This means:

- The browser operates invisibly (you won't see it on your screen)
- Lower resource usage and faster operation
- Ability to continue working on other tasks while the bot runs
- Ideal for server environments or when running the bot for extended periods

### What is Visible Mode?

Visible mode shows the browser window and all actions in real-time. This means:

- You can watch exactly what the bot is doing
- Useful for troubleshooting or understanding the registration/sign-in process
- Helpful for debugging if you encounter issues
- Recommended for first-time users to understand the workflow

### How to Choose

When starting Mass Registration or Mass Sign In, the bot will ask:

```bash
Run in headless mode? (y/n, default: y):
```

Type `y` (or just press Enter) for headless mode, or `n` for visible mode.

## Upgrading to New Versions

⚠️ **IMPORTANT: Handling Data When Upgrading**

When upgrading to a new version of the Veloscripts, follow these steps to ensure a smooth transition:

1. **Backup Your Data**: Before upgrading, copy your important data files to a safe location:
   - `dist/data/registeredEmails.csv` - Contains all your registered accounts
   - `dist/data/pendingEmails.csv` - Contains emails waiting to be registered
   - `dist/data/proxyList.csv` - Contains your proxy configurations
   - `dist/data/license.json` - Contains your license information

2. **Delete Old Files**: Remove the old executable file and the entire `dist/data` directory

3. **Install New Version**: Download and place the new executable in a clean location

4. **First Run**: Run the new version once to let it create a fresh `dist/data` directory structure

5. **Restore Your Data**: Copy your backed-up CSV files to the newly created `dist/data` directory

**Why This Is Important**: New versions may have different data structures or requirements. Using old data files without proper migration can cause unexpected behavior or errors. Always follow this process when upgrading to ensure compatibility.

## Best Practices

1. **Regular Backups**: Keep backups of your data files, especially `registeredEmails.csv`
2. **Use High-Quality Proxies**: For better success rates, use reliable proxy services
3. **Verify Email Access**: Ensure you have IMAP access to all emails used for registration
4. **Update Regularly**: Always use the latest version of the bot for best results

## Support

If you encounter any issues not covered in this guide, please contact support through your Whop dashboard or the official support channels.

---

Thank you for using Veloscripts! We hope this guide helps you get the most out of our software.
