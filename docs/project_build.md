This section describes how to build an RVBuilder project in VS Code. It covers the available build methods, where the build output is displayed, and where the generated artifacts are located for single-core and multi-core Andes RISC-V targets.

## Build Methods 
With the project selected in the **Explorer** view, use either of the following ways to initiate the build process of an RVBuilder project.

 - On the project's **Settings** page, click "Build" in the upper-right corner. 
    ![project build 1](./images/build_from_project_setting.png)

 - On the project's drop-down menu, click "RVBuilder: Build Project".
    ![project build 2](./images/build_from_project_drop_down.png)

 - On the **Explorer** view title menu, click ![Build icon](./images/build_icon.png) (RVBuilder: Build Project).  
    ![project build 3](./images/build_from_title_menu.png)

 - In the Command Palette (opened using the keyboard F1 or Ctrl+Shift+P), use the  "RVBuilder: Build Project" command.  
    ![project build 4](./images/build_from_command_palette.png)

 **Note**

   If you use a self-defined `tasks.json` for an RVBuilder project, start the build process using the “Tasks: Run Task” command from the Command Palette. This invokes VS Code’s native task runner to execute the build task defined in `tasks.json`.
    
## Build Output 
The build process and result are displayed in the **Terminal** view. 

```txt
Executing task in folder Debug: make all 

Building file: ../src/Test.c
Invoking: Andes C Compiler
riscv32-elf-gcc -mcpu=a25 -Og -mcmodel=medium -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/Test.d" -MT"src/Test.d src/Test.o" -o "src/Test.o" "../src/Test.c" 
Finished building: ../src/Test.c
 
Building target: Test.adx
Invoking: Andes C Linker
riscv32-elf-gcc -mcpu=a25 -Og -static -mcmodel=medium -mvh -T"../.settings/Debug/.loadedaddr/nds.ld" -o "Test.adx" src/Test.o  
Finished building target: Test.adx
 
Invoking: NM (symbol listing)
riscv32-elf-nm -n -l -C "Test.adx" > output/symbol.txt
Finished building: output/symbol.txt
 
Invoking: Readelf (ELF info listing)
riscv32-elf-readelf -a "Test.adx" > output/readelf.txt
Finished building: output/readelf.txt
 
Invoking: Objdump (disassembly)
riscv32-elf-objdump -x -d -C "Test.adx" > output/objdump.txt
Finished building: output/objdump.txt
 
Invoking: Objcopy (object content copy)
riscv32-elf-objcopy -S -O binary "Test.adx" output/Test.bin
Finished building: output/Test.bin
 
Invoking: Size (section size listing)
riscv32-elf-size  "Test.adx" | tee output/.PHONY.size
   text    code  rodata    data     bss     dec     hex filename
  11256   11228      28    1364     976   13596    351c Test.adx
Finished building: output/.PHONY.size
```

## Build Artifacts 
For RVbuilder projects targeting a single-core Andes RISC-V target, the program executable (`.adx`) and object file are generated in `$PROJECT\[Debug|Release]` and the binutil output (e.g., `.bin`) in `$PROJECT\[Debug|Release]\output`. 

For projects targeting a multi-core Andes RISC-V target, the program executable (`.adx`) and object file are generated in `$PROJECT\$CORE\[Debug|Release]-$CORE` and the binutil output (e.g., `.bin`) is in `$PROJECT\$CORE\[Debug|Release]-$CORE/output`. 

The following shows build artifact locations for a Test project to be run on a single-core Andes RISC-V target. 
 ![project build 4](./images/build_artifact_location.png)