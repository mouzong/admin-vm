# Install Pass from source code

```bash

sudo dnf install epel-release -y
sudo dnf config-manager --set-enabled crb

sudo dnf clean all

sudo dnf makecache

sudo dnf install git gcc make gnupg2 -y

git clone https://git.zx2c4.com/password-store.git

cd password-store

make install

```
