## Install

```
Linux raspberrypi 5.15.32-v8+ #1538 SMP PREEMPT Thu Mar 31 19:40:39 BST 2022 aarch64 GNU/Linux

Distributor ID: Debian
Description:    Debian GNU/Linux 11 (bullseye)
Release:        11
Codename:       bullseye
```

```
sudo apt-get install autoconf gawk libc-ares-dev libcrypto++8 libcrypto++-dev libcurl4-openssl-dev libfreeimage-dev libreadline-dev libsqlite3-dev libssl-dev libtool sqlite3 libsodium-dev build-essential git automake

git clone https://github.com/meganz/MEGAcmd.git
cd MEGAcmd && git submodule update --init --recursive

sh autogen.sh
./configure
make
sudo make install
```

### Create mega-cmd service

/etc/systemd/system/mega-cmd.service

```
[Unit]
Description=Mega-CMD systemd service
After=network.target
StartLimitIntervalSec=0

[Service]
Type=simple
Restart=on-failure
RestartSec=1
User=pi
Environment="LD_LIBRARY_PATH=/usr/local/lib"
ExecStart=/usr/local/bin/mega-cmd-server

[Install]
WantedBy=multi-user.target
```

### Run

```
sudo systemctl start mega-cmd
sudo systemctl enable mega-cmd
mega-backup /srv/dev-disk-by-uuid-7fbb3083-839f-4a13-9731-9dd8cdf5d88b/Docker /Sync --period="0 30 2 * * 6" --num-backups=2
```
