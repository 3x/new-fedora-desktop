# New Fedora Machine Setup

Here are the steps I take after installing a new machine running Fedora Workstation. Most, if not all, of these steps can be adapted for other GNU/Linux distributions. 

# Installation
## ISO File
Download the latest Fedora Workstation ISO from [https://getfedora.org/workstation/download/](https://getfedora.org/workstation/download/).

If you have a slow or unreliable internet connection, it's advisable to use a command-line tool such as `curl` or `wget` to download the ISO to prevent download failures from the browser.

The Fedora Project has a guide for burning this ISO to a disk and booting into the live system [here](https://docs.fedoraproject.org/en-US/quick-docs/creating-and-using-a-live-installation-image/index.html).

## Disk Encryption
After booting into the live system, be sure to enable disk encryption. 

# First Boot
Update all installed packages:

```shell
$ sudo dnf upgrade
```

Some packages may require a reboot for an update to take effect:
```shell
$ reboot
```

# Using `dnf`
Install the following programs using `dnf`:
```shell
sudo dnf install alacritty firejail gnome-tweaks htop papirus-icon-theme rhythmbox rofi zsh -y
```
> 📝 **Note**: The `-y` flag skips having to type `"y"` into the terminal to confirm installing packages.

- `alacritty` - GPU-accelerated terminal emulator. Feels faster and more responsible than the default `gnome-terminal`. [More info](https://github.com/alacritty/alacritty)
- `firejail` - Used to sandbox apps. [More info](https://wiki.archlinux.org/title/Firejail)
- `gnome-tweaks` - Customize advanced GNOME settings. [More info](https://wiki.gnome.org/Apps/Tweaks)
- `htop` - CLI tool to control running processes. [More info](https://htop.dev/)
- `papirus-icon-theme` - Icon theme for GTK apps. [More info](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)
- `rhythmbox` - Music and podcast player. [More info](https://wiki.archlinux.org/title/Rhythmbox)
- `rofi` - Application launcher. [More info](https://github.com/davatorium/rofi)
- `zsh` - Alternative to `bash` with more customization abilities and utilities. [More info](https://zsh.sourceforge.io/)

# Enable Flatpak apps
Flatpak is a modern platform for distributing and installing apps on GNU/Linux, with easy control over what data apps can and cannot access.

Use the following command to enable the installation of Flatpak apps. 

```shell
$ flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

# Additional programs
The following programs each require different installation instructions. To avoid redundancy, installation instructions for each are linked.

- `flatseal` - A tool for managing Flatpak app permissions. [Installation]()
- `nvm` - After installing `nvm`, execute `nvm i node` to install `Node.js` and `npm`. [Installation](https://github.com/nvm-sh/nvm#about)
- `ungoogled-chromium` - A fork of Chromium, the framework that powers Google Chrome, with telemetry and non-free software removed. [Installation](https://flathub.org/apps/details/com.github.Eloston.UngoogledChromium)
- `vscodium` - A completely FLOSS fork of Microsoft's Visual Studio Code with telemetry and non-free software removed. [Installation (scroll to Fedora)](https://vscodium.com/#install)

# Browser Setup
## Firefox
1. Launch Firefox and navigate to [https://ffprofile.com/](https://ffprofile.com/).
1. Set your desired settings. When finished, click `Download profile.zip`.
1. Open the Files app and navigate to `Downloads/`.
1. Right-click `profile.zip` and select `Extract here`.
1. Enter the new `profile/` directory created.
1. Select all files using `ctl+A` and copy them with `ctl+C`.
1. Return to Firefox and navigate to `about:support`.
1. Scroll to the line labeled `Profile Directory` and click `Open Directory`.
1. Quit Firefox (this is important—leaving Firefox open will cause your new settings to be reset).
1. Select all files in this directory and delete them.
1. Paste the contents of your clipboard into this directory with `ctl+V`.
1. Relaunch Firefox and navigate to `about:preferences`.
1. Click `Home`. If you have `Shortcuts` or `Recommended by Pocket` enabled, you can deselect `Sponsored` under those categories to prevent Mozilla from displaying ads in the new tab page.
1. Click `Search`. Change your search engine to `DuckDuckGo`.
1. Click `Privacy`. There are many options here which depend on your opinions and threat model, which I cannot advise. [privacytools.io](https://privacytools.io) has a great guide on Firefox privacy settings and optimizations [here](https://blog.privacytools.io/firefox-privacy-an-introduction-to-safe/). <br> All users should at least install [uBlock Origin](https://addons.mozilla.org/firefox/addon/ublock-origin/) for blocking ads and tracking content, and [HTTPS Everywhere](https://addons.mozilla.org/firefox/addon/https-everywhere) to upgrade insecure HTTP connections to secure HTTPS connections wherever possible.

# Terminal
I recommend the `zsh` shell, `oh-my-zsh` for managing themes and plugins, and the `powerlevel10k` theme.

Open the `Terminal` app and execute this command to install `oh-my-zsh`:
```shell
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
`oh-my-zsh` will prompt you to change your default shell to `zsh`.

Next, follow the instructions [here](https://github.com/romkatv/powerlevel10k#get-started) to install the `powerlevel10k` theme.

---

> ⚠️ **WIP!** More coming soon.
