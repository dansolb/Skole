The shadow copy service is enabled by default on Vista and Windows 7, but not on Windows 2008 or 2008 R2.

* Shadow copies provide a “snapshot” of a volume at a particular time.
* Shadow copies can show how files have been altered.
* Shadow copies can retain data that has later been deleted, wiped, or encrypted.
* vssadmin list shadows /for=[volume]:

Eksempel for hvordan man henter ut en Shadowcopy:

VSS Tool: http://www.dmares.com/pub/nt_32/vss.exe

Søker opp shadowcopies for en disk: 

```CMD
vssadmin list shadows /for=C:
```
Lager en shadowcopy gjennom en symbolic link:
```CMD
Mklink /d C:\{test-shadow} \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy3\
```

Man kan mounte Shadows rett til nettverks share:

```CMD
net share testshadow=\\.\HarddiskVolumeShadowCopy11\
```