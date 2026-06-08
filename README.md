<h2>Ubuntu WSL Installation Guide</h2>
Objective:
Install Ubuntu on Windows 11 using WSL (Windows Subsystem for Linux).
Environment :
* Windows 11
* Ubuntu from Microsoft Store
* 16 GB RAM
Issue Encountered:
After installing Ubuntu from the Microsoft Store and launching it, the following error appeared:

" WslRegisterDistribution failed with error: 0x80370114 "

Investigation:
First, I checked whether virtualization was enabled.
Steps:
Open Task Manager
Go to Performance → CPU
Verify the Virtualization status

Result:
Virtualization: Enabled

Since virtualization was already enabled, I checked the WSL status.

Command:
wsl --status

Output:
WSL2 is unable to start since virtualization is not enabled on this machine.
Enable "Virtual Machine Platform" by running:
wsl.exe --install --no-distribution

Resolution

Opened PowerShell as Administrator and executed:

wsl --install --no-distribution

Output:

The requested operation is successful.
Changes will not be effective until the system is rebooted.
After running the command, I restarted the system.

Why This Worked

The Ubuntu application was already installed from the Microsoft Store.
However, the required WSL components were not fully enabled in Windows.
The command enabled the required WSL infrastructure without installing another Linux distribution.
Ubuntu Initialization
After restarting, Ubuntu launched successfully and prompted for UNIX user creation:

Enter new UNIX username:

After completing the setup, Ubuntu started successfully.

<h3>Result</h3>

Ubuntu WSL was installed successfully and is ready for Linux practice.

<h3> Key Learning</h3>

Seeing "Virtualization: Enabled" in Task Manager does not always mean all WSL requirements are enabled. Additional WSL components may still need to be configured in Windows.
