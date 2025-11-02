# n8n Workflows Collection

A curated collection of production-ready n8n workflows for automation, productivity, and system management.

## 🎯 Purpose

This repository contains battle-tested n8n workflows designed to automate common tasks, improve productivity, and streamline system operations. Each workflow is fully documented, sanitized for public use, and ready to import into your n8n instance.

## 📁 Available Workflows

### [File Organizer](file-organizer/)

Intelligent file organization workflow that automatically sorts files based on their extensions.

**Features:**
- 🎯 Supports 133+ file types
- 📊 Extension-based categorization
- 📧 Email notifications
- 🗓️ Scheduled execution
- 🛡️ Edge case handling
- 📝 Comprehensive logging

**Status:** ✅ Production Ready  
**OS:** Linux (Ubuntu, Debian, Fedora)  
**Version:** 1.0.0

[View Documentation →](file-organizer/README.md)

---

## 🚀 Quick Start

1. **Choose a workflow** from the list above
2. **Navigate to its folder** and read the README
3. **Follow the SETUP.md** for installation instructions
4. **Import the workflow.json** into your n8n instance
5. **Configure** according to your needs

## 📋 Requirements

### General Requirements
- n8n version 1.0.0 or higher
- Node.js 18.x or higher
- Active n8n instance (self-hosted or cloud)

### Workflow-Specific Requirements
Each workflow has its own requirements listed in its README file.

## 📖 Documentation

Each workflow includes:
- **README.md** - Complete documentation
- **SETUP.md** - Quick setup guide
- **workflow.json** - Importable n8n workflow
- **CHANGELOG.md** - Version history

## 🔧 Installation

### Method 1: Import Individual Workflow

```bash
# Download the workflow.json from the specific workflow folder
# In n8n: Click "+" → "Import from File" → Select workflow.json
```

### Method 2: Clone Repository

```bash
git clone https://github.com/Ashok-19/n8n-workflows.git
cd n8n-workflows
# Navigate to desired workflow folder
```

## 🤝 Contributing

While this is a personal collection, suggestions and improvements are welcome:

1. Open an issue for bugs or feature requests
2. Fork the repository for major changes
3. Submit a pull request with clear description

## 📄 License

These workflows are provided as-is, free to use and modify for personal or commercial purposes.

## ⚠️ Disclaimer

- Always test workflows in a safe environment first
- Backup important data before running automation workflows
- Review and customize workflows for your specific needs
- Use at your own risk

## 🔗 Resources

- [n8n Official Documentation](https://docs.n8n.io/)
- [n8n Community Forum](https://community.n8n.io/)
- [n8n GitHub Repository](https://github.com/n8n-io/n8n)

## 📧 Contact

For issues or questions about these workflows:
- Open an issue on GitHub
- Check existing issues for solutions

---

**Repository Structure:**
```
n8n-workflows/
├── README.md                    # This file
├── .gitignore                   # Git ignore rules
├── file-organizer/              # File organization workflow
│   ├── README.md
│   ├── SETUP.md
│   ├── workflow.json
│   └── ...
└── (future workflows...)
```

---

**Last Updated:** November 2025  
**Maintained by:** [@Ashok-19](https://github.com/Ashok-19)
# n8n-workflows
