# Suricata

> Suricata is **an open-source threat detection engine that functions as an intrusion detection system (IDS), intrusion prevention system (IPS), and network security monitoring (NSM) tool**. It analyzes network traffic for threats like viruses and denial-of-service attacks by using a powerful ruleset and can either alert administrators to the threats or automatically block malicious traffic.
> 

# **Steps to Install and Configure Suricata**

# **Step 1: Download Suricata**

1. Visit the official [Suricata download page](https://suricata.io/download/)
2. Download the latest version of Suricata for Windows.

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd00bfdabafd7071b35_AD_4nXcd_LjAQ-IP9gYykL1UHCdNSmVRbiwJaJ5GdVxe3eH0z1RvfuY6cVG4L1LBobLFXqyz-KtW7CCbeQeWoSMq-oselEaVbT-O2rE11VyngR7sZBL6mnY4uiBf2scRr0cn7MaeAxypbdV988QQAvkMEy0N5Ek.png)

‍

# **Step 2: Install WinPcap or Npcap**

Suricata requires a packet capture library like WinPcap or Npcap to capture network traffic.

‍

**Download and Install Npcap** (recommended):

- Visit the [Npcap download page](https://npcap.com/#download).
- Download the latest version of Npcap.

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd09f1bcd78f29930d5_AD_4nXf6dXW-JM5LMPiagXqMppk3Kjljm-oftFyWVfk1YuFu5z2Ju_jl-0P-p65QSU5eW8vkHSbA-sQNjqEVNYzthg4Tn6ZbKdCEMg9ILUq59qvHFBVyAyvUGsDwY-i5n5tjiedTmDCvCUFG9Fbh89lIJ7SFgFOl.png)

‍

- Run the installer and follow the on-screen instructions to complete the installation.
- Make sure to select the option to install Npcap in "WinPcap API-compatible mode".

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd0954529db6bf28b45_AD_4nXcu-zEm-1G8S4rqdh73WIJcpDE5CS8IPFGTs-tI8lsFDFbpU_KSJw3LGpwHHV0QnIZ2zq3uX-2YklPcqdW4r39LI6E_7TXr6tkxStIOA_dYfQ9bKg6suOL3ETQkK79Vhwipv9vptlaEdc5gmWkt44GzYEo.png)

‍

**Alternative: Download and Install WinPcap**:

- Visit the [WinPcap download page.](https://www.winpcap.org/install/)
- Download and install the latest version of WinPcap.

‍

# **Step 3: Install Suricata**

1. Double Click on the file you downloaded
2. Run the suricata-<version>.msi file to start the Suricata installation.
3. Follow the normal process installation Next > Next etc..
4. At the end you will get this Icon on desktop

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd0224cfc7be34ecc0c_AD_4nXetpUIQJ-20VvT88V3y5vjX4rmjquoNCPEcO5uz4z-NDmcHqbFW72-m4PqmojXYky0Lr6F-az5DNSjjpPopHgomWN4GclhISYCiFIO7Zd7uhmtdtU_ZFcKFr9RtDvWB0jkDfjM3M5YYEnrmMmlPPFwQ3t0u.png)

‍

# **Step 4: Configure Suricata**

**Create Suricata Configuration File**:

- Navigate to the suricata directory where the configuration file is located (usually C:\\Program Files\\Suricata or the directory where you extracted Suricata).
- Open the suricata.yaml configuration file using a text editor like Notepad++.

‍

**Edit Network Interface Settings**:

- Find the af-packet section in the suricata.yaml file.

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd0af6ab5e3d4290b6b_AD_4nXdThox9Rhzh8n0cshXEHertnr2Ss1MXVvJFQcz-m39VnebWGs9UKyIrZn2yfM0_sBclnc4J7pGEVDrxUyL-2j-zybOCLFVRi3dzxhsu8SPBiTC1TyJHPIk9dHfB9yxOdK_qV6orgS-oW5M6JBeumzbNP_Q.png)

‍

- Replace the interface name with the correct network interface name on your system. You can find the interface name by running ipconfig /all in the command prompt.

‍

Example:

‍

```jsx
 af-packet:
  - interface: "Ethernet"
    threads: 4
    cluster-id: 99
    cluster-type: cluster_flow
    defrag: yes
```

‍

**Update Rule Files**:

- Suricata uses rule files to [detect threats](https://app.letsdefend.io/path/detection-engineering-path). You can download the latest rule sets from the [Emerging Threats website.](https://rules.emergingthreats.net/open/)

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd035913ff197ae7897_AD_4nXePCCkAe0IGSvZ6HWp_JOuO0bjGZ6V6sci1NEUwvF7mWN3jHmcbxaGVoHoDbZFRbC3_15jnd06R_QdnKNyQTu23Ual-_qFRTAGHEugMe8X1I0IQBqNTFP5tyjsAdQHiJ0aouBtq548Hyf6wh19DKejEOygS.png)

