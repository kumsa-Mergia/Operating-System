# Red Hat Enterprise Linux (RHEL) Commands

## 1. System Information & Management
```bash
uname -r               # Check kernel version
hostnamectl            # Display or set the hostname
cat /etc/redhat-release # Check RHEL version
uptime                 # Show system uptime
whoami                 # Show current user
who                    # Show logged-in users
```

## 2. Package Management (DNF & RPM)
```bash
dnf update -y                # Update all packages
dnf install <package> -y     # Install a package
dnf remove <package> -y      # Remove a package
dnf list installed           # List installed packages
dnf search <package>         # Search for a package
rpm -qa                      # List all installed RPM packages
```

## 3. User & Group Management
```bash
useradd <username>        # Create a new user
passwd <username>         # Set password for a user
usermod -aG <group> <user> # Add user to a group
groupadd <groupname>      # Create a new group
id <username>             # Get user ID and group ID
whoami                    # Show current user
```

## 4. Service Management (Systemd)
```bash
systemctl status <service>  # Check status of a service
systemctl start <service>   # Start a service
systemctl stop <service>    # Stop a service
systemctl restart <service> # Restart a service
systemctl enable <service>  # Enable service to start at boot
systemctl disable <service> # Disable service from starting at boot
```

## 5. Network Troubleshooting
```bash
ip a                      # Show network interfaces and IPs
ip r                      # Show routing table
nmcli device status       # Show network connection status
ping <IP/hostname>        # Test network connectivity
traceroute <IP/hostname>  # Trace network route (install with `dnf install traceroute`)
nslookup <domain>         # Resolve domain name to IP
dig <domain>              # Get detailed DNS info (requires `dnf install bind-utils`)
curl -I <URL>             # Fetch HTTP headers from a website
```

## 6. Firewall & Port Issues (Firewalld & Netstat)
```bash
firewall-cmd --list-all               # Show firewall rules
firewall-cmd --list-ports             # List open ports
firewall-cmd --add-port=8080/tcp --permanent  # Open a port
firewall-cmd --reload                 # Reload firewall rules
netstat -tulnp | grep LISTEN           # Check listening ports (install with `dnf install net-tools`)
ss -tulnp                              # Show open ports and services
```

## 7. SELinux Troubleshooting
```bash
sestatus                  # Check if SELinux is enabled
getenforce                # Get current SELinux mode
setenforce 0              # Temporarily disable SELinux
setenforce 1              # Re-enable SELinux
cat /var/log/audit/audit.log | grep AVC  # Check SELinux denials
aausearch -m AVC          # Find SELinux AVC denials
```

## 8. Disk & Filesystem Issues
```bash
df -h                     # Check disk space usage
du -sh /var/log           # Check disk usage of a directory
lsblk                     # List all attached storage devices
fdisk -l                  # List partitions
mount | column -t         # Show mounted filesystems
umount /mnt               # Unmount a filesystem
fsck /dev/sdX             # Check and repair filesystem issues
```

## 9. Kernel & Boot Issues
```bash
uname -r                  # Check running kernel version
grub2-editenv list        # Check bootloader settings
cat /boot/grub2/grub.cfg  # View GRUB configuration
dracut -f                 # Rebuild initramfs (if boot issues occur)
```

## 10. Containerization & Virtualization Issues (Podman, Docker, VM)
```bash
podman ps -a              # List all containers
podman logs <container>   # View logs of a specific container
podman inspect <container># Get detailed container info
virsh list --all          # List all virtual machines (if using KVM/QEMU)
