This section introduces the configuration of the RVBuilder extension in VS Code and the RVBuilder-specific interface and settings designed to facilitate software development with Andes RISC-V processors.

## RVBuilder Configuration

Click ![Setting wheel](./images/setting_wheel.png) at the bottom of the **Activity Bar** and select **Settings**. Under the **User** tab, select **Extensions > RVBuilder** in the navigation pane to view the available RVBuilder extension settings and modify them if necessary. 


| Setting | Description |
|---------|-------------|
| Home Page| Controls whether the RVBuilder Home page is displayed when the VS Code starts. |
| Package Root | Specifies the installation destination of the RVBuilder package components.
| Project Workspace | Specifies the path to the project workspace.|

![RVBuilder Settings](./images/RVBuilder_settings.png)

## RVBuilder-Specific Interface 

1. RVBuilder Icon on the Activity Bar

   The RVBuilder icon serves as the entry point to the RVBuilder view.

2. RVBuilder View

   This view provides access to the RVBuilder Home page.

3. RVBuilder Home Page

   The RVBuilder Home page provides quick access to creating a new RVBuilder project or importing an RVBuilder demo project. It also includes links to reference documentation, technical support resources, and Andes Technology social media channels for developers who want to learn more.

   ![RVBuilder Entry Interface](./images/Interface_entry.png)

4. RVBuilder Project Actions Items 

   RVBuilder enables a set of project-related operations through an RVBuilder project pull-down menu or the Explorer view toolbar to streamline the development workflow. 

   | Menu Item | Description |
   |---------|-------------|
   | RVBuilder: Build Project| Compiles the current project and generates the target binary/executable. |
   | RVBuilder: Clean Project | Removes all build artifacts generated during previous builds. |
   | RVBuilder: Delete Project | Deletes the RVBuilder project, including the configuration and source files. |
   | RVBuilder: Rebuild Project | Performs a clean operation followed by a full rebuild. |
   | RVBuilder: Debug | Launches a debug session for the RVBuilder project using the configured settings. |
   | RVBuilder: Settings | Opens the RVBuilder project settings for configuration and modification. |
   | RVBuilder: Flash Burner | Programs the generated project binary to the flash memory of a specified target.  |

   ![RVBuilder Porject Menu Items](./images/RVBuilder_project_pulldown_menu.png)

   ![RVBuilder Toolbar Items](./images/RVBuilder_toolbar.png)


