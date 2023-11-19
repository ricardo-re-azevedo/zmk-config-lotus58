#Setup 
First follow: https://zmk.dev/docs/development/setup
```shell
cd /
set -Ux ZEPHYR_VERSION 3.2.0
west init -l "config"
west update
west zephyr-export
```

#Building
```shell
# build the reset firmware if you need to start from scratch
west build -p -b nice_nano_v2 -- -DSHIELD=settings_reset
# build right side
west build -p -b nice_nano_v2 -- -DSHIELD="lotus58_right nice_view_adapter nice_view" -DZMK_CONFIG=/home/ricardo/projects/zmk-config-lotus58/config
# build left side
west build -p -b nice_nano_v2 -- -DSHIELD="lotus58_left nice_view_adapter nice_view" -DZMK_CONFIG=/home/ricardo/projects/zmk-config-lotus58/config     
```

copy `zmk.uf2` from `zmk-config-lotus58\zmk\app\build\zephyr`