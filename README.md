#Setup 
First follow: https://zmk.dev/docs/development/setup
```shell
cd zmk/app
west init --mr v3.2.0
west update
west zephyr-export
```

#Building
```shell
cd zmk/app
set -Ux ZEPHYR_TOOLCHAIN_VARIANT zephyr # assuming using fish shell
# build the reset firmware if you need to start from scratch
west build -p -b nice_nano_v2 -- -DSHIELD=settings_reset
# build right side
west build -p -b nice_nano_v2 -- -DSHIELD="lotus58_right nice_view_adapter nice_view" -DZMK_CONFIG=/home/ricardo/projects/zmk-config-lotus58/config
# build left side
west build -p -b nice_nano_v2 -- -DSHIELD="lotus58_left nice_view_adapter nice_view" -DZMK_CONFIG=/home/ricardo/projects/zmk-config-lotus58/config     
```

copy `zmk.uf2` from `zmk-config-lotus58\zmk\app\build\zephyr`