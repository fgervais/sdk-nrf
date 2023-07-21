#

## Build

```bash
docker compose run --rm nrf west build -b bitcraze_crazyradio_2 -- -DOVERLAY_CONFIG="overlay-usb.conf" -DDTC_OVERLAY_FILE="usb.overlay"
```

## Flash

### pyocd
```bash
pyocd flash -e chip -t nrf52840 -f 4000000 build/zephyr/zephyr.hex
```