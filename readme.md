# This repository is unmaintained

It has been updated to reflect the [internal jimtcl deprecation](https://github.com/openocd-org/openocd/commit/77c904fd13c08077cafd0845107506db408b5bb1) and some minor changes line numbers for the STM32H7x dual-bank patch. Hopefully, this should fix the build process for the foreseeable future.

However, as this fork will not regularly be maintained, please fork and maintain it if you need it.

-------------------

## Build from source for Ubuntu >=22.04 / Debian >= 12 (x86_64)

The current version of openocd requires `libjim-dev >= 0.81`, which isn't available on older versions of Ubuntu nor Debian. If necessary, you can compile [jimtcl from source](https://github.com/msteveb/jimtcl), which provides `libjim-dev`.

You can build and install from source by running the following commands:

```bash
./build.sh
sudo dpkg -i openocd-git_*_amd64.deb
sudo apt-get -y -f install
```

It installs into `/opt/openocd-git`, so you don't have to worry about conflicts with the `openocd` package in case it's already installed. This package also installs udev rules.

Now you can execute openocd using `/opt/openocd-git/bin/openocd`.

Make sure to export this to your path or set `export OPENOCD=/opt/openocd-git/bin/openocd` so that other programs can find it.

## Build from source (ARM)

For ARM-based linux machines (like Raspberry Pi), you can build and install from source by running the following commands:

```bash
./build.sh
# use this for ARMv7 (Pi 3 and earlier)
sudo dpkg -i openocd-git_*_armhf.deb
# use this for ARMv8 (Pi 4 and later)
sudo dpkg -i openocd-git_*_arm64.deb
sudo apt-get -y -f install
```

## Build for other Linux distros

This repository can be used with other Linux distros but you may need to manually install dependencies. In `build.sh`, either comment out the `sudo apt-get install -y` lines, or modify the package names to match your distro.

## Build for MacOS

```bash
brew install texinfo automake libusb-compat hidapi
export PATH=/usr/local/opt/texinfo/bin:$PATH

cd openocd-git
make mac

cd openocd
sudo make install
```

Add this to your `~/.zshrc` file, and source it (`. ~/.zshrc`) or start a new shell afterwards:

```bash
export PATH=/opt/openocd-git/bin:$PATH
```
