# Windows 10 Setup Tips

## Table of Contents

## Tips

### Git for Windows
  - Configure Windows for 'Developer Mode'
  - Install Git for Windows
    - Use the defalts for everything, except:
      - Ensure '__Git__' LFS is selected
      - Select '__Use the native Windows Secure Channel Library__'
      - Select '__Enable symbolic links__'
  - Choice of Git Directories (Outside of OneDrive's default pervue)
    - `C:\data\git`
    - `C:\Users\%USERNAME%\git`
  - Custom User Bin Location (For things like Vagrant, Pakcer, etc...)
    - `C:\data\${app}\bin`
    - `C:\Users\%USERNAME%\apps\bin`

### Atom Editor
  - Fix the Windows natvie compilers:  
    `apm install --check`
  - Install my favorite packages:  
    ``` cmd
    apm install ^
      linter
      linter-jsonlint
    ```

### Windows make
  - Install [NMAKE](https://msdn.microsoft.com/en-us/library/dd9y37ha.aspx)
  as part of the '__Microsoft Visual C++ Build Tools__' package
  - It will use the `Makefile` in the current directory unless otherwise
  specified using the `/F filename` option
  - In my builds I will have targets `win-{blah}` so that I can maintain
  cross-compatiility of the make file between \*nix and win-cmd

### Vagrant\\Hyper-V
  - Enable Hyper-V from '__Turn Windows features on or off__'
  - Download and install Vagrant

### Hyper-V with Hybernate on Surface
  Important: Before you enable Hyper-V you MUST ensure hibernation is turned on

  1. Ensure Hiberfile is supported  
    `powercfg /H on /TYPE full`
  2. Validate that this worked:  
    `powercfg /a`
    Example Output:
    ```
    The following sleep states are available on this system:
        Standby (S0 Low Power Idle) Network Disconnected
        Hibernate
        Fast Startup
    ```
  3. You can now enable Hyper-V from the '__Turn Windows features on or off__' dialog
  4. It's Windows: Of course you reboot now :)
  5. Optional... But sometimes required: Set '__Hyper-V Virtual Machine Management__' to '__Manual__'
