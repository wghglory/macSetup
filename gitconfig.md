# Global git config

`~/.gitconfig`:

```shell
[user]
	name = Guanghui Wang
	email = guanghui-wang@foxmail.com
[credential]
	helper = osxkeychain
[core]
	editor = code --wait
[alias]
	co = checkout
	br = branch
  bd = branch -d
  ca = commit --amend
	ci = commit --no-verify
	st = status --short --branch
	unstage = reset HEAD --
  un = reset --hard HEAD
	last = log -1 HEAD
  ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
  ld = log --pretty=format:"%C(yellow)%h\\ %C(green)%ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short --graph
  ls = log --pretty=format:"%C(green)%h\\ %C(yellow)[%ad]%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=relative
[color]
  diff = auto
  status = auto
  branch = auto
```