‍

- Here you need to choose the closest version to your Suricata, in my case it’s 7.0.6 So I will choose 7.0.3
- You can download all the rules from emerging-all.rules or if you want something custom you can go to the rules directory and choose what suits you.

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd0e0920d36114d051b_AD_4nXdimkvSUhZY_GXAKcpQnVtC1bnBHMT1yFR12JHyb0_kNjlkh32EDpHdQRFMMwMIoYuWIaPU2DdW0SNm0ivmD9xkE-uL1SincuB4tMmoJvB761aUI_LfY4tOc3QZUfXkVdE8e3p1cmDUlbCqgnMGSuAtYLhF.png)

‍

- Download the rules and save them in the rules directory of your Suricata installation.
- Update the rule-files section in the suricata.yaml file to include the downloaded rule files.

‍

Example:

```jsx
 rule-files:
  - emerging-all.rules
```

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd0af6ab5e3d4290b64_AD_4nXeBZs6rDsA3KzzJiGtBU7jBNzrwRSFF4OiAeI82hyLfaF11hG9XvmtB60kyKqwjM6aoLm0jEAZx1zQoCqU2MtuVIA-a0H2wSotlciTt3rFvFLhz5KQjTTcIOjO0QEaannUKc1QpSLHnGV--2wPV4AsaVuKL.png)

‍

# **Step 5: Running Suricata**

1. Open the command prompt as an administrator.
2. Navigate to the Suricata installation directory.
3. Run Suricata with the following command: Replace <interface> with the name of your network interface. suricata.exe -c suricata.yaml -i <interface>

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd091209425740b17ed_AD_4nXcXAwTsJWdXPXn6hCzp73BLmehxhh8X5gKee6zQu8N-v2fVCkWVyhy6P7BQ8FuXK4xCSrJ20gi8x71P0M38ouMn7DFdFaId8dmv7yCXWz3Pu1rRecAEz7wWn1uuinkHCUMIfNSR-VeZvS4M5kZNN0TtStw.png)

‍

# **Step 6: Verify Suricata Installation**

1. Check the Suricata log files to ensure it is running correctly. Logs are typically found in the log directory of the Suricata installation.
2. Open the suricata.log file to check for any errors or warnings.
3. Any alert will appear in fast.log or eve.json in the log directory

‍

![](https://cdn.prod.website-files.com/65e1f74aeadd13bc01d31d46/67081dd00bfdabafd7071b32_AD_4nXeZUatWHj3fR8CM2b_kM-v74uP7t8D7pV-WAkhyRRU_kq4OW7uGN8cwPZcuViGhoAdYyRxCldWIPBMaaTbcSdzT4qReI4aYoYSOjfGyJIhaQ07kA_NdWjuWx3fPdEy4m6i0SteWr5-tmdea9nhQWrsuRZGQ.png)

‍

# **Troubleshooting**

# **Common Issues**

- **Permission Errors**: Ensure you are running the command prompt as an administrator.
- **Incorrect Interface Name**: Verify the network interface name using ipconfig /all and update the suricata.yaml file accordingly.
- **Missing Dependencies**: Make sure Npcap or WinPcap is installed correctly.

‍

# **Useful Commands**

To test Suricata configuration:

```jsx
suricata.exe -T -c suricata.yaml
```

## Run Suricata as a Windows Service (Recommended)

This allows Suricata to:

- Start automatically when Windows boots.
- Run quietly in the background.
- Keep writing to logs even if you close PowerShell.

### Step-by-Step:

1. **Open PowerShell as Administrator**
2. **Install the service:**
    
    ```powershell
    suricata.exe --install-service
    
    ```
    
3. **Start the service:**
    
    ```powershell
    net start suricata
    
    ```
    
4. **Check service status:**
    
    ```powershell
    Get-Service suricata
    
    ```
    
    You should see:
    
    ```
    Status   Name               DisplayName
    ------   ----               -----------
    Running  suricata           Suricata IDS/IPS
    
    ```
    
5. **Logs location:**
    
    By default:
    
    ```
    C:\ProgramData\Suricata\log\fast.log
    
    ```
    
    You can open this with Notepad or run:
    
    ```powershell
    Get-Content "C:\ProgramData\Suricata\log\fast.log" -Wait
    
    ```
    
    to watch live alerts.
    

---

## Uninstall or Stop the Service

If you ever want to stop or remove it:

```powershell
net stop suricata
suricata.exe --remove-service

```

‍


