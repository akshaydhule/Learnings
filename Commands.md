# Unix commands

## GREP :
| command | description |
| --- | --- |
| grep -r 'pattern_to_match’ directory_to_search | Will output the file name and full line matching the pattern
|Options:||
|    -i | case insensitive|
|    -r, --recursive  like --directories=recurse | recursive search under directory |
|    -R, --dereference-recursive |  likewise, but follow all symlinks|
|      --include=FILE_PATTERN |  search only files that match FILE_PATTERN|
|      --exclude=FILE_PATTERN | skip files and directories matching FILE_PATTERN | 
|      --exclude-from=FILE   | skip files matching any file pattern from FILE |
|      --exclude-dir=PATTERN  | directories that match PATTERN will be skipped. |

## File commands
| command | description |
| --- | --- |
| `Cat log | egrep -I “starting"` |	While opening file, it will check for patterns and highlights them
| tail	| Output the last parts of files |
| touch 	| Creates new file |
| tee <file name> |	Read from standard input and write to standard output |
| Find -name “name"	| Search for file name |
| `find . -name "*String*" -print0 | xargs -0 rm -rf` | to find and delete all files matching name 'String' |
| sed -e 's/.*latency=\(.*\)ms.*/\1/' | to dump values between two strings, in this case 'latency=' and 'ms'|
  

## Device commands
### LSUSB

| command | description |
| --- | --- |
| lsusb | displaying information about USB buses in the system and the devices connected to them. |
|-s [[bus]:][devnum] |	Show only devices in specified bus and/or devnum. Both ID’s are given in decimal and may be omitted. |
|-d [vendor]:[product]|	Show only devices with the specified vendor and product ID. Both ID’s are given in hexadecimal. |
  
### Android debug commands
| command | description |
| --- | --- |
|adb devices | lists connected devices|
|adb root |restarts adbd with root permissions|
|adb start-server |starts the adb serve|
|adb kill-server |kills the adb server|
|adb reboot |reboots the device|
|adb devices -l |list of devices by product/model|
|adb shell |starts the backround terminal|
|exit |exits the background terminal|
|adb help |list all commands|
|adb -s <deviceName> <command> |redirect command to specific device|
|adb –d <command> |directs command to only attached USB device|
|adb –e <command> |directs command to only attached emulator|
| adb remount | put /system partition in writable mode.|
| adb disable-verity| disable dm-verity protection which lives in the kernel. Disabling dm-verity will retain kernel modifications by bypassing this protection. |

## Brazil commands
| command | description |
| --- | --- |
| Brazil workspace —create —name <name>	| Creates workspace|
| Brazil workspace —use —package <package name>	| git clones the package into local repo |
| Brazil-build |	Builds the target repository |

## Yocto/Bitbake commands
| command | description |
| --- | --- |
| bitbake [PACKAGE NAME] -c do_cleanall  | cleans entire build for this package |
| bitbake -ccleansstate [PACKAGE NAME] | (same as above} |
| bitbake [DEVICE TYPE IMAGE] | builds the whole image for particular device type |
| bitbake -g -u taskexp <recipe-or-image-name> | Show dependency information in a graphical interface|
| bitbake -c <task> <recipe> | runs specific task + its dependent task (earlier tasks) |
| bitbake -C <task> <recipe> | runs specific task + tasks depending on it (remaining tasks)|
| Other used options: ||
| -k/--continue |                                          # continue as much as possible |
| -e              |                                       # show environment, good to debug recipe|
| -m/--kill-server |                                      # Terminate any running bitbake server.|
| -u               |                                     # ui (knotty, tasexp, ncurses, teamcity)|
| -b               |                                     # Specified recipe alone built ( assumes depenedent packages are met)|
  
## Systemd commands
| command | description |
| --- | --- |
| systemctl start test.service | start a service |
|systemctl stop test.service | stop the service |
|systemctl restart test.service | restart the service |
|systemctl reload test.service  | reload the service without interrupting normal functionality |
|systemctl list-unit-files | including those that systemd has not tried to load into memory|
| systemctl list-unit-files --type=target | target, service etc |
| systemctl list-dependencies test.service | list dependencies |
| systemctl list-dependencies --all test.service | list dependencies # `--reverse` : reverse dependencies (units that depend on the specified unit) |
|systemctl enable nginx.service | enable a service to start automatically at boot |
