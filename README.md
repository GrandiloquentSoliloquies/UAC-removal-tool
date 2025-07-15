# UAC-removal-tool
Unchecks the "Run this program as an administrator" checkbox of all .exe files found somewhere in same folder the script is executed from.
It does so by removing each exe's respective "Run as Administrator"-compatibility flag in the registry.

![Script Screenshot](https://i.imgur.com/RBruRQo.png)

---

## ➤ Features

-   **Automated Flag Removal**: Scans and removes the `RUNASADMIN` compatibility flag from registry entries associated with `.exe` files.
-   **Safe Reversion**: Automatically creates a `AdminFlag_Backup.json` file before making changes, allowing for a complete and safe restoration of the original settings.
-   **Two Scan Modes**:
    -   **Normal Scan**: A quick scan targeting only the root directory and its immediate subfolders.
    -   **In-depth Scan**: A comprehensive scan that recursively processes all subdirectories.
-   **Self-Elevation**: The script automatically checks for administrator privileges and will attempt to restart itself with elevated rights if necessary.
-   **User-Friendly Interface**: A simple command-line menu guides the user through the available options.
-   **Robust Error Handling**: Includes checks for missing backup files and provides clear error messages.

---

## ➤ Requirements

-   **Operating System**: Windows
-   **Execution Environment**: PowerShell
-   **Permissions**: The script requires administrator privileges to modify the necessary registry hives (`HKCU` and `HKLM`). It will attempt to self-elevate if not run as an administrator.

---

## ➤ How to Use

1.  **Download** the `Remove-AdminFlag.ps1` script.
2.  **Place** the script in the root directory you wish to scan. For example, if you want to scan executables inside `C:\Program Files\MyApplication`, place the script there.
3.  **Run** the script by right-clicking it and selecting "Run with PowerShell".

The script will first check for administrator rights. If it doesn't have them, it will attempt to re-launch itself. Once elevated, you will be presented with the main menu.

### Operation 1: Remove Admin Flags

This option scans for `.exe` files and removes the "Run as Administrator" flag.

1.  Choose **Option `1`** from the main menu.
2.  You will be prompted to select a scan type:
    -   Choose **Option `1`** for a **Normal Scan**.
    -   Choose **Option `2`** for an **In-depth Scan**.
3.  The script will begin scanning directories and modifying registry entries for any executables with the flag.
4.  Progress will be displayed. Once complete, if any changes were made, a backup file named `AdminFlag_Backup.json` will be created in the same directory as the script.

### Operation 2: Revert Changes from Backup

This option restores all changes from the `AdminFlag_Backup.json` file.

1.  Ensure the `AdminFlag_Backup.json` file is in the same directory as the script.
2.  Choose **Option `2`** from the main menu.
3.  The script will read the backup file and restore the original registry settings for each entry.
4.  Progress will be displayed until all entries are reverted.

---

## ➤ Scan Modes Explained

-   **Normal Scan (Faster)**: This mode is ideal for simple application structures where executables are located in the main folder or one level deep. It only scans the root folder (where the script is) and its direct subfolders.
-   **In-depth Scan (Slower)**: This is the recommended mode for complex applications or entire game directories with many nested folders. It recursively scans every single subdirectory, ensuring no executable is missed.

---

## ⚠️ Disclaimer

This script modifies the Windows Registry. While it includes a backup-and-restore functionality, irreversible issues can occur. Use this script at your own risk. The author is not responsible for any damage to your system. It is always recommended to create a system restore point before running tools that modify the registry.
