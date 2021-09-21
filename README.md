# Zabbix Monitoring for StorageCraft ShadowProtectSPX and ImageManager
Template Zabbix to monitor StorageCraft ShadowProtectSPX and ImageManager

This template will automatically monitor your Backup tasks and ImanageManager consolidations tasks. It includes also triggers if advanced verification of collapse is late or failed.

To integrate in your Zabbix Dashboard, create a *widget* **Data overview** and use the *Application* **StorageCraft Dashboard** with *Host location* on **Top**.

Works for Zabbix 5.x Active Agent

## Discovery of ShadowProtectSPX Backup Task
The discovery is based on the a successful eventID 3 in Windows Log.

## Discovery of ImageManager Collapse Task
The discovery is based on the a successful eventID 1120 in Windows Log which show the successful creation of a collapse file.

I only store my backups on NAS... so the Regex in the template are only working where EventData look something like:

```
\\nas\mountname\MACHINE\ft-backup\C_VOL-b001-i001-cd-cw.spi 
\\nas\mountname\MACHINE\C_VOL-b001-i001-cd-cw.spi 
```

Note also that the subfolder "ft-backup" is not mandatory and only for organization purpose.

## Useful links
https://support.storagecraft.com/s/article/Windows-Event-Log-IDs-created-by-StorageCraft-products?language=en_US
