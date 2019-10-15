![SoftU2F Snap logo](https://github.com/alexmurray/softu2f-snap/blob/master/resources/softu2f.svg "SoftU2F Snap")

# SoftU2F #

-------------------------------------------------------------------------------

**SoftU2F in a snap** - Provides a software-based Universal 2nd Factor (U2F) token for use by Firefox / Chrome

[![SoftU2F](https://snapcraft.io/softu2f/badge.svg)](https://snapcraft.io/softu2f)

## Installation ##

[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/softu2f)

``` shell
sudo snap install softu2f --classic
```

([Don't have snapd installed?](https://snapcraft.io/docs/core/install))

## Build it yourself ##

```shell
# clone this repo
git clone https://github.com/alexmurray/softu2f-snap
cd softu2f-snap

# install snapcraft and multipass tooling needed to build the snap in a reproducible way
sudo snap install snapcraft --classic
sudo snap install multipass --beta --classic

# build the snap
snapcraft

# install the snap (--dangerous signals this is not signed and hence not trusted)
sudo snap install ./softu2f*.snap --dangerous

# connect the appropriate interfaces
sudo snap connect softu2f:uhid
sudo snap connect softu2f:password-manager-service

# start the application part by launching SoftU2F from the application launcher

# Hack around the device permissions (this is temporary hack until we resolve issue #1)
sudo chmod 0666 /dev/$(dmesg | grep SoftU2F | tail -n1 | grep -o hidraw[0-9])
```
