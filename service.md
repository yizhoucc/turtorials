# service and schedules

## mac

have such file in 

```<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>com.launchd.note</string>
    <key>ProgramArguments</key>
        <array>
            <string>zsh</string> <!-- This line isn't required if *.sh is already executable -->
            <string>/Users/yc/repo/note/push_release.sh</string>
        </array>
    <key>StartCalendarInterval</key>
    <dict>
      <key>Hour</key>
      <integer>13</integer>
      <key>Minute</key>
      <integer>14</integer>
    </dict>
  </dict>
</plist>
```
placed into ```~/Library/LaunchAgents```

then ```launchctl load com.launchd.<job name>.plist``` to load the service