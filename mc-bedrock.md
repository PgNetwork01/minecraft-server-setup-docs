# Minecraft Bedrock Server Setup Guide

This guide explains how to set up and host a Minecraft Bedrock Edition server on **PC**, **VPS**, and **Mobile (using Termux)**.

---

## Prerequisites
- Stable internet connection.
- Sufficient system resources:
  - **PC**: 2 GB+ RAM.
  - **VPS**: At least 1 GB RAM.
  - **Mobile**: Modern Android device.

---

## 1. Hosting Minecraft Bedrock Server on a PC

### Requirements
- A decent PC.
- Router access for **port forwarding** (optional).

### Steps
1. **Download the Bedrock Server Software**:
   - Visit [Minecraft Bedrock Server Download Page](https://www.minecraft.net/en-us/download/server/bedrock) and download the appropriate server package for your operating system.

2. **Extract Files**:
   - Extract the downloaded `.zip` file into a folder (e.g., `BedrockServer`).

3. **Configure the Server**:
   - Edit the `server.properties` file to set game settings, maximum players, and the server port.

4. **Start the Server**:
   - Run the `bedrock_server.exe` file (on Windows) or execute the following command in the terminal (on Linux/macOS):
     ```bash
     ./bedrock_server
     ```

5. **Port Forwarding** (optional):
   - Forward port **19132** (default Bedrock port) in your router for public access.

6. **Connect**:
   - Use `localhost` (for local connections) or your public IP (if port forwarded) in Minecraft Bedrock Edition.

---

## 2. Hosting Minecraft Bedrock Server on a VPS

### Requirements
- A Linux-based VPS (e.g., Ubuntu 20.04).
- SSH access to the server.

### Steps
1. **Login via SSH**:
   ```bash
   ssh username@vps_ip
   ```

2. **Download Bedrock Server**:
   - Navigate to the [Bedrock Server Download Page](https://www.minecraft.net/en-us/download/server/bedrock) and copy the link for the Linux version.
   - Download and extract the server:
     ```bash
     mkdir bedrock-server
     cd bedrock-server
     wget <bedrock_server_linux_download_url>
     unzip bedrock-server*.zip
     ```

3. **Run the Server**:
   - Start the server with:
     ```bash
     ./bedrock_server
     ```

4. **Firewall Configuration**:
   - Allow Bedrock server traffic:
     ```bash
     sudo ufw allow 19132
     ```

5. **Keep Server Running**:
   - Use `screen`:
     ```bash
     sudo apt install screen
     screen -S bedrock
     ./bedrock_server
     ```
   - Detach using `Ctrl+A+D`.

6. **Connect**:
   - Use the **VPS IP** in Minecraft Bedrock Edition.

---

## 3. Hosting Minecraft Bedrock Server on Mobile (Termux)

### Requirements
- Android device with Termux app installed.
- Bedrock server package for Linux.

### Steps
1. **Install Termux**:
   - Download and install Termux from [F-Droid](https://f-droid.org/).
   - Update packages:
     ```bash
     pkg update && pkg upgrade
     pkg install wget unzip
     ```

2. **Download Bedrock Server**:
   - Visit the [Bedrock Server Download Page](https://www.minecraft.net/en-us/download/server/bedrock) and copy the Linux version link.
   - Download and extract:
     ```bash
     mkdir bedrock-server
     cd bedrock-server
     wget <bedrock_server_linux_download_url>
     unzip bedrock-server*.zip
     ```

3. **Run the Server**:
   - Start the server:
     ```bash
     ./bedrock_server
     ```

4. **Expose Server Publicly**:
   - Install and configure Ngrok:
     ```bash
     pkg install wget
     wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-arm.zip
     unzip ngrok-stable-linux-arm.zip
     ./ngrok authtoken <your_auth_token>
     ./ngrok tcp 19132
     ```
   - Use the Ngrok-provided address in Minecraft Bedrock Edition.

5. **Join the Server**:
   - Use your device’s IP address (local) or Ngrok address (public).

---

## Notes
- **Performance**: Ensure your system meets the server's requirements.
- **Port Forwarding**: Required for public access without using Ngrok.
- **Backup**: Regularly save the server files to avoid data loss.
- **Resources**: Bedrock servers use fewer resources than Java servers but still benefit from adequate memory and CPU power.

---

Happy crafting! 🎮
