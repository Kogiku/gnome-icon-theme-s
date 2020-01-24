# GNOME Icon Theme Slate
Slate blue recolor of the default icon theme used by the GNOME desktop. The icons are used in the panel menu, and in nautilus and other applications, to represent the different applications, files, directories, and devices.
![Preview](https://raw.githubusercontent.com/Kogiku/gnome-icon-theme-slate/master/preview.png)
<sub>Preview Details: Theme: [Vertex](https://github.com/oberon-manjaro/vertex-theme) | File Manager: Caja 1.22.3 | Font: DejaVu Sans</sub>
## Installation
### Packages
|Distro|Package Name/Link|
|:----:|:----:|
| Debian | [gnome-icon-theme-slate_3.12.0s-1_all.deb](https://github.com/Kogiku/gnome-icon-theme-slate/releases/download/3.12.0s/gnome-icon-theme-slate_3.12.0s-1_all.deb) |
| any | [gnome-icon-theme-slate_3.12.0s.tar.bz2](https://github.com/Kogiku/gnome-icon-theme-slate/releases/download/3.12.0s/gnome-icon-theme-slate_3.12.0s.tar.bz2) (extract to `~/.icons`)|
### Manual Installation
The following packages are required to build
* `autoconf`
* `automake`
* `icon-naming-utils`
* `intltool`
* `pkg-config` or `pkgconfig` for Fedora
* `gettext`
* `git` to clone the source directory
* `gtk-update-icon-cache`
#### 1. Get the source
```
git clone https://github.com/Kogiku/gnome-icon-theme-slate
cd gnome-icon-theme-slate
```
#### 2. Build and install
```
./autogen.sh --prefix=/usr
sudo make install
```
