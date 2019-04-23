# VM Ware Workstaion CLI `vmrun`

This document summarizes the information given when unrecognized input is passed to `vrmun` and gives an overview of the available commands and parameters.

## vmrun version 1.17.0 build-12990004

**Usage:** `vmrun [AUTHENTICATION-FLAGS] COMMAND [PARAMETERS]`

### AUTHENTICATION-FLAGS

These must appear before the command and any command parameters.

``` shell
   -T <hostType> (ws|fusion| | player)
   -vp <password for encrypted virtual machine>
   -gu <userName in guest OS>
   -gp <password in guest OS>
```

### Power Commands

| POWER COMMANDS | PARAMETERS | DESCRIPTIONs |
| --: | --- | --- |
| start | Path to vmx file, `gui` or `nogui` | Start a VM or Team |
| stop  | Path to vmx file, `hard` or `soft` | Stop a VM or Team |
| reset  | Path to vmx file, `hard` or `soft` | Reset a VM or Team |
|suspend | Path to vmx file, `hard` or `soft` | Suspend a VM or Team |
| pause  | Path to vmx file, | Pause a VM |
|unpause | Path to vmx file, | Unpause a VM |

### Snapshot Commands

| SNAPSHOT COMMANDS | PARAMETERS | DESCRIPTION |
| --: | --- | --- |
| listSnapshots | Path to vmx file `showTree` | List all snapshots in a VM |
| snapshot | Path to vmx file, `Snapshot name` | Create a snapshot of a VM |
| deleteSnapshot | Path to vmx file, `Snapshot name`, `andDeleteChildren` | Remove a snapshot from a VM |
| revertToSnapshot | Path to vmx file, `Snapshot name` | Set VM state to a snapshot |

### Guest OS Commands

| GUEST OS COMMANDS | PARAMETERS | DESCRIPTION |
| --: | --- | --- |
| runProgramInGuest | Path to vmx file, `-noWait`, `-activeWindow`, `-interactive`, `Complete-Path-To-Program`, `Program arguments` | Run a program in Guest OS |
| fileExistsInGuest | Path to vmx file, Path to file in guest | Check if a file exists in Guest OS |
| directoryExistsInGuest | Path to vmx file, Path to directory in guest | Check if a directory exists in Guest OS |
| setSharedFolderState | Path to vmx file, `Share name`, `Host path`, `writable | readonly` | Modify a Host-Guest shared folder |
| addSharedFolder | Path to vmx file, `Share name`, `New host path` | Add a Host-Guest shared folder |
| removeSharedFolder | Path to vmx file, `Share Name` | Remove a Host-Guest shared folder |
| enableSharedFolders| Path to vmx file, `runtime` | Enable shared folders in Guest|
| disableSharedFolders | Path to vmx file,`runtime` | Disable shared folders in Guest|
| listProcessesInGuest | Path to vmx file | List running processes in Guest OS |
| killProcessInGuest | Path to vmx file, `process id` | Kill a process in Guest OS |
| runScriptInGuest | Path to vmx file, `-noWait`, `-activeWindow`, `-interactive`, `Interpreter path`, `Script text` | Run a script in Guest OS |
| deleteFileInGuest | Path to vmx file, Path in guest | Delete a file in Guest OS |
| createDirectoryInGuest | Path to vmx file,Directory path in guest | Create a directory in Guest OS |
| deleteDirectoryInGuest | Path to vmx file,Directory path in guest | Delete a directory in Guest OS |
| CreateTempfileInGuest | Path to vmx file | Create a temporary file in Guest OS |
| listDirectoryInGuest | Path to vmx file,Directory path in guest | List a directory in Guest OS |
| CopyFileFromHostToGuest | Path to vmx file, Path on host, Path in guest, Path on host, Path in guest | Copy a file from host OS to guest OS |
| CopyFileFromGuestToHost | Path to vmx file, Path in guest, Path on host | Copy a file from guest OS to host OS |
| renameFileInGuest | Path to vmx file, Original name, New name | Rename a file in Guest OS |
| typeKeystrokesInGuest | Path to vmx file, keystroke string | Type Keystrokes in Guest OS |
| connectNamedDevice | Path to vmx file, device name | Connect the named device in the Guest OS |
| disconnectNamedDevice | Path to vmx file, device name | Disconnect the named device in the Guest OS |
| captureScreen | Path to vmx file, Path on host | Capture the screen of the VM to a local file |
| writeVariable | Path to vmx file, `runtimeConfig| guestEnv| guestVar`, variable name, variable value | Write a variable in the VM state |
| readVariable | Path to vmx file,`runtimeConfig| guestEnv| guestVar`, variable name | Read a variable in the VM state |
| getGuestIPAddress | Path to vmx file, `-wait` | Gets the IP address of the guest |

### General Commands

| GENERAL COMMANDS | PARAMETERS | DESCRIPTION |
| --: | --- | --- |
| list | | List all running VMs |
| upgradevm | Path to vmx file | Upgrade VM file format, virtual hw |
| installTools | Path to vmx file | Install Tools in Guest |
| checkToolsState | Path to vmx file |Check the current Tools state |
| deleteVM | Path to vmx file | Delete a VM |
| clone | Path to vmx file, `Path to destination vmx file`, `full` or `linked`, `-snapshot=Snapshot Name`, `-cloneName=Name` | Create a copy of the VM |

### Template VM Commands

| Template VM COMMANDS | PARAMETERS | DESCRIPTION |
| --: | --- | --- |
| downloadPhotonVM | Path for new VM | Download Photon VM |

### Examples

Starting a virtual machine with Workstation on a Windows host

    vmrun -T ws start "c:\my VMs\myVM.vmx"

Running a program in a virtual machine with Workstation on a Windows host with Windows guest:

    vmrun -T ws -gu guestUser -gp guestPassword runProgramInGuest "c:\my VMs\myVM.vmx" "c:\Program Files\myProgram.exe" ```

Creating a snapshot of a virtual machine with Workstation on a Windows host

    vmrun -T ws snapshot "c:\my VMs\myVM.vmx" mySnapshot

Reverting to a snapshot with Workstation on a Windows host

    vmrun -T ws revertToSnapshot "c:\my VMs\myVM.vmx" mySnapshot

Deleting a snapshot with Workstation on a Windows host

    vmrun -T ws deleteSnapshot "c:\my VMs\myVM.vmx" mySnapshot

Enabling Shared Folders with Workstation on a Windows host

    vmrun -T ws enableSharedFolders "c:\my VMs\myVM.vmx"
    
