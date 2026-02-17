# 🚀 Quick Start Guide - MemU v1.4.0 on Windows

**For Jonathan's setup**: Miniconda3 + Python 3.12.1

## 🔧 **Fix Python Version Issue**

### **Create Python 3.13 Environment (Recommended):**

```powershell
# Create dedicated environment for MemU
conda create -n memu-env python=3.13 -y
conda activate memu-env

# Navigate to MemU repository
cd C:\Users\jonlutu\memu-enhanced

# Install MemU v1.4.0
pip install -e .
```

### **Test Installation:**

```powershell
# Quick functionality test
python tests/test_inmemory.py
```

### **Set OpenAI API Key:**

```powershell
# Option 1: Environment variable
$env:OPENAI_API_KEY = "sk-your-actual-openai-key-here"

# Option 2: .env file
echo "OPENAI_API_KEY=sk-your-actual-openai-key-here" > .env
```

## 📋 **Backup Current MemU Bot Configs**

```powershell
# Create timestamped backup
$backupDir = "C:\Users\jonlutu\memu-backup-$(Get-Date -Format 'yyyy-MM-dd-HHmm')"
mkdir $backupDir

# Backup everything from desktop MemU Bot
Copy-Item "C:\Users\jonlutu\AppData\Roaming\memu-bot\*" -Destination $backupDir -Recurse -Force

# Verify backup
Get-ChildItem $backupDir -Recurse | Measure-Object | Select-Object Count
Write-Host "✅ Backup complete: $(Get-ChildItem $backupDir | Measure-Object | Select-Object -ExpandProperty Count) items backed up"
```

## 🎯 **What Gets You:**

✅ **Python 3.13 environment** - Meets MemU v1.4.0 requirement  
✅ **Latest MemU features** - 4 versions newer than desktop v1.0.0.0  
✅ **Config backup** - All your current settings preserved  
✅ **Test ready** - Quick validation that installation works

## 💡 **Quick Reference:**

**Conda Commands:**
- `conda env list` - See all environments
- `conda activate memu-env` - Switch to MemU environment
- `conda deactivate` - Leave environment

**MemU Testing:**
- `tests/test_inmemory.py` - In-memory test
- `tests/test_postgres.py` - PostgreSQL test

**After Installation:**
- Check examples/ folder for usage examples
- Review README.md for detailed documentation

## 🚨 **If Installation Fails:**

1. **Check Python version**: `python --version` should be 3.13+
2. **Check dependencies**: `pip install --upgrade pip` might help
3. **Create fresh environment**: `conda env remove -n memu-env` then recreate

---

**Created for quick MemU v1.4.0 setup on Windows with Python version compatibility fixes!**