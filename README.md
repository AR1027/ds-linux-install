# BIOVIA Discovery Studio 2025 – Linux Installation Scripts

This repository contains scripts and documentation to install **BIOVIA Discovery Studio 2025 Client** on Ubuntu Linux.

## What’s Included  
- `install_biovia_ds.sh`: A wrapper script that extracts the `.bin` installer, patches its internal script to use `bash`, and then runs it.  
- `start_ds.sh`: A simple launcher script to start Discovery Studio after installation.  
- `README.md`: This file of documentation.

## Installation Instructions  
1. Download the `BIOVIA_DS2025Client.bin` from BIOVIA (you must have permission/license).  
2. Place the `.bin` installer in your `~/Downloads` directory.  
3. Install the required dependencies using:  
   ```bash
   sudo apt update  
   sudo apt install bash csh tcsh libglu1-mesa libglew2.2 libpng16-16 libxml2  
   ```  
4. Make the installer executable and run it with bash:  
   ```bash
   chmod +x ~/Downloads/BIOVIA_DS2025Client.bin  
   bash ~/Downloads/BIOVIA_DS2025Client.bin  
   ```  
5. After installation, create the launcher script `~/BIOVIA/DiscoveryStudio2025/biovia.sh` with these contents:  
   ```bash
   #!/bin/bash  
   export LD_LIBRARY_PATH=/home/user/BIOVIA/DiscoveryStudio2025/lib:$LD_LIBRARY_PATH  
   /home/user/BIOVIA/DiscoveryStudio2025/bin/DiscoveryStudio2025  
   ```  
6. Make the launcher executable:  
   ```bash
   chmod +x ~/BIOVIA/DiscoveryStudio2025/biovia.sh  
   ```  
7. Run Discovery Studio using:  
   ```bash
   ~/BIOVIA/DiscoveryStudio2025/biovia.sh  
   ```

## ⚠️ Warnings & Risks  
- This method may include the step:  
  ```bash
  sudo ln -sf /bin/bash /bin/sh
  ```  
  This *changes* the system `/bin/sh` symlink to `bash`, which is risky and can break other scripts. Revert it after installation with:  
  ```bash
  sudo ln -sf /bin/dash /bin/sh
  ```  
- You **must** have a legal license for Discovery Studio — this repository does *not* include the `.bin` file.  
- Discovery Studio may require additional libraries (OpenGL, GLU, etc.) to run correctly.

## License  
These scripts are free for personal use. Do **not** share the proprietary `.bin` file — always download it from BIOVIA / 3DS legally.
