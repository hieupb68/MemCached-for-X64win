# MemCached-for-X64win  

**Memcached build for Windows using Cygwin**  

---

## 📌 Installation Guide  

---

### 1️⃣ Install Memcached as a Windows Service  

#### 📂 **Step 1: Copy `nssm-2.25.0.exe`**  

Move the `nssm-2.25.0.exe` file to the Memcached folder or any directory included in `%PATH%`.  

#### 🖥️ **Step 2: Run the installation commands**  

Run the following commands in **Command Prompt** (Administrator).  
**Note**: Adjust `C:\memcached` to match your installation directory.  

```sh
nssm-2.25.0.exe install memcached C:\memcached\memcached-avx.exe
nssm-2.25.0.exe set memcached AppParameters "-vv -m 512 -I 256m"
nssm-2.25.0.exe set memcached AppDirectory C:\memcached
nssm-2.25.0.exe set memcached AppExit Default Restart
nssm-2.25.0.exe set memcached AppNoConsole 1
nssm-2.25.0.exe set memcached AppPriority ABOVE_NORMAL_PRIORITY_CLASS
nssm-2.25.0.exe set memcached AppStderr C:\memcached\logs\memcached.log
nssm-2.25.0.exe set memcached AppStopMethodSkip 6
nssm-2.25.0.exe set memcached AppTimestampLog 1
nssm-2.25.0.exe set memcached DisplayName "Memcached Service"
nssm-2.25.0.exe set memcached ObjectName LocalSystem
nssm-2.25.0.exe set memcached Start SERVICE_AUTO_START
nssm-2.25.0.exe set memcached Type SERVICE_WIN32_OWN_PROCESS

----
Verify Memcached is Running
Check if Memcached is listening on port 11211
Open PowerShell and run:
Test-NetConnection -ComputerName localhost -Port 11211
If the result shows:
TcpTestSucceeded : True
🎉 Memcached is running successfully!
Check Active Connections
Run the following command in PowerShell to display all active connections on Memcached's port:
Get-NetTCPConnection -LocalPort 11211
Manage Memcached Service
▶️ Start Memcached
nssm-2.25.0.exe start memcached
⏹️ Stop Memcached
nssm-2.25.0.exe stop memcached
🔄 Restart Memcached
nssm-2.25.0.exe restart memcached
❌ Uninstall Memcached Service
nssm-2.25.0.exe remove memcached confirm

