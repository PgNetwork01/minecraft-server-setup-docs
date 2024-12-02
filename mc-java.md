# Minecraft Java Edition Server Setup Guide

This guide explains how to set up and host a Minecraft server on **PC**, **VPS**, and **Mobile (using Termux)**.

---

## Prerequisites
- **Java** (Java Edition server only).
- **Stable internet connection**.
- Sufficient system resources:
  - At least 4 GB RAM recommended for smooth performance.

---

## 1. Hosting Minecraft Server on a PC

### Requirements
- A decent PC.
- Router access for **port forwarding** (optional).

### Steps
1. **Download the Server Software**:
   - Visit [Minecraft's official server download page](https://www.minecraft.net/en-us/download/server) and download the `.jar` file.

2. **Setup the Server**:
   - Create a folder (e.g., `MinecraftServer`) and place the downloaded `.jar` inside.
   - Open a terminal in the folder and run:
     ```bash
     java -Xmx1024M -Xms1024M -jar server.jar nogui
     ```

3. **Agree to EULA**:
   - Open `eula.txt`, set `eula=true`, and save.

4. **Customize Server**:
   - Modify `server.properties` for game settings.

5. **Enable Port Forwarding**:
   - Forward port `25565` on your router for public access.

6. **Start the Server**:
   - Relaunch using the `java` command.

7. **Connect**:
   - Use `localhost` or your **public IP** in Minecraft.

---

## 2. Hosting Minecraft Server on a VPS

### Requirements
- A Linux VPS (e.g., Ubuntu 20.04) with at least 2 GB RAM.
- SSH access.

### Steps
1. **Login via SSH**:
   ```bash
   ssh username@vps_ip
   ```

2. **Install Java**:
   ```bash
   sudo apt update
   sudo apt install openjdk-17-jre-headless
   ```

3. **Download Server**:
   ```bash
   mkdir minecraft-server
   cd minecraft-server
   wget https://launcher.mojang.com/v1/objects/<server_jar_url>
   ```

4. **Run Server**:
   ```bash
   java -Xmx1024M -Xms1024M -jar server.jar nogui
   ```

5. **Firewall Configuration**:
   ```bash
   sudo ufw allow 25565
   ```

6. **Keep Server Running**:
   - Use `screen`:
     ```bash
     sudo apt install screen
     screen -S minecraft
     java -Xmx1024M -Xms1024M -jar server.jar nogui
     ```
   - Detach using `Ctrl+A+D`.

7. **Access**:
   - Use your **VPS IP** in Minecraft.

---

## 3. Hosting Minecraft Server on Mobile (Termux)

### Requirements
- Android device.
- Termux app (from [F-Droid](https://f-droid.org/)).

### Steps
1. **Install Termux**:
   - Update packages:
     ```bash
     pkg update && pkg upgrade
     pkg install openjdk-17 wget
     ```

2. **Download Server**:
   ```bash
   mkdir minecraft-server
   cd minecraft-server
   wget https://launcher.mojang.com/v1/objects/<server_jar_url>
   ```

3. **Run Server**:
   ```bash
   java -Xmx1024M -Xms1024M -jar server.jar nogui
   ```

4. **Expose Server Publicly (Optional)**:
   - Install and set up Ngrok:
     ```bash
     pkg install wget
     wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-arm.zip
     unzip ngrok-stable-linux-arm.zip
     ./ngrok authtoken <your_auth_token>
     ./ngrok tcp 25565
     ```
   - Use the Ngrok-provided address to connect.

5. **Join the Server**:
   - Use the public address from Ngrok in Minecraft.

---

## Notes
- **Performance**: Consider using optimized server software like [Paper](https://papermc.io/).
- **Backup**: Regularly back up server files.
- **Public Access**: Ensure proper port forwarding/firewall settings.
- **RAM Management**: Adjust `-Xmx` and `-Xms` values based on your device's memory.

---

Happy crafting! 🎮
