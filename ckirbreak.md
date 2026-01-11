# Ckirbreak Guide
To ckirbreak (jailbreaking CKIR), you must disable the monitoring processes and services of CKIR's MOMI and MaestroWeb systems. This allows you to run software that would otherwise be blocked or restricted by these monitoring tools.

## Methods

### Method 1

1. Open `resmon.exe`
    1. Right click on target process
    2. Suspend Process
2. Open `resources.msc` 
    1. Right click on the target service
    2. Properties
        1. Startup type: Disabled
        2. Service status > Stop/Pause

### Method 2

```powershell
# Process Name
Add-Type 'using System;using System.Runtime.InteropServices;
public class N{
[DllImport("ntdll.dll")]public static extern int NtSuspendProcess(IntPtr h);
[DllImport("kernel32.dll")]public static extern IntPtr OpenProcess(uint a,bool b,int c);
}';
[N]::NtSuspendProcess([N]::OpenProcess(2097151,0,(gps $pname).Id))

# PID
Add-Type 'using System;using System.Runtime.InteropServices;
public class N{
[DllImport("ntdll.dll")]public static extern int NtSuspendProcess(IntPtr h);
[DllImport("kernel32.dll")]public static extern IntPtr OpenProcess(uint a,bool b,int c);
}';
[N]::NtSuspendProcess([N]::OpenProcess(2097151,0,$pid))
```

### Method 3

- [SGB Unlimiter](https://github.com/ParkSnoopy/sgb_unlimiter/releases/download/v1.2.1/windows.zip)
    - [Visual C++ Redistributable v14 (x64)](https://aka.ms/vc14/vc_redist.x64.exe)

## Target Processes

### MaestroWeb

1. `MaestroWebSvr.exe`
2. `MaestroWebAgent.exe`

### momi

1. `lqndauccd.exe`
    1. `nfowjxyfd.exe`
    2. `nhfneczzm.exe`
    3. `qukapttp.exe`
2. `rwtyijsa.exe`

## Target Services

### MaestroWeb

1. MaestroWeb Remote Control
2. MaestroWebSvr

### momi

1. MayaDSesSVC
2. MayaSVCEC