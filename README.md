---
title: MAC鼠标速度
date: 2019-03-09 14:30
tags: Mac使用优化
---

Mac 中跟鼠标有关的默认选项有以下三个，不用第三方软件也可以改动效果

### 鼠标双击阈值：
``` bash
defaults read -g com.apple.mouse.doubleClickThreshold
```

### 鼠标加速度：
``` bash
defaults read -g com.apple.mouse.scaling
```

### 滚动速度：
``` bash
defaults read -g com.apple.scrollwheel.scaling
```

如果鼠标使用有异常，可以再终端中读以上三个参数，并根据自己的需要适当调高调低

### 鼠标双击阈值：
``` bash
defaults write -g com.apple.mouse.doubleClickThreshold 0.75
```

### 鼠标加速度：
``` bash
defaults write -g com.apple.mouse.scaling 5
```

### 滚动速度：
``` bash
defaults write -g com.apple.scrollwheel.scaling 0.75
```

三个选项数值范围未验证，自己根据需要调低调高，系统重启后生效。
