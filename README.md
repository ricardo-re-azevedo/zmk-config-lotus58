#Building
```shell
cd zmk/app
# build the reset firmware if you need to start from scratch
west build -p -b nice_nano_v2 -- -DSHIELD=settings_reset -DZMK_CONFIG=/home/ricardo/projects/dactyl-keyboard-software/zmk-config-dactyl-manuform/config
# build right side
west build -p -b nice_nano_v2 -- -DSHIELD="dactyl_manuform_5x6_right nice_view_adapter nice_view" -DZMK_CONFIG=/home/ricardo/projects/dactyl-keyboard-software/zmk-config-dactyl-manuform/config
# build left side
west build -p -b nice_nano_v2 -- -DSHIELD="dactyl_manuform_5x6_left nice_view_adapter nice_view" -DZMK_CONFIG=/home/ricardo/projects/dactyl-keyboard-software/zmk-config-dactyl-manuform/config     
```