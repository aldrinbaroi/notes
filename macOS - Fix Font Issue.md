# macOS - Fix Font Issue

### First Try
Open ***Font Book*** and then under ***File*** menu click on the option ***Restore Standard Fonts...*** & then ***reboot***

### Second Try
If ***First Try*** fails then run the following command & then ***reboot***
```
sudo atsutil databases -remove
```

