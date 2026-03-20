This section describes how to build an RVBuilder project in VS Code. It covers the available build methods, where the build output is displayed, and where the generated artifacts are located for single-core and multi-core Andes RISC-V targets.

## Build Methods 
With the project selected in the **Explorer** view, use either of the following ways to initiate the build process of an RVBuilder project.

 - On the project's **Settings** page, click "Build" in the upper-right corner. 
    ![project build 1](./images/build_from_project_setting.png)

 - On the project's drop-down menu, click "RVBuilder: Build Project".
    ![project build 2](./images/build_from_project_drop_down.png)

 - On the **Explorer** view title menu, click ![Build icon](./images/build_icon.png) (RVBuilder: Build Project).  
    ![project build 3](./images/build_from_title_menu.png)

 - In the command palette (opened using the keyboard F1 or Ctrl+Shift+P), run the "RVBuilder: Build Project" command.  
    ![project build 4](./images/build_from_command_palette.png)

 ---
 **Note**

If you use a self-defined `tasks.json` for an RVBuilder project, start the build process using the “Tasks: Run Task” command from the command palette. This invokes VS Code’s native task runner to execute the build task defined in `tasks.json`.

---

## Build Output 
The build process and result are displayed in the **Terminal** view. 

 ![build output](./images/build_output_from_terminal.png)


## Build Artifacts 
The build artifacts are generated in the following locations:

- **Program executable** (`.adx`) and **object files**: `${PROJECT}/[Debug|Release]` 
- **Binutils outputs** (e.g. `.bin`): `${PROJECT}/[Debug|Release]/output`. 


 ![build artifact location](./images/build_artifact_location.png)