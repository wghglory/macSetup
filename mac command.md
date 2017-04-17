### 隐藏文件

```bash
defaults write com.apple.finder AppleShowAllFiles -boolean false ; killall Finder
```

### 显示文件

```bash
defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder
```

- Set files hidden: `chflags hidden <file>`
- Set files nohidden: `chflags nohidden <file>`

### Allow download

Sierra allow download app anywhere: `sudo spctl --master-disable`
