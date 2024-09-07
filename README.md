![zilpzalp](https://github.com/kilipan/zilpzalp/blob/main/img/zilpzalp_photo.jpg?raw=true)

# zilpzalp ZMK module

_A wonky 28-key split-unibody column-stagger keyboard._

[Here](https://github.com/kilipan/zilpzalp) you can find the hardware files.\
[Here](https://github.com/kilipan/qmk-config-zilpzalp) you can find the QMK config for zilpzalp.

## HOW TO USE

- setup a zmk-config repo following [this guide](https://zmk.dev/docs/user-setup)
- edit your west.yml file found in your zmk-config's config directory to add the zilpzalp module. example:

```
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: grassfedreeve
      url-base: https://github.com/grassfedreeve
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    - name: zmk-keyboards-akohekohe
      remote: grassfedreeve
      revision: main
  self:
    path: config
```

- Once you have the module added to your west.yml you can then build firmware as if it was in your config's shield directory or in ZMK main.
- create a zilpzalp.keymap file to add your own keymap, likewise a zilpzalp.conf to modify the configuration
- adjust the zilpzalp.keymap file (find all the keycodes on [the zmk docs pages](https://zmk.dev/docs/codes/))
- `git push` to your repo or save if using GitHub ui
- on the GitHub page of your fork navigate to "Actions"
- scroll down and unzip the `firmware.zip` archive that contains the latest firmware
- connect the zilpzalp to your PC, press reset and hold the boot key during reset
- the keyboard should now appear as a mass storage device
- drag'n'drop the `zilpzalp-seeeduino_xiao_ble-zmk.uf2` file from the archive onto the storage device

## Troubeshooting

On macOs you might get an error stating that the `operation can’t be completed unexpected error 100093`. You can circumvent this by copying the file from your terminal:

- move the `zilpzalp-seeeduino_xiao_ble-zmk.uf2` to your root directory
- copy the file onto the zilpzalp volume: `cp -X zilpzalp-seeeduino_xiao_ble-zmk.uf2 ../../Volumes/<volume_name>/`
