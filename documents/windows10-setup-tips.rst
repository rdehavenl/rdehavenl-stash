====
Windows 10 Setup Tips
====

====
Tips
====

Git for Windows
----
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


Atom Editor
----
  - Fix the Windows natvie compilers:  

    `apm install --check`

  - Install my favorite packages:  
  
    ``` cmd
    apm install ^
      linter
      linter-jsonlint
    ```

Windows make
----
  Note: I'm pretty sure this is pointless, and there will be no using the same
  makefile
  
  - Install [NMAKE](https://msdn.microsoft.com/en-us/library/dd9y37ha.aspx)
  as part of the '__Microsoft Visual C++ Build Tools__' package
  - If you don't need any MS SDK's then pick '__Custom__' and de-select any SDK's
  - It will use the `Makefile` in the current directory unless otherwise
  specified using the `/F filename` option
  - In my builds I will have targets `win-{blah}` so that I can maintain
  cross-compatiility of the make file between \*nix and win-cmd

Vagrant\\Hyper-V
----
  - Enable Hyper-V from '__Turn Windows features on or off__'
  - Download and install Vagrant

Hyper-V with Hibernate on Surface and other battery saving tips
----
    Important: Before you enable Hyper-V you MUST ensure hibernation is turned on

  1. Enable Hibernate that can support Hyper-V
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
  2. Laptop Power Saving (Settings>>System>>Power and Sleep)
      1. Screen Turn-off Timeout
          - On Battery: 1 min
          - On Power: 5 min
      2. Sleep after
          - On Battery: 4 min
          - On Power: 10 min
      3. Network Connection (Sleep and Battery, Disconnect)
          - Always
      4. Additional Power Settings -> Change Plan Settings -> Change Advanced Power Settings
          - Sleep -> Hibernate After
            - On Battery: 15 mins
            - On Power: Never
