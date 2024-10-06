# This repository is archived.

Please fork and maintain it if you need it.


-------------------


# Nightly openocd-git build for Ubuntu 20.04

This repository uses github actions to build openocd from the master branch each night.

It installs into `/opt/openocd-git`, so you don't have to worry about conflicts with the `openocd` package in case it's already installed. This package also installs udev rules.

To install this artifact, do the following:

```
wget https://nightly.link/kbeckmann/ubuntu-openocd-git-builder/workflows/docker/master/openocd-git.deb.zip
unzip openocd-git.deb.zip
sudo dpkg -i openocd-git_*_amd64.deb
sudo apt-get -y -f install
```

Now you can execute openocd using `/opt/openocd-git/bin/openocd`.


# Build from source (ARM linux)
For ARM-based linux machines (like raspberry pi), you cannot use the prebuilt artifact described above. You can build and install from source by running the following commands.

```
./build.sh
sudo dpkg -i openocd-git_*_armhf.deb
sudo apt-get -y -f install
```


# MacOS
```
brew install texinfo automake libusb-compat hidapi
export PATH=/usr/local/opt/texinfo/bin:$PATH

cd openocd-git
make mac

cd openocd
sudo make install
# Run and add this to your ~/.zshrc file
export PATH=/opt/openocd-git/bin:$PATH
```


