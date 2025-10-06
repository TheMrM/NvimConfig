# 🧰 Kali Linux Terminal Setup Guide  
**Zsh + Oh My Zsh + Powerlevel10k + FiraCode Nerd Font + Plugins**

This guide walks you through creating a beautiful and powerful terminal setup on **Kali Linux** — ideal for both pentesting and development.  
It uses **Zsh** with **Powerlevel10k**, **Oh My Zsh**, and a **Nerd Font** for icons.

## ⚙️ Step 1 — Update System
```bash
sudo apt update && sudo apt full-upgrade -y
````

## 🧠 Step 2 — Install Essentials

```bash
sudo apt install -y git curl wget unzip zsh fonts-firacode
```

## 🧩 Step 3 — Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

After installation, type:

```bash
exit
```

to return to your shell and continue setup.

## 🧩 Step 4 — Set Zsh as Default Shell

```bash
chsh -s $(which zsh)
```

Then log out and back in, or run:

```bash
zsh
```

## 🌈 Step 5 — Install Powerlevel10k Theme

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```

Edit your configuration:

```bash
nano ~/.zshrc
```

Find this line:

```bash
ZSH_THEME="robbyrussell"
```

Replace it with:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```
## 🔤 Step 6 — Install FiraCode Nerd Font

```bash
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/FiraCode.zip
unzip -o FiraCode.zip
fc-cache -fv
```

Then open your terminal **Preferences → Appearance** and apply these settings:

| Setting                                              | Value                     |
| ---------------------------------------------------- | ------------------------- |
| **Font**                                             | `FiraCode Nerd Font Mono` |
| **Size**                                             | `11 pt`                   |
| **Cursor shape**                                     | `IBeamCursor`             |
| **Transparency**                                     | `0%`                      |
| **Margin**                                           | `5px`                     |
| **Use bold font for intense colors**                 | ✅                         |
| **Enable bi-directional text support**               | ✅                         |
| **Use box drawing characters contained in the font** | ✅                         |
| **Change window title based on terminal**            | ✅                         |

## ⚙️ Step 7 — Install Zsh Plugins

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Edit your `.zshrc`:

```bash
nano ~/.zshrc
```

Find the line:

```bash
plugins=(git)
```

Replace with:

```bash
plugins=(git z sudo colored-man-pages command-not-found history-substring-search zsh-autosuggestions zsh-syntax-highlighting)
```

Then reload:

```bash
source ~/.zshrc
```

## ⚡ Step 8 — Configure Powerlevel10k

Run:

```bash
p10k configure
```

When prompted:

* ✅ Yes, I have a Nerd Font
* ✴️ Unicode characters
* 🔹 Angled separators
* 🌈 Rainbow color style
* 🧱 Compact or full prompt (your choice)
* ⚡ Enable instant prompt

This creates the file:

```
~/.p10k.zsh
```

## 🧱 Step 9 — Optional: Tilix Color Scheme

If you’re using **Tilix** as your terminal:

```bash
mkdir -p ~/.config/tilix/schemes
cd ~/.config/tilix/schemes
wget https://raw.githubusercontent.com/catppuccin/tilix/main/src/catppuccin-mocha.json
```

Then open Tilix → **Preferences → Profiles → Color → Import** → select `catppuccin-mocha.json`.


## ✅ Step 10 — Reload

```bash
source ~/.zshrc
```

Your terminal is now:

* 🧠 Smart with autosuggestions
* 🎨 Beautiful with Powerlevel10k
* ⚙️ Fast and functional
* 🖋️ Using proper Nerd Font icons


## 🧾 Bonus: Backup and Restore Config

After customizing your prompt, back it up:

```bash
cp ~/.zshrc ~/zshrc.backup
cp ~/.p10k.zsh ~/p10k.backup
```

Restore later with:

```bash
cp ~/zshrc.backup ~/.zshrc
cp ~/p10k.backup ~/.p10k.zsh
source ~/.zshrc
```

## 📸 Final Appearance Reference

**Font:** `FiraCode Nerd Font Mono 11pt`
**Cursor:** IBeam
**Color Scheme:** BreezeModified / Catppuccin Mocha
**Theme:** Powerlevel10k (Rainbow, Angled, Unicode)

## 🧩 Summary of Commands

```bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install -y git curl wget unzip zsh fonts-firacode
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
chsh -s $(which zsh)
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
mkdir -p ~/.local/share/fonts && cd ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/FiraCode.zip
unzip -o FiraCode.zip && fc-cache -fv
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
p10k configure
source ~/.zshrc
```

### ✨ Author Notes

This guide was created after configuring a polished **Kali Linux terminal environment** in a virtual machine, ensuring correct font alignment, color consistency, and Powerlevel10k integration.
Perfect for rebuilding your setup anytime you reinstall Kali.
