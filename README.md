# Zabbix Monitoring for StorageCraft ShadowProtectSPX and ImageManager
The StorageCraft Monitoring Template is designed to streamline the monitoring of ShadowProtectSPX backups and ImageManager collapses.

To integrate in your Zabbix Dashboard, create a *widget* **Data overview** and use the *Application* **StorageCraft Dashboard** with *Host location* on **Top**.

Works for Zabbix 6.0 Active Agent

## Features

1. **Discovery Rule**: Automates the discovery of new tasks using a predefined discovery rule. This ensures that any new tasks that are added are automatically integrated into the monitoring regime without manual configuration.
   
2. **Regular Expression Processing**: It processes each line of the returned value to check for specific patterns that indicate task status, thereby automating the process of monitoring task success or failure.
   
3. **Dynamic Macro Configuration**: Allows for the customization of various thresholds and monitoring behaviors. Each macro is accompanied by a detailed description for clarity.


## Macros

### 1. `{$STORAGECRAFT.BACKUP.CRIT}`
- **Value**: `5d`
- **Description**: This macro defines the critical threshold for the age of the most recent successful backup. If a successful backup hasn't been conducted within the past 5 days, a critical alert will be triggered.

### 2. `{$STORAGECRAFT.BACKUP.WARN}`
- **Value**: `3d`
- **Description**: Specifies the warning threshold for the age of the latest successful backup. It raises a warning if no successful backup is detected within the past 3 days.

### 3. `{$STORAGECRAFT.COLLAPSE.CHKDSK}`
- **Value**: `1`
- **Description**: This macro determines if the "No CHKDSK" trigger is activated by default. A value of '1' means it's enabled.

### 4. `{$STORAGECRAFT.COLLAPSE.CHKDSK.CRIT}`
- **Value**: `14d`
- **Description**: Sets the maximum age threshold for the most recent successful CHKDSK operation on a Collapse. If a successful CHKDSK hasn't been executed within the past 14 days, an alert will be initiated.

### 5. `{$STORAGECRAFT.COLLAPSE.CHKDSK.INFO}`
- **Value**: `1h`
- **Description**: Specifies the duration for which info on a successful CHKDSK should be displayed. Any successful CHKDSK operation within the last hour will have its details shown.

### 6. `{$STORAGECRAFT.COLLAPSE.CHKDSK:"DEVT-ST001"}`
- **Value**: `0`
- **Description**: An example of a macro tailored for a specific machine. This macro disables CHKDSK triggers for the mentioned machine (`DEVT-ST001`).

### 7. `{$STORAGECRAFT.COLLAPSE.CRIT}`
- **Value**: `7d`
- **Description**: Specifies the critical threshold for the age of the most recent successful Collapse operation. A critical alert will be raised if a successful Collapse hasn't taken place within the past 7 days.

### 8. `{$STORAGECRAFT.COLLAPSE.IGNORE}`
- **Value**: `0`
- **Description**: Governs the activation status of triggers for ImageManager. By default, these triggers are active. If set to '1', it would disable all associated triggers.

### 9. `{$STORAGECRAFT.COLLAPSE.IGNORE:"DEVT-ST001 [C_VOL-b001]"}`
- **Value**: `1`
- **Description**: An example macro that deactivates triggers for a particular chain of a machine. This specific macro would disable triggers for the chain `DEVT-ST001 [C_VOL-b001]`.

### 10. `{$STORAGECRAFT.COLLAPSE.IGNORE:"DEVT-ST001"}`
- **Value**: `1`
- **Description**: Another example macro, but this one deactivates triggers for all chains associated with the machine `DEVT-ST001`.

### 11. `{$STORAGECRAFT.COLLAPSE.VIRTUALBOOT}`
- **Value**: `0`
- **Description**: Defines the activation status of the VirtualBoot check on ImageManager. By default (value '0'), the VirtualBoot check is not activated.

### 12. `{$STORAGECRAFT.COLLAPSE.VIRTUALBOOT.CRIT}`
- **Value**: `40d`
- **Description**: Sets the maximum age threshold for the latest successful VirtualBoot on a Collapse. A critical alert will be generated if no successful VirtualBoot has taken place within the past 40 days.

### 13. `{$STORAGECRAFT.COLLAPSE.VIRTUALBOOT.INFO}`
- **Value**: `1h`
- **Description**: Specifies the time window for displaying info on a successful VirtualBoot. Information on any VirtualBoot conducted within the last hour will be displayed.

### 14. `{$STORAGECRAFT.COLLAPSE.WARN}`
- **Value**: `4d`
- **Description**: Sets the warning threshold for the age of the most recent successful Collapse. A warning alert will be triggered if no successful Collapse has been detected within the past 4 days.

### 15. `{$STORAGECRAFT.DEST_IS_NOT_HA}`
- **Value**: `0`
- **Description**: This macro determines the constant availability of the destination for both Backup and Collapse. If set to '1', some backups and collapse error log triggers will be ignored, presuming the destination is not always reachable.

---

Each of these macros plays a crucial role in fine-tuning the monitoring system for optimal performance and precision. By understanding and correctly setting each macro, administrators can ensure they're notified of relevant events in a timely manner.

## Conclusion

This StorageCraft Monitoring Template is a versatile tool for administrators to ensure the efficient monitoring of tasks related to backups, disk checks, and collapses. With its integration with Zabbix, it provides a consolidated platform for real-time insights and notifications, ensuring that critical issues are addressed promptly.

## Useful links
https://support.storagecraft.com/s/article/Windows-Event-Log-IDs-created-by-StorageCraft-products?language=en_US
