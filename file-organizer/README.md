# 📁 n8n File Organizer Workflow

An automated file organization workflow for n8n that organizes your files based on their extensions into a well-structured directory hierarchy.

## 🚀 Quick Start (5 Minutes)

### Step 1: Import Workflow

1. Open n8n interface
2. Click **"+" → Import from File**
3. Select `workflow.json`
4. Click **"Import"**

### Step 2: Configure Home Directory

Edit the **Configuration** node and change:

```javascript
home: process.env.HOME || '/home/username'  // Change 'username' to YOUR username
```

### Step 3: Test in Dry-Run Mode

1. In **Configuration** node, ensure `dry_run: true`
2. Click **"Execute Workflow"**
3. Check logs to verify file mappings look correct

### Step 4: Go Live

1. In **Configuration** node, set `dry_run: false`
2. Click **"Execute Workflow"**
3. Check email for results (if configured)

**Optional:** Configure email notifications in the **Send Email** node, or delete it if not needed.

---

## 🌟 Features

- **🎯 Extension-Based Organization**: Automatically categorizes 133+ file types
- **📊 Comprehensive Logging**: JSON logs of all file movements
- **📧 Email Notifications**: Get notified after each organization run
- **🔄 Idempotent**: Safe to run multiple times - skips already organized files
- **⚡ Fast**: Pure extension-based logic, no AI overhead
- **🛡️ Fault-Tolerant**: Handles edge cases gracefully
- **🗓️ Scheduled**: Optional daily automatic organization

## 📋 Requirements

### System Requirements

- **Operating System**: Linux (Ubuntu, Debian, Fedora, etc.)
- **Shell**: Bash (default on most Linux systems)
- **Tools**: `find`, `mv`, `mkdir` (standard Unix utilities)

### n8n Requirements

- **n8n Version**: 1.0.0 or higher
- **Node.js**: 18.x or higher
- **Required Nodes**:
  - Code (n8n-nodes-base.code)
  - Execute Command (n8n-nodes-base.executeCommand)
  - Filter (n8n-nodes-base.filter)
  - If (n8n-nodes-base.if)
  - Email Send (n8n-nodes-base.emailSend) - optional
  - Schedule Trigger (n8n-nodes-base.scheduleTrigger) - optional
  - Manual Trigger (n8n-nodes-base.manualTrigger)

### SMTP Configuration (Optional)

If you want email notifications, configure SMTP credentials in n8n:

- Gmail, Outlook, or any SMTP server
- Configure in n8n: Settings → Credentials → SMTP

## 🚀 Installation

### 1. Import Workflow

1. Open n8n interface
2. Click **"+" → Import from File**
3. Select `workflow.json`
4. Click **"Import"**

### 2. Configure Home Directory

Edit the **Configuration** node:

```javascript
home: process.env.HOME || '/home/username'  // Change 'username' to your actual username
```

Or use an environment variable:

```bash
export HOME=/home/yourusername
```

### 3. Configure Email (Optional)

Edit the **Send Email** node:

- Set `toEmail` to your email address
- Configure SMTP credentials (Settings → Credentials → SMTP)

Or disable email:

- Delete the connection from "Write Log" → "Send Email"

### 4. Test Run (Dry Run Mode)

**IMPORTANT**: Before the first live run:

1. Edit **Configuration** node
2. Set `dry_run: true`
3. Click **"Execute Workflow"**
4. Check the logs to verify file mappings
5. Once satisfied, set `dry_run: false`

## 📂 Directory Structure

The workflow organizes files into this structure:

```
$HOME/
├── Documents/
│   ├── Office/          # docx, xlsx, pptx, odt, ods, odp
│   ├── PDF/             # pdf
│   ├── Text/            # txt, md, markdown, rtf
│   ├── Data/            # csv, tsv, xml
│   ├── Audio/           # mp3, wav, flac, aac, ogg, m4a, wma, opus
│   ├── Archives/        # zip, rar, 7z, tar, gz, bz2, xz, tgz, tbz2
│   └── Code/
│       ├── Web/         # html, css, js, jsx, ts, tsx, svelte, vue, scss
│       ├── Python/      # py, pyc, pyi, pth, ipynb
│       ├── Systems/     # c, cpp, h, hpp, go, rs, rust
│       ├── Java/        # java, kt, scala
│       ├── Swift/       # swift
│       ├── R/           # r
│       ├── SQL/         # sql
│       ├── Scripts/     # sh, bash, zsh, fish, ps1, bat, cmd
│       ├── Config/      # json, yml, yaml, toml, ini, conf, cfg, env
│       └── Other/       # proto, glsl, map
├── Pictures/
│   ├── Images/          # png, jpg, jpeg, gif, webp, svg, bmp, tiff, heic, ico, raw
│   ├── Screenshots/     # *screenshot*.{png,jpg,jpeg}
│   └── Design/          # fig, sketch, xd, psd, ai
├── Videos/
│   └── Movies/          # mp4, avi, mkv, mov, wmv, flv, webm, m4v, mpg, mpeg
└── Downloads/
    ├── Installers/      # deb, rpm, appimage, exe, msi, dmg, pkg
    ├── Binaries/        # dll, so, lib, wasm, dylib, pyd
    └── Other/           # Unknown file types
```

## 🎯 Supported File Types

### Documents (90 types)

- **Office**: docx, doc, pptx, ppt, xlsx, xls, odt, ods, odp
- **PDFs**: pdf
- **Text**: txt, md, markdown, rtf
- **Data**: csv, tsv, xml
- **Audio**: mp3, wav, flac, aac, ogg, m4a, wma, opus
- **Archives**: zip, rar, 7z, tar, gz, bz2, xz, tgz, tbz2
- **Code**: 70+ programming language extensions

