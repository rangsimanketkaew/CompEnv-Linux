# Installation

sudo apt-get purge nvidia*
sudo apt-get install nvidia-current

#e.g.: sudo apt-get install nvidia-378 --> this is the lastest version of nvidia driver for linux64 / gtx 950m.

### optional
sudo apt-get install dkms


## Restoring graphic
sudo apt-get remove --purge nvidia*
sudo apt-get autoremove

sudo apt-get install nvidia-378

### optional
sudo apt-get install nvidia-378 --no-x-check
# skip the start x error
