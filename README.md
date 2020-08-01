<h1 align="center">
  <img src=".github/gnome-icon-theme-s.png" alt="GNOME Icon Theme S" />
</h1>

Updated version of the icon theme that was used by the GNOME 3.12 desktop. The icons are used in the panel menu, and in nautilus and other applications, to represent the different applications, files, directories, and devices.

Color variants:
* [Legacy](src/folders.svg) (3.12 original)
* [Sakura](src/folders-sakura.svg) (pink)
* [Seafoam](src/folders-seafoam.svg) (teal)
* [Slate](src/folders-slate.svg) (blueish)
* [Stardust](src/folders-stardust.svg) (purple)
* [Steel](src/folders-steel.svg) (grey)

### Some notable differences relative to gnome-icon-theme 3.12.0:
* More colors to choose from.
* Save and save-as cabinet icons were replaced with floppy icons.
* Additional icons were added from sources such as the [Adwaita](https://github.com/GNOME/adwaita-icon-theme) and [MATE](https://github.com/mate-desktop/mate-icon-theme) icon themes.

## Installation
### Packages
|Distro|Package Name/Link|
|:----:|:----:|
| Debian | [gnome-icon-theme-s_3.12.0.8-1_all.deb](https://github.com/Kogiku/gnome-icon-theme-s/releases/download/3.12.0.8/gnome-icon-theme-s_3.12.0.8-1_all.deb) |
| any | [gnome-icon-theme-s_3.12.0.8.tar.bz2](https://github.com/Kogiku/gnome-icon-theme-s/releases/download/3.12.0.8/gnome-icon-theme-s_3.12.0.8.tar.bz2) (extract to `~/.icons`)|

### Manual installation from source
The following packages are required to build:
* `autoconf`
* `automake`
* `icon-naming-utils`
* `pkg-config` or `pkgconfig` for Fedora
* `gtk-update-icon-cache`

#### 1. Get the source using `git`
```
git clone https://github.com/Kogiku/gnome-icon-theme-s
cd gnome-icon-theme-s
```

#### 2. Build and install
System wide (installs to `/usr/share/icons`):
```
./autogen.sh --prefix=/usr
sudo make install
```
Home directory (installs to `~/.local/share/icons`):
```
./autogen.sh --prefix=$HOME/.local
make install
```
#### 3. Uninstall
Run the following from the source code directory:
```
sudo make uninstall
<< or >>
make uninstall
```
Or simply remove the icon theme directories:
```
sudo rm -rf /usr/share/icons/gnome-{,legacy,sakura,seafoam,slate,stardust,steel}
<< or >>
rm -rf ~/.local/share/icons/gnome-{,legacy,sakura,seafoam,slate,stardust,steel}
<< or >>
rm -rf ~/.icons/gnome-{,legacy,sakura,seafoam,slate,stardust,steel}
```
