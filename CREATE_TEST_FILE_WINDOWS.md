# MemU Test File Creation Guide

## 🚀 Option 1: Create Test File Directly on Windows (RECOMMENDED)

No VPS or SSH needed! Just create the file yourself:

```powershell
# Create test file directly
@"
from memu import MemUService

service = MemUService(
    llm_profiles={
        'default': {
            'base_url': 'https://open.bigmodel.cn/api/paas/v4',
            'api_key': '47a38aead2934fbf895212441324e6b8.zLwKKwsEaXpUHR2a',
            'chat_model': 'glm-4',
            'client_backend': 'httpx',
            'embedding': {
                'model': 'embedding-2'
            }
        }
    }
)

result = service.memorize(
    resource_url='text://hello world',
    modality='conversation',
    user={'user_id': 'test'}
)

print(f'✅ Memorized! Categories: {result["categories"]}')
print(f'✅ Items extracted: {len(result["items"])}')
"@ | Out-File -Encoding utf8 test_memu.py

# Run it
python test_memu.py
```

Expected Output:
```
✅ Memorized! Categories: [...]
✅ Items extracted: X
```

## 🚀 Option 2: Use SCP for File Transfer

On VPS, create a simpler file without heredoc:

```bash
# On VPS (rew516)
cat > /home/jlutu/memu-enhanced/test_memu_simple.py 'from memu import MemUService
service = MemUService(
    llm_profiles={
        "default": {
            "base_url": "https://open.bigmodel.cn/api/paas/v4",
            "api_key": "47a38aead2934fbf895212441324e6b8.zLwKKwsEaXpUHR2a",
            "chat_model": "glm-4",
            "client_backend": "httpx",
            "embedding": {
                "model": "embedding-2"
            }
        }
    }
)
result = service.memorize(
    resource_url="text://hello world",
    modality="conversation",
    user={"user_id": "test"}
)
print(f"✅ Memorized! Categories: {result["categories"]}")
print(f"✅ Items extracted: {len(result["items"])}")
'
```

Then on Windows:
```powershell
# Copy from VPS
scp jonlutu@rew516:/home/jlutu/memu-enhanced/test_memu_simple.py C:\Users\jonlutu\memu-enhanced\test_memu_simple.py

# Then run it
python test_memu_simple.py
```

## 🚀 Option 3: Create File Manually (QUICKEST)

Just open Notepad or VS Code and paste this content:

```python
from memu import MemUService

service = MemUService(
    llm_profiles={
        'default': {
            'base_url': 'https://open.bigmodel.cn/api/paas/v4',
            'api_key': '47a38aead2934fbf895212441324e6b8.zLwKKwsEaXpUHR2a',
            'chat_model': 'glm-4',
            'client_backend': 'httpx',
            'embedding': {
                'model': 'embedding-2'
            }
        }
    }
)

result = service.memorize(
    resource_url='text://hello world',
    modality='conversation',
    user={'user_id': 'test'}
)

print(f'✅ Memorized! Categories: {result["categories"]}')
print(f'✅ Items extracted: {len(result["items"])}')
```

Then save as `test_memu.py` and run!

## 💡 Why Option 1 Is Best

- ✅ Fastest - No VPS SSH issues
- ✅ Simplest - Just paste and run
- ✅ No dependencies - Works immediately
- ✅ No authentication problems

## 🎯 RECOMMENDATION

**Use Option 1** - Create the test file directly in Notepad or VS Code with the content shown above. This avoids all SSH/SCP issues entirely and gets you testing MemU + GLM integration immediately!