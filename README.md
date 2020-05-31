# Simulator command line cheatsheet

simctl is a "Command line utility to control the Simulator". Bellow are some useful commands


## Showing help

```
xcrun simctl help
```

## List all available simulators

```
xcrun simctl list
```

## Create simulator

### Create a new one
```
xcrun simctl create <name> <device type id> <runtime id>

# eg:
xcrun simctl create My-iphone11 com.apple.CoreSimulator.SimDeviceType.iPhone-11 com.apple.CoreSimulator.SimRuntime.iOS-13-3 
```

### Clone from other simulator
```
xcrun simctl clone <device> <new name>

# eg:
xcrun simctl clone D9C49E13-0FBE-49FE-8C68-426DE48B7B3B My-iphone11-2
```

## Boot a device
```
xcrun simctl boot <device>

# eg:
xcrun simctl boot My-iphone11
```
<device> can be device name or device id (as listed in the above listing command `xcrun simctl list`)


## Open url

```
xcrun simctl openurl <device> <URL>
# eg:
xcrun simctl openurl My-iphone11 "https://google.com"

# eg2:
xcrun simctl openurl booted "https://google.com"
```
`booted` can be used to open url on currently running simulator without specify device id or device name


## Add media
```
xcrun simctl addmedia <device> <path>
eg:
xcrun simctl addmedia booted ~/Desktop/cat.png
```

## Installing
### Install an app
```
xcrun simctl install <device> <path>

eg:
xcrun simctl install booted <path-to-app.app>

```

### Uninstall an app
```
xcrun simctl uninstall <device> <app bundle identifier>

# eg:
xcrun simctl uninstall booted com.david.GreatTable
``` 

## Launching
### Launch an app
```
xcrun simctl launch <device> <app bundle identifier>

#eg:
xcrun simctl launch booted com.apple.mobilesafari

xcrun simctl launch booted com.david.GreatTable 

```


### Terminate an app
```
xcrun simctl terminate <device> <app bundle identifier>

#eg:
xcrun simctl terminate booted com.david.GreatTable
```

## IO
### Record video
```
xcrun simctl io <device> recordVideo <file>

#eg:
xcrun simctl io booted recordVideo myvideo.mov
```
To stop recording, press `Ctrl + C` on your terminal

### Capture screenshot
```
xcrun simctl io <device> screenshot <file>

#eg:
xcrun simctl io booted screenshot myimage.png

```

## Device logs
### Collect debug log
```
xcrun simctl spawn booted log stream --level debug
```

### Collect debug log from specific app
```
xcrun simctl spawn booted log stream --level debug --predicate 'subsystem contains "com.davidtran"' 
```

Replace `com.davidtran` by your app's bundle id


## Shutdown and erase
### Shutdown a device

```
xcrun simctl shutdown <device>
#eg:
xcrun simctl shutdown My-iphone11

```

### Erase a device
Make sure the device has been shutdown before erasing

```
xcrun simctl erase <device>

# eg:
xcrun simctl erase My-iphone11

```

## Delete device
```
xcrun simctl delete <device>

# eg: 
xcrun simctl delete CA5EA4CE-0647-4E1D-81C2-8257AF19BD1A
```


