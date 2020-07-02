<h1 align="center">
  <img src=".github/gnome-icon-theme-s.png" alt="GNOME Icon Theme S" />
</h1>

Soft recolors of the default icon theme used by the GNOME 3.12 desktop. The icons are used in the panel menu, and in nautilus and other applications, to represent the different applications, files, directories, and devices.

Color variants include:
* Sakura (pink)
* Seafoam (teal)
* Slate (blueish)
* Stardust (purple)
* Steel (grey).
## Installation
### Packages
|Distro|Package Name/Link|
|:----:|:----:|
| Debian | [gnome-icon-theme-s_3.12.0.6-1_all.deb](https://github.com/Kogiku/gnome-icon-theme-s/releases/download/3.12.0.6/gnome-icon-theme-s_3.12.0.6-1_all.deb) |
| any | [gnome-icon-theme-s_3.12.0.6.tar.bz2](https://github.com/Kogiku/gnome-icon-theme-s/releases/download/3.12.0.6/gnome-icon-theme-s_3.12.0.6.tar.bz2) (extract to `~/.icons`)|
### Manual Installation
The following packages are required to build
* `autoconf`
* `automake`
* `icon-naming-utils`
* `pkg-config` or `pkgconfig` for Fedora
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
