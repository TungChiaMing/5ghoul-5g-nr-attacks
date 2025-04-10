# Install

```bash
sudo apt install qttools5-dev
sudo apt install libfmt-dev
sudo apt install libmbim-glib-dev
sudo apt install libqmi-glib-dev
sudo apt install libstdc++-12-dev
```

```bash
cd ~/5ghoul-5g-nr-attacks/3rd-party/ModemManager/libqrtr-glib
sudo env "PATH=$PATH" "PYTHONPATH=$PYTHONPATH:$(python3 -c 'import site; print(site.USER_SITE)')" ninja -C build install

cd ~/5ghoul-5g-nr-attacks/3rd-party/ModemManager/libqmi
export PKG_CONFIG_PATH=/runtime/lib/pkgconfig:$PKG_CONFIG_PATH
pkg-config --modversion qmi-glib
```