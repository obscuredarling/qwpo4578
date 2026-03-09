
This section outlines the system requirements, installation instructions for the RVBuilder extension in Visual Studio Code, and the extension configuration. 

## Requirements 
- **Operating System**: Windows or Linux
- **Software**: Visual Studio Code (version 1.82 or later) from [Microsoft Visual Studio Code](https://code.visualstudio.com/download)

## RVBuilder Installation
1. Download the RVBuilder extension package `rvbuilder-1.0.0.vsix` from the [RVBuilder lastest release page](https://github.com/andestech/RVBuilder/releases/tag/v1.0.0).  
2. In Visual Studio Code, click ![Extension](./images/extension.png) in the **Activity Bar**. 
3. In the **Extensions** view, click the **More Actions** icon ![dots](./images/dots.png) in the top-right corner, select "Install from VSIX…" from the drop-down menu, and then choose the downloaded file `rvbuilder-1.0.0.vsix` to start the installation. 
4. After the completion of installation, RVBuilder appears in the list of installed extensions in the **Extensions** view and the **RVBuilder** icon ![RVBuilder icon](./images/RVBuilder_icon.png) is displayed in the **Activity Bar**. These indicate that the installation was successful.

    ![RVBuilder install verification](./images/RVBuilder_install_verify.png)

---
 **Note**

  - To reinstall or update the RVBuilder extension, uninstall the existing extension before proceeding. After reinstallation, restart VS Code to apply the changes. 

     ![RVBuilder Uninstall](./images/RVBuilder_uninstall.png)


  - On Linux, a system password is required to grant RVBuilder permissions. After RVBuilder installation, follow the on-screen prompt to click **Run** and enter your system password.

    ![Notification for Linux installation](./images/notify_for_linux_install.png)
    ![Linux installation password](./images/linux_install_pw.png)

---

## Extension Configuration

Click ![Setting wheel](./images/setting_wheel.png) at the bottom of the **Activity Bar** and select **Settings**. Under the **User** tab, select **Extensions > RVBuilder** in the navigation pane to view the available RVBuilder extension settings and modify them if necessary. 


| Setting | Description |
|---------|-------------|
| Home Page| Controls whether the RVBuilder Home page is displayed when the VS Code starts. |
| Package Root | Specifies the installation destination of the RVBuilder package components.
| Project Workspace | Specifies the path to the project workspace.|

![RVBuilder Settings](./images/RVBuilder_settings.png)