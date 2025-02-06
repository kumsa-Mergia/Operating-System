# Windows Commands

## 1. System Information & Management
```powershell
systeminfo             # Display system details
hostname               # Show computer name
wmic os get Caption    # Get Windows version
whoami                 # Show current user
```

## 2. Process Management
```powershell
tasklist               # List running processes
taskkill /F /PID <pid> # Kill a process by PID
taskkill /IM <name>    # Kill a process by name
```

## 3. User & Group Management
```powershell
net user               # List all users
net user <username>    # Get user details
net user <username> /add <password>  # Create a new user
net localgroup         # List groups
net localgroup Administrators <username> /add  # Add user to Administrators group
```

## 4. Service Management
```powershell
sc query               # List services
sc start <service>     # Start a service
sc stop <service>      # Stop a service
sc config <service> start= auto  # Set service to start automatically
```

## 5. Network Troubleshooting
```powershell
ipconfig /all          # Show network interfaces and IPs
ping <IP/hostname>     # Test network connectivity
tracert <IP/hostname>  # Trace network route
nslookup <domain>      # Resolve domain name to IP
netstat -ano           # Show active network connections
```

## 6. Firewall & Port Issues
```powershell
netsh advfirewall show allprofiles  # Show firewall status
netsh advfirewall firewall add rule name="Open Port" dir=in action=allow protocol=TCP localport=<port>  # Open a port
netsh advfirewall firewall delete rule name="Open Port"  # Close a port
```

## 7. Disk & Filesystem Issues
```powershell
chkdsk C:              # Check disk for errors
wmic logicaldisk get name, freespace, size  # Get disk space details
dir /s /b | sort /R    # Find largest files in a directory
diskpart               # Open disk partition tool
```

## 8. Boot & Kernel Issues
```powershell
bcdedit                # View boot configuration
dism /online /cleanup-image /restorehealth  # Repair system image
sfc /scannow           # Scan and fix system files
```

## 9. Task Scheduler & Automation
```powershell
schtasks /query /fo LIST /v  # List scheduled tasks
schtasks /create /tn "MyTask" /tr "C:\script.bat" /sc daily /st 10:00  # Create a scheduled task
```

## 10. Containerization & Virtualization (Docker, Hyper-V)
```powershell
docker ps -a            # List all Docker containers
docker logs <container> # View logs of a container
Get-VM                 # List all virtual machines (if using Hyper-V)
Start-VM <VMName>      # Start a virtual machine