### Pictures (20 types)

- **Images**: png, jpg, jpeg, gif, webp, svg, bmp, tiff, tif, heic, heif, ico, raw, cr2, nef
- **Design**: fig, sketch, xd, psd, ai
- **Screenshots**: Auto-detected by filename

### Videos (10 types)

mp4, avi, mkv, mov, wmv, flv, webm, m4v, mpg, mpeg

### Downloads (13 types)

- **Installers**: deb, rpm, appimage, exe, msi, dmg, pkg
  
- **Binaries**: dll, so, lib, wasm, dylib, pyd

**Total: 133 file types supported**

## 🔧 Usage

### Manual Execution

1. Open the workflow in n8n
2. Click **"Execute Workflow"** button
3. Wait for completion
4. Check email notification (if configured)

### Scheduled Execution

Enable the **Daily Schedule** trigger:

1. Click on "Daily Schedule" node
2. Click **"Activate"** button
3. Set your preferred time (default: 7:00 PM)
4. Save workflow

The workflow will now run automatically every day.

### Scanned Directories

The workflow scans these directories by default:

- `$HOME/Downloads` (root level + 1 level deep)
- `$HOME/Documents` (root level + 1 level deep)
- `$HOME/Pictures` (root level + 1 level deep)
- `$HOME/Desktop` (root level only)
- `$HOME/Videos` (1 level deep only)

**Note**: Hidden files (starting with `.`) are excluded.

## 📊 Logging

Execution logs are saved to:
```
$HOME/Desktop/file_change_logs/YYYY-MM-DDTHH-MM-SS.json
```

Log format:

```json
{
  "execution_id": "2025-11-03T00:58:02.582+05:30",
  "timestamp": "2025-11-02T19:28:02.586Z",
  "dry_run": false,
  "summary": {
    "files_analyzed": 127,
    "files_moved": 80,
    "approved": 80,
    "rejected": 0
  },
  "approved_actions": [...],
  "rejected_actions": []
}
```

## 🛡️ Edge Case Handling

The workflow handles these scenarios:

✅ **File already in correct location** - Skipped  
✅ **File already in target directory** - Skipped  
✅ **File doesn't exist** - Skipped with message  
✅ **Source and destination are same** - Skipped  
✅ **Permission errors** - Logged, workflow continues  
✅ **Duplicate filenames** - Error logged, file not moved  

## 🔒 Security & Privacy

- No external API calls
- No data sent outside your system
- Runs entirely on your local n8n instance
- Email credentials stored securely in n8n

## ⚙️ Customization

### Change Scanned Directories

Edit **Find Root Files** and **Find Nested Files** nodes:

```bash
# Find Root Files
find $HOME/Downloads $HOME/Documents $HOME/CustomFolder -maxdepth 1 -type f

# Find Nested Files
find $HOME/Downloads $HOME/CustomFolder -maxdepth 2 -mindepth 2 -type f
```

### Add New File Types

Edit **Map Extensions to Folders** node:

```javascript
const extensionMap = {
  // Add your custom mappings
  'customext': 'Documents/CustomFolder',
  
  // Existing mappings...
  'pdf': 'Documents/PDF',
  // ...
};
```

### Change Destination Folders

Modify the paths in the extension map:

```javascript
'pdf': 'MyDocuments/PDFs',  // Instead of 'Documents/PDF'
```

### Disable Email Notifications

1. Delete or Deactivate the **Send Email** node
2. Connect **Write Log** directly to end of workflow (or leave disconnected)

### Change Schedule Time

Edit **Daily Schedule** node:

- Default: 7:00 PM (19:00)
- Change `triggerAtHour` to your preferred hour (0-23)

## 🐛 Troubleshooting

### Workflow Not Moving Files

**Check:**

1. `dry_run` is set to `false` in Configuration node
2. Home directory path is correct
3. Permissions allow file operations
4. Files actually exist in scanned directories

**Run:**

```bash
# Check permissions
ls -la $HOME/Downloads
ls -la $HOME/Documents

# Test move manually
mv "$HOME/Downloads/test.pdf" "$HOME/Documents/PDF/test.pdf"
```

### Email Not Sending

**Check:**

1. SMTP credentials configured correctly
2. Email node is connected in workflow
3. Check n8n logs for email errors

### Files Going to "Other" Folder

- Extension not in mapping
- Add it to **Map Extensions to Folders** node

### Permission Denied Errors

**Solution:**

```bash
# Fix permissions
chmod 755 $HOME/Downloads
chmod 755 $HOME/Documents
chmod 755 $HOME/Pictures
```

## 📈 Performance

- **Speed**: ~100-150 files organized per second
- **Scalability**: Tested with 1000+ files
- **Memory**: Minimal (no file content reading)
- **Execution Time**: 5-15 seconds for 100-200 files

## 🤝 Contributing

Found a bug or have a suggestion?

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📝 License

This workflow is provided as-is, free to use and modify under MIT license.

## 🔗 Links

- [n8n Documentation](https://docs.n8n.io/)
- [GitHub Repository](https://github.com/Ashok-19/n8n-workflows)

## 📧 Support

For issues or questions:

- Open an issue on GitHub
- Check existing issues for solutions

## ⚠️ Disclaimer

**IMPORTANT**:

- Always run in dry-run mode first
- Test on a small number of files initially
- Backup important files before bulk operations
- This workflow moves files permanently
- Use at your own risk

## 🎉 Acknowledgments

Built with:

- [n8n](https://n8n.io/) - Workflow automation platform
- Standard Unix utilities (find, mv, mkdir)

---

**Tested On:**

- Ubuntu 22.04
- n8n Version 1.114.4

---
