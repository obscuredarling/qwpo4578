This section outlines the physical network setups and target connection types supported by RVBuilder.

## Physical Network 
The target systems supported by RVBuilder in VS Code include the AndeShape™ AE350 or Corvette-F1 platform integrated with an AndesCore™ single-core or symmetric multiprocessing (SMP) RISC-V processor. These targets can be either a simulator target or an In-Circuit Emulator (ICE) target, connected through a local or remote Ethernet network using the TCP/IP protocol. 

- Simulator Target: A Virtual Evaluation Platform (VEP) connected to a debugging host through an SoC simulator specified by a configuration file.

- ICE Target: A Real Evaluation Platform (REP), such as an AndeShape development platform, connected to a debugging host through an ICE debugger.


To set up the physical network between RVBuilder and either type of target, see the figure below.

![Physical Target Network](./images/target_network.png){ width="75%" height="60%"}

## Target Connection
After setting up the physical network, you can build the target connection for program development. RVBuilder supports the following four connection types, each corresponding to a specific target environment. You can select one of these connection types in the RVBuilder's **Project Settings** interface to establish the target connection for a project. See [**Target Configuration**](./project_config.md#target-configuration) for a project. 

### Andes QEMU (Local Simulator Target)
This connection type connects to a virtual evaluation platform through the Andes QEMU emulator, a QEMU system emulator designed to simulate Andes RISC-V target architectures. 

Andes QEMU targets prioritize speed and flexibility over accuracy. Therefore, they are well-suited for early-stage software development and rapid design verification, where cycle or timing precision and detailed hardware modeling are not required.

Note that Andes QEMU does not fully simulate all peripheral functions of Andes target architectures. For a detailed list of its supported peripherals and available configuration options for the emulator, see [**Andes QEMU Emulator Reference Manual**](./ref/Andes_QEMU_Emulator_Reference_Manual_UM284_V1.2.pdf). 

### AICE (Local ICE Target Connection)
This connection type connects to a real evaluation platform through an Andes ICE box. You can use the Andes ICE Management Software, ICEman, to control the ICE debugger during program execution. For a complete list of ICEman options and their usage, see [**Andes ICE Management Software (ICEman) User Manual**](./ref/Andes_ICE_Management_Software_UM067_V4.1.pdf).    


### Maverick (Local ICE Target Connection)
This connection type connects to a real evaluation platform through a SEGGER J-Link using a custom implementation.

Note that full compatibility with all SEGGER J-Link versions and features is not guaranteed in RVBuilder, as support may vary depending on the firmware version and updates.

### GDB Server (Remote ICE/Simulator Target Connection)

This connection type connects to an Andes QEMU, ICE, or Maverick target running on a remote host. It requires the hostname or IP address of the remote host as well as the port number used by GDB to establish the connection.    