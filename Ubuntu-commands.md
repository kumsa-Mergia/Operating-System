# Ubuntu Commands

## 1. System Information & Management
```bash
uname -r               # Check kernel version
hostnamectl            # Display or set the hostname
lsb_release -a         # Check Ubuntu version
uptime                 # Show system uptime
whoami                 # Show current user
who                    # Show logged-in users
```

## 2. Package Management (APT & DPkg)
```bash
apt update && apt upgrade -y   # Update all packages
apt install <package> -y       # Install a package
apt remove <package> -y        # Remove a package
apt list --installed           # List installed packages
dpkg -l                        # List all installed packages (DPKG)
dpkg -i <package>.deb          # Install a .deb package manually
```

## 3. User & Group Management
```bash
adduser <username>        # Create a new user
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
traceroute <IP/hostname>  # Trace network route (install with `apt install traceroute`)
nslookup <domain>         # Resolve domain name to IP
dig <domain>              # Get detailed DNS info (requires `apt install dnsutils`)
curl -I <URL>             # Fetch HTTP headers from a website
```

## 6. Firewall & Port Issues (UFW & Netstat)
```bash
ufw status               # Check firewall status
ufw allow <port>/tcp     # Allow a specific port
ufw deny <port>/tcp      # Block a specific port
ufw enable               # Enable UFW firewall
ufw disable              # Disable UFW firewall
netstat -tulnp | grep LISTEN  # Check listening ports (install with `apt install net-tools`)
ss -tulnp                     # Show open ports and services
```

## 7. Disk & Filesystem Issues
```bash
df -h                     # Check disk space usage
du -sh /var/log           # Check disk usage of a directory
lsblk                     # List all attached storage devices
fdisk -l                  # List partitions
mount | column -t         # Show mounted filesystems
umount /mnt               # Unmount a filesystem
fsck /dev/sdX             # Check and repair filesystem issues
```

## 8. Kernel & Boot Issues
```bash
uname -r                  # Check running kernel version
update-grub               # Update GRUB bootloader
cat /boot/grub/grub.cfg   # View GRUB configuration
```

## 9. Containerization & Virtualization Issues (Docker, KVM, LXC)
```bash
docker ps -a              # List all containers
docker logs <container>   # View logs of a specific container
docker inspect <container># Get detailed container info
virsh list --all          # List all virtual machines (if using KVM/QEMU)
lxc-ls -f                 # List LXC containers
