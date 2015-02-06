# Quick-Notes-MacOSX

Quick Notes about Mac OSX


## Change login window picture

```shell
cp my_favorite_picture.jpg /Library/Caches/com.apple.desktop.admin.png
```

## Disable the “Are you sure you want to open this file?” warning dialogue

To disable this warning dialogue:
```shell
defaults write com.apple.LaunchServices LSQuarantine -bool NO
```

To enable it again:
```shell
defaults write com.apple.LaunchServices LSQuarantine -bool YES
```

Reboot or killing Finder are required

You can be more specific and only disable it from specified folder:
```shell
xattr -d -r com.apple.quarantine ~/Downloads
```


## Downloaded files history

To list all files downloaded (everything that has been passed through the Quarantine Manager):
```shell
sqlite3 ~/Library/Preferences/com.apple.LaunchServices.QuarantineEventsV* 'select LSQuarantineDataURLString from LSQuarantineEvent'
```

To reset that list:
```shell
sqlite3 ~/Library/Preferences/com.apple.LaunchServices.QuarantineEventsV* 'delete from LSQuarantineEvent'
```
