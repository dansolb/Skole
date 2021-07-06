# Regedit Cheatsheet
Cheatsheet for hvor man finner div ting i reg edit.
## Ekstra lokasjoner etc
https://www.dfir.training/ultimate-registry-forensics-cheat-sheet

https://static1.squarespace.com/static/552092d5e4b0661088167e5c/t/5a00963153450a8779b23489/1509987890282/Windows

https://www.jaiminton.com/cheatsheet/DFIR/#

## System info

Maskinnavn:
* HKLM\SYSTEM\ControlSet001\Control\ComputerName\ComputerName

Shutdown:
* HKLM\SYSTEM\CurrentControlSet\Control\Windows
* HKLM\SYSTEM\ControlSet001\Control\Windows

Timezone:
* SYSTEM\ControlSet001\Control\TimeZoneInformation

Nettverksinfo :
* HKLM\SYSTEM\CurrentControlSet\Services\

Installert programvare:
* HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths
* HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

## Restore point/Shadow Copy

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\BackupRestore

Within this path, we’ve got three subkeys:
* FilesNotToBackup — specifies files that should not be backed up or restored.
* FilesNotToSnapshot (only Vista/2008+)— Specify files that should be deleted from newly-created shadow copies
* KeysNotToRestore — Provides the names of registry keys and values that backup applications should not restore

## Recycle Bin
Når en fil blir flyttet til søppeldunken vil MFT entry bli slettet for filen så vil en ny MFT entry.
* [original drive letter][index number].[original file extension]
### The INFO2 file contains:
* The files original filename and path (entered twice, once in ASCII and again in Unicode)
* The date and time of deletion
* The index number
* The physical size of the file

## Autodest Jump List
C:\Users\%USERNAME%\Recent\AppData\Roaming\Microsoft\Windows\Recent\ AutomaticDestinations

## Custdest Jump Lists
C:\Users\%USERNAME%\Recent\AppData\Roaming\Microsoft\Windows\Recent\ CustomDestinations

## Windows Index service

* C:\ProgramData\Microsoft\Search\Data\Applications\Windows\Windows.edb
## Cortana Database
Cortana Databases (EDBs):
* \Users\%USERNAME%\AppData\Local\Packages\Microsoft.Windows.Cortana_xxxx\AppData\Indexed DB\IndexedDB.edb
## Thumbs.db

* Header = D0 CF 11 E0 A1 B1 1A E1 00

C:\Users\userid\AppData\Local\Microsoft\Windows\Explorer
\Users\%username%\AppData\Local\Microsoft\Windows\Explorer.
* thumbcache_32.db
* thumbcache_96.db
* thumbcache_256.db
* thumbcache_1024.db

## LNK Filer
.LNK er filer som blir autogenerert når en bruker åpner en fil, disse kan inneholde informasjon om sletta filer.

## Partition volum Serie nummer
* FAT32: Offset 67 from the start of the partition
* NTFS: Offset 72 from the start of the partition

## Prefetch
Windows keeps tracks of programs used during the session and saves it to a prefetch file located in the Windows\prefetch directory. 
It allows the loading of regularly used programs faster.
When an application is launched a prefetch file for that application is created.
* Windows\prefetch

## Logs
* System Log - information that relates to system operation and maintenance. 
starting and stopping of services or the installation of drivers. 
* Application Log - applications that use Windows APIs can note significant events to that application. 
anti-virus programs will utilise this.
* Security Log - records events including logons, file access, authentication, account creation, privilege use. 
This log would tell you who was logged on at a particular time and whether people had attempted to access an account unsuccessfully.
* %System32%\winevt\Logs

Dump eventlog via Powershell: PsLogList

## Windows Store
Programmer installert via Windows Store
* Installerte programmer: HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Appx\AppxAllUserStore\Applications\
* Slettede programmer: HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Appx\AppxAllUserStore\Deleted\

## User Assist
ROT-13 encoding of data used to populate the User Assist Area of the start button
Contains most recently used programs
* HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Exlorer\UserAssist\{*********}\Count


