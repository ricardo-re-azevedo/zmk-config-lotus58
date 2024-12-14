Includes a custom nice_view sheild that replaces the wpm monior with a message

#Setup 
https://zmk.dev/docs/development/local-toolchain/setup/native
Follow https://docs.zephyrproject.org/latest/develop/west/install.html to install zephyr, west, and sdk.


```shell
cd /
#set -Ux ZEPHYR_VERSION 3.2.0
west init -l "config"
west update
west zephyr-export
```

We will mount our repo into a docker for excecution.
1. go to zmk/.devcontainer/devcontainer.json. 
2. Click cube in corner > "Create Dev Container and Mount Sources"
3. Create docker toolchain: https://www.jetbrains.com/help/clion/clion-toolchains-in-docker.html#create-docker-toolchain

#Building
```shell
cd zmk/app
set -Ux ZEPHYR_TOOLCHAIN_VARIANT zephyr
# or set ZEPHYR_TOOLCHAIN_VARIANT=zephyr
# build the reset firmware if you need to start from scratch
west build -p -b nice_nano_v2 -- -DSHIELD=settings_reset -DZMK_CONFIG=/home/ricardo/projects/zmk-config-lotus58/config
# build right side
west build -p -b nice_nano_v2 -- -DSHIELD="lotus58_right nice_view" -DZMK_CONFIG=/home/ricardo/projects/zmk-config-lotus58/config
# build left side
west build -p -b nice_nano_v2 -- -DSHIELD="lotus58_left nice_view" -DZMK_CONFIG=/home/ricardo/projects/zmk-config-lotus58/config     
```

copy files from `zmk-config-lotus58\zmk\app\build\zephyr`