This section introduces the configuration of the RVBuilder extension in VS Code and the RVBuilder-specific interface and settings designed to facilitate software development with Andes RISC-V processors.

## Extension Configuration

Click ![Setting wheel](./images/setting_wheel.png) at the bottom of the **Activity Bar** and select **Settings**. Under the **User** tab, select **Extensions > RVBuilder** in the navigation pane to view the available RVBuilder extension settings and modify them if necessary. 


| Setting | Description |
|---------|-------------|
| Home Page| Controls whether the RVBuilder Home page is displayed when the VS Code starts. |
| Package Root | Specifies the installation destination of the RVBuilder package components.
| Project Workspace | Specifies the path to the project workspace.|

![RVBuilder Settings](./images/RVBuilder_settings.png)

## RVBuilder-Specific Interface 

### 1. RVBuilder Icon on the Activity Bar

   The RVBuilder icon serves as the entry point to the RVBuilder view.

### 2. RVBuilder View

   This view provides access to the RVBuilder Home page.

### 3. RVBuilder Home Page

   The RVBuilder Home page provides quick access to creating a new RVBuilder project or importing an RVBuilder demo project. It also includes links to reference documentation, technical support resources, and Andes Technology social media channels for developers who want to learn more.

   ![RVBuilder Entry Interface](./images/Interface_entry.png)

### 4. RVBuilder Project Action Items 

   RVBuilder enables a set of project-related operations through an RVBuilder project pull-down menu or the **Explorer** view toolbar to streamline the development workflow. 

   ![RVBuilder Porject Menu Items](./images/RVBuilder_project_pulldown_menu.png)

   ![RVBuilder Toolbar Items](./images/RVBuilder_toolbar.png)

   | Menu Item | Description |
   |---------|-------------|
   | RVBuilder: Build Project| Compiles the current project and generates the target binary/executable. |
   | RVBuilder: Clean Project | Removes all build artifacts generated during previous builds. |
   | RVBuilder: Delete Project | Deletes the RVBuilder project, including the configuration and source files. |
   | RVBuilder: Rebuild Project | Performs a clean operation followed by a full rebuild. |
   | RVBuilder: Debug | Launches a debug session for the RVBuilder project using the configured settings. |
   | RVBuilder: Settings | Opens the RVBuilder project settings for configuration and modification. |
   | RVBuilder: Flash Burner | Programs the generated project binary to the flash memory of a specified target.  |

## RVBuilder Settings in Workspace Configuration Files 
A RVBuilder project, or an existing project applied with RVBuilder settings, includes preconfigured workspace settings required for development with Andes RISC-V targets. These settings are written to VS Code workspace configuration files in the `.vscode` folder under the project root directory. Among the files, pay attention to the following: 

### `tasks.json`: Toolchain Executable Path
For a RVBuilder project uses a custom Makefile (i.e., with an unchecked "Auto-Generate Makefile" option in its settings. See [**Auto Generate Makefile**](./project_config.md#auto-generate-makefile)), changing the project toolchain requires you to update the toolchain executable paths specified in this task configuration file. Otherwise, it may result in build errors. 

Note that a toolchain change is typically triggered by a change in the selected chip profile. For more about toolchains in the RVBuilder package and their paths, see [**Toolchains**](./components.md#toolchains)

![Toolchain Path](./images/toolchain_path_in_tasks_file.png)


### `launch.json`: Memory Map Setting  
Most target and program settings in this debug configuration file are configured automatically for RVBuilder projects. By default, 
- the launch type is set to `rvbuilder-debug`.
- the connection type and program specification are aligned with the project's target configuration and build settings. 
- the `loadMemoryMap` setting is set to `true`, indicating the program executable is loaded according to the memory regions defined in the selected chip profile. If you want to load the program executable without applying the predefined memory mapping, set this setting to `false`.

  ![Load Memory Map](./images/mem_map_in_launch.png)