# GNOME Icon Theme S
Recolors of the default icon theme used by the GNOME desktop. The icons are used in the panel menu, and in nautilus and other applications, to represent the different applications, files, directories, and devices.

Color variants include:
* Sakura (pink)
* Seafoam (teal)
* Slate (blueish)
* Stardust (purple)
* Steel (grey).
### Preview
![Preview](https://raw.githubusercontent.com/Kogiku/gnome-icon-theme-s/master/preview.png)
## Installation
### Packages
|Distro|Package Name/Link|
|:----:|:----:|
| Debian | [gnome-icon-theme-s_3.12.0.4-2_all.deb](https://github.com/Kogiku/gnome-icon-theme-s/releases/download/3.12.0.4/gnome-icon-theme-s_3.12.0.4-2_all.deb) |
| any | [gnome-icon-theme-s_3.12.0.4.tar.bz2](https://github.com/Kogiku/gnome-icon-theme-s/releases/download/3.12.0.4/gnome-icon-theme-s_3.12.0.4.tar.bz2) (extract to `~/.icons`)|
### Manual Installation
The following packages are required to build
* `autoconf`
* `automake`
* `icon-naming-utils`
* `pkg-config` or `pkgconfig` for Fedora
* `gettext`
* `gtk-update-icon-cache`
* `git` to clone the source directory
#### 1. Get the source
```
git clone https://github.com/Kogiku/gnome-icon-theme-s
cd gnome-icon-theme-s
```
#### 2. Build and install
```
./autogen.sh --prefix=/usr
sudo make install
```
