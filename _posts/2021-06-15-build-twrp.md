## Compile TWRP

Here I am going to show you how I built TWRP for my Realme C12 which is running on Android 10.

What you will need?
- Linux PC
- Internet
- Patience

### Setup Build Environment
```bash
git clone https://github.com/akhilnarang/scripts.git
cd scripts
bash setup/android_build_env.sh
cd ..
mkdir ~/work
cd ~/work
```

### Sync sources
```bash
repo init --depth=1 -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-10.0 -g default,-device,-mips,-darwin,-notdefault 
repo sync -j$(nproc --all)
git clone --depth=1 https://github.com/HemanthJabalpuri/android_recovery_realme_RMX2185 -b android-10 device/realme/RMX2185
```

### Building
```bash
source build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
lunch omni_RMX2185-eng
mka recoveryimage
```

### Get final img file
Finaly image is available at out/target/product/RMX2185/recovery.img
