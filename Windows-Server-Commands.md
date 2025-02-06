# Windows Server Commands

## 1. System Information & Management
```powershell
systeminfo                        # Display system details
hostname                          # Show computer name
Get-ComputerInfo                  # Get detailed system information
Get-WindowsFeature                # List installed roles & features
```

## 2. Active Directory (AD) Management
```powershell
Get-ADUser -Filter *              # List all Active Directory users
Get-ADGroup -Filter *             # List all AD groups
New-ADUser -Name "John Doe" -SamAccountName jdoe -UserPrincipalName jdoe@domain.com -Path "OU=Users,DC=domain,DC=com" -Enabled $true  # Create a new AD user
Set-ADUser -Identity jdoe -PasswordNeverExpires $true  # Modify user settings
Get-ADComputer -Filter *          # List all computers in AD
```

## 3. User & Group Management
```powershell
net user                           # List all local users
net user <username> /add           # Create a new local user
net localgroup                     # List all local groups
net localgroup Administrators <username> /add  # Add user to Administrators group
```

## 4. Service Management
```powershell
Get-Service                        # List all services
Get-Service -Name <service>        # Check status of a service
Restart-Service <service>          # Restart a service
Stop-Service <service>             # Stop a service
Start-Service <service>            # Start a service
Set-Service -Name <service> -StartupType Automatic  # Set service to auto-start
```

## 5. Network Troubleshooting
```powershell
ipconfig /all                      # Show network interfaces and IPs
ping <IP/hostname>                 # Test network connectivity
tracert <IP/hostname>              # Trace network route
nslookup <domain>                  # Resolve domain name to IP
netstat -ano                       # Show active network connections
test-netconnection -ComputerName <server> -Port 3389  # Test if a port is open
```

## 6. DNS & DHCP Management
```powershell
Get-DnsServerResourceRecord -ZoneName "domain.com"  # List all DNS records
Add-DnsServerResourceRecordA -ZoneName "domain.com" -Name "webserver" -IPv4Address "192.168.1.10"  # Add an A record
Get-DhcpServerv4Scope                         # List all DHCP scopes
Get-DhcpServerv4Lease -ScopeId 192.168.1.0    # List all DHCP leases
```

## 7. Firewall & Port Issues
```powershell
Get-NetFirewallProfile                       # Show firewall profiles
New-NetFirewallRule -DisplayName "Allow 80" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 80  # Allow port 80
Remove-NetFirewallRule -DisplayName "Allow 80"  # Remove firewall rule
```

## 8. Disk & Filesystem Issues
```powershell
Get-PhysicalDisk                             # List physical disks
Get-Volume                                   # Show volume information
Check-Disk C:                                # Check disk for errors
Get-Disk                                     # Show all attached disks
```

## 9. Boot & Kernel Issues
```powershell
bcdedit                                      # View boot configuration
dism /online /cleanup-image /restorehealth  # Repair system image
sfc /scannow                                 # Scan and fix system files
```

## 10. IIS (Web Server) Management
```powershell
Get-WindowsFeature -Name Web-Server         # Check if IIS is installed
Install-WindowsFeature -Name Web-Server     # Install IIS
Get-IISSite                                 # List all IIS sites
New-Website -Name "MySite" -Port 80 -PhysicalPath "C:\inetpub\mysite"  # Create a new website
```

## 11. Hyper-V (Virtualization) Management
```powershell
Get-VM                                      # List all virtual machines
Start-VM <VMName>                           # Start a virtual machine
Stop-VM <VMName> -Force                     # Stop a virtual machine
New-VM -Name "NewVM" -MemoryStartupBytes 2GB -Generation 2 -NewVHDPath "C:\VMs\NewVM.vhdx" -NewVHDSizeBytes 50GB  # Create a new VM
```

## 12. Windows Updates & Patching
```powershell
Get-WindowsUpdate                           # Check for updates
Install-WindowsUpdate -AcceptAll -AutoReboot  # Install updates automatically
```

## 13. Scheduled Tasks & Automation
```powershell
schtasks /query /fo LIST /v                 # List scheduled tasks
schtasks /create /tn "Backup" /tr "C:\backup.bat" /sc daily /st 01:00  # Create a scheduled backup task
```

## 14. Remote Desktop & Remote Management
```powershell
Test-NetConnection -ComputerName <server> -Port 3389  # Check if RDP is enabled
Enable-PSRemoting -Force                            # Enable PowerShell remoting
Enter-PSSession -ComputerName <server>              # Start a remote PowerShell session
```

## 15. Backup & Restore
```powershell
wbadmin get versions                            # List backup versions
wbadmin start backup -backupTarget:D: -include:C: -allCritical -quiet  # Create a full system backup
wbadmin start recovery -version:06/10/2024-08:00 -itemType:Volume -items:C: -backupTarget:D:  # Restore from backup
