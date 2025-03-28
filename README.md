# OPNsense on GCP
**OPNsense installation guide on Google Cloud Platform (GCP)**:

---

### **1. GCP Setup**  
- **Create a Project**: Start a new project in GCP and enable billing.  
- **Configure VPC Network**: Set up a custom Virtual Private Cloud (VPC) with subnets and firewall rules (allow HTTP/HTTPS, SSH, and OPNsense ports like 443/8443).  

### **2. Create a VM Instance**  
- **Machine Type**: Use at least an `e2-medium` instance for minimal requirements.  
- **Boot Disk**: Select a **FreeBSD 12/13** image (OPNsense is based on FreeBSD).  
- **Network**: Attach the instance to your VPC and enable IP forwarding.  
- **Firewall Rules**: Allow traffic for ports `80`, `443`, `22` (SSH), and OPNsense’s admin interface (default: `443` or `8443`).  

### **3. Install OPNsense**  
- **SSH into the VM**: Use GCP’s SSH terminal or a third-party client.  
- **Download & Write Image**: Fetch the OPNsense ISO, write it to the disk, and reboot.  
- **Configure Interfaces**: Assign `vtnet0` as WAN (public-facing) and `vtnet1` as LAN (internal).  

### **4. Initial OPNsense Setup**  
- **Web Interface**: Access the admin panel via the VM’s external IP (e.g., `https://<external-IP>:443`).  
- **Default Credentials**: Log in with `root`/`opnsense`.  
- **WAN/LAN Configuration**: Assign interfaces, set static/dynamic IPs, and configure DHCP for LAN if needed.  

### **5. Post-Installation**  
- **Firewall Rules**: Define rules for inbound/outbound traffic and NAT.  
- **Plugins & Updates**: Install security plugins and update OPNsense.  
- **Backup**: Save configurations to avoid data loss.  

### **Cost Optimization**  
- Use preemptible instances or shut down VMs when idle to reduce costs.  

---

This process sets up a secure, customizable firewall/router on GCP using OPNsense. 
