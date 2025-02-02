# APICallProxy

This Project is for Windows API Call Obfuscation to make static/Dynamic analysis of a program harder, and to make it harder to recognize and extract the sequance of Windows API the application Call.

To use it all what you need to do is Call **DeviceIoControl** with the appropriate **IOCTL** code insted of calling normal Windows API like **CreateFile**, **WriteFile**, **OpenProcess**,..

So if you want to Create File insted of calling **CreateFile()** API you call **DeviceIoControl()** with IOCTL Code **IOCTL_API_PROXY_CREATEFILE**

```
I Create sample Client that will do the following:
1 - APCInjection.exe : APC injection 
2 - DisableDSE.exe : Sample code to Disable Signing Policy(DSE), tested on windows 10 21H1 (it might crash on other windows version)
3-  RegisterLoadDriver.exe : Register and Load Driver using DeviceIoControl()
4-  WinsockServer.exe  :  WinSock Server same as Microsoft implementation (https://docs.microsoft.com/en-us/windows/win32/winsock/complete-server-code)
5-  WinsockClient.exe  :  WinSock Client same as Microsoft implementation (https://docs.microsoft.com/en-us/windows/win32/winsock/complete-client-code)
6-  ReverseShellClient.exe: Reverse Shell Client
7-  ReverseShellServer.exe: Reverse Shell Server (it can support command up to 99 character (can be increased from the code) for example: powershell.exe -encodedCommand "Base64 Script")

Note that the APCInjector.exe only work as x64 bit application on x64 bit windows because the shellcode is x64 bit

i tested the Driver and the client on windows 10 0x64 and window 8.1 x64/x86 bit

Note that the network operation only support the TCP connection for now, will add UDP connection soon.

The Communication Between the Driver and User-mode happens using METHOD_NEITHER i made it very easy to change the communication method (METHOD_BUFFERED,..), you only need to change a couple of lines in the source code and it will work normally
```


 
# Windows API:

- [x] **CreateFile**
- [x] **OpenFile**
- [x] **DeleteFile**
- [x] **WriteFile**
- [x] **ReadFile**
- [x] **OpenProcess**
- [x] **TerminateProcess**
- [x] **OpenThread**
- [x] **CloseHandle**
- [x] **GetFileSize**
- [x] **ZwQuerySystemInformation**
- [x] **ZwAllocateVirtualMemory**
- [x] **ZwFreeVirtualMemory**
- [x] **VirtualProtectEx**
- [x] **WriteProcessMemory**
- [x] **ReadProcessMemory**
- [x] **NtSuspendProcess**
- [x] **NtResumeProcess**
- [x] **ZwCreateSection**
- [x] **ZwOpenSection**
- [x] **ZwMapViewOfSection**
- [x] **ZwUnmapViewOfSection**
- [x] **SetThreadContext**
- [x] **GetThreadContext**
- [ ] **CreateThread**
- [ ] **CreateRemoteThread**
- [ ] **ResumeThread**
- [ ] **SuspendThread**
- [x] **RegCreateKey**
- [x] **RegDeleteKey**
- [x] **RegQueryValue**
- [x] **RegSetValue**
- [x] **ZwLoadDriver**
- [x] **ZwUnloadDriver**
- [x] **WSAStartup**
- [x] **WSACleanup**
- [x] **GetAddrInfo**
- [x] **FreeAddrInfo**
- [x] **Socket**
- [x] **CloseSocket**
- [x] **Connect**
- [x] **Listen**
- [x] **Bind**
- [x] **Accept**
- [x] **Send**
- [x] **Recv**

- [x] **Get_ProcessID_From_Process_Name**         not windows API but usefull utility (can use ZwQuerySystemInformation to do the same)


# Reference

https://github.com/hfiref0x/DSEFix 

https://github.com/wbenny/KSOCKET

# License:
MIT
