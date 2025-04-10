# Install Requirement
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

```bash
./requirements.sh dev
./requirements.sh 5g
```

# Run
Currently, I can only run with the docker container

```bash
cd ~
mkdir 5ghoul # Create 5ghoul folder
curl -LJO https://github.com/asset-group/5ghoul-5g-nr-attacks/raw/master/container.sh
chmod +x container.sh # Give exec. permission to the 5Ghoul container script
./container.sh run release-5g # This will pull and start the terminal of the 5Ghoul container
sudo bin/5g_fuzzer --MCC=001 --MNC=01 --GlobalTimeout=false --EnableMutation=false # Start the base station inside the container
```

Note: If you exit the shell and want to enter again you should run `curl` again
```bash
curl -LJO https://github.com/asset-group/5ghoul-5g-nr-attacks/raw/master/container.sh
./container.sh run release-5g 
```

Or you can run the simulation to test instead
```bash
sudo bin/5g_fuzzer --EnableSimulator=true --EnableMutation=false --GlobalTimeout=false
```