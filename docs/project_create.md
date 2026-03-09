## Start a New RVBuilder Project 

1. In Visual Studio Code, click ![RVBuilder icon](./images/RVBuilder_icon.png) to open the RVBuilder view and click **Home**. 
2. On the RVBuilder **Home** page, click **New Project**. 
3. On the **New Project** dialog, enter a project name, specify a programming language (C or C++), a desired Andes RISC-V target and a project type, and then click **Browse** to specify a project workspace location.

    !!! note
        Andes RISC-V targets are defined by chip profiles. For more about chip profiles in the RVBuilder package, see [**Chip Profiles**](./using_rvbuilder.md#chip-profiles).

4. Click **Create** to complete the project creation.
 
![RVBuilder project creation](./images/project_create.png)

## Add RVBuilder settings to an Existing Project 

For an existing non-RVBuilder project, RVBuilder settings can be added to enable RVBuilder features and streamline development on targets embedded with Andes RISC-V processors. Proceed as follows:

1. Add an existing project folder to the current workspace. 

2. In the **Explorer** view, select the interested project folder. Next, click any [RVBuilder project action item](./using_rvbuilder.md#4-rvbuilder-project-action-items) from either the project context menu or the **Explorer** view title menu.

    For example, select an existing "hello" project and click **RVBuilder: Settings** on the **Explore** view title menu.
    ![Add RVBuilder Settings](./images/add_rvbuilder_setting.png)

3. A notification dialog appears indicating that the selected project is not yet configured for RVBuilder development. Click **Yes** to add the required RVBuilder settings to the project.
    
    ![RVBuilder Settings Notification](./images/add_rvbuilder_setting_notify.png)


4. The project is now configured as an RVBuilder project. RVBuilder features such as build, debug, and flash operations dedicated for development with Andes RISC-V targets are enabled, and the project is ready for development using the RVBuilder workflow.
