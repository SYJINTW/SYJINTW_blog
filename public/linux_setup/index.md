# Linux Setup



最近在因為進實驗室有一台桌機可以灌系統，然後一開始灌了 Ubuntu ，但是不知道發生什麼事突然掛掉，所以我就生氣打算重新灌一個系統。經過實驗室學長的推薦，決定試試看 Pop! OS ，反正都是 Ubuntu 為基礎的 OS ，所以設定上都差不多。  
  
這篇文章主要會放在紀錄我對 Linux 環境，好看好用方面的設定，不在意美觀的自行斟酌。
   
---

<!-- Basic tools -->
## 下載基礎工具

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -y install git snapd snapcraft cmake gcc speedtest-cli vim nano tmux python3.8 openssh-client
```

---

<!-- Terminal Setting -->
## Terminal (Oh-my-zsh)

下載 zsh

```bash
sudo apt-get -y install zsh
```

下載 oh-my-zsh

```bash
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

Shell 預設改成 zsh

```bash
chsh -s /bin/zsh
```

### 安裝字型

```bash
sudo apt-get -y install powerline fonts-powerline ttf-ancient-fonts
```

### 設定主題

[Themes · ohmyzsh/ohmyzsh Wiki](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)

[External themes · ohmyzsh/ohmyzsh Wiki](https://github.com/ohmyzsh/ohmyzsh/wiki/External-themes)

這裡用 `bullet-train` 為例子

[GitHub - caiogondim/bullet-train.zsh: An oh-my-zsh shell theme based on the Powerline Vim plugin](https://github.com/caiogondim/bullet-train.zsh)

建立一個新資料夾

```bash
mkdir -p ~/.oh-my-zsh/custom/themes/
```

下載主題

```bash
wget -xqO ~/.oh-my-zsh/custom/themes/bullet-train.zsh-theme https://raw.githubusercontent.com/caiogondim/bullet-train-oh-my-zsh-theme/master/bullet-train.zsh-theme
```

用 `vim` 打開 zsh 的設定檔

```bash
sudo vim ~/.zshrc
```

把 ~/.zshrc 中的 `ZSH_THEME` 換成自己想要的主題

```bash
ZSH_THEME="bullet-train"
```

在 `ZSH_THEME` 的前一行加上

```bash
export TERM="xterm-256color"
```

把 ~/.zshrc 中添加 `BULLETTRAIN_PROMPT_ORDER` 調整 Bullet train 顯示的東西

```bash
BULLETTRAIN_PROMPT_ORDER=(
  time
	status
  context
  dir
  git
	cmd_exec_time
)
```

如果顯示亂碼的話，到 terminal 的 Preferences → Pop → Text，把 Custom font 設成 `Hack Regular`

### 下載 plugin

[Plugins · ohmyzsh/ohmyzsh Wiki](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)

#### Autosuggestions

下載 `zsh-autosuggestions`

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

在 ~/.zshrc 中的 `plugins` 添加 plugin 名稱

```bash
plugins=( 
    # other plugins...
    zsh-autosuggestions
)
```

#### Syntax highlighting

下載 `zsh-syntax-highlighting`

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

在 ~/.zshrc 中的 `plugins` 添加 plugin 名稱

```bash
plugins=( 
    # other plugins...
    zsh-syntax-highlighting
)
```

#### Colored man pages

在 ~/.zshrc 中的 `plugins` 添加 plugin 名稱

```bash
plugins=( 
    # other plugins...
    colored-man-pages
)
```

#### Web search

[ohmyzsh/plugins/web-search at master · ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/web-search)

在 ~/.zshrc 中的 `plugins` 添加 plugin 名稱

```bash
plugins=( 
    # other plugins...
    web-search
)
```

如何使用

```bash
web_search google [what to search]
google [what to search]
```

#### Copydir

[ohmyzsh/plugins/copydir at master · ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/copydir)

在 ~/.zshrc 中的 `plugins` 添加 plugin 名稱

```bash
plugins=( 
    # other plugins...
    copydir
)
```

Then use the command `copydir` to copy the $PWD.

如果出現 `Platform linux-gnu not supported or xclip/xsel not installed`

就安裝 `xclip` 並且重新打開 terminal

```bash
sudo apt-get -y install xclip
```

#### Copyfile

[ohmyzsh/plugins/copyfile at master · ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/copyfile)

在 ~/.zshrc 中的 `plugins` 添加 plugin 名稱

```bash
plugins=( 
    # other plugins...
    copyfile
)
```

Then you can run the command `copyfile <filename>` to copy the file named `filename`.

如果出現 `Platform linux-gnu not supported or xclip/xsel not installed`

就安裝 `xclip` 並且重新打開 terminal

```bash
sudo apt-get -y install xclip
```

---

## 小結

大致先寫成這樣，希望可以幫助跟我一樣還不太會設定 Linux 的人。

